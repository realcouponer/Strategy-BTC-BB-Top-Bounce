# About
This repository holds an open-source trading strategy maintained by the [Superalgos Community](https://t.me/superalgoscommunity). The strategy was released in the community's Telegram group in August 2019 and has been trading live since. An evolution of the system is currently available as version 2. This page explains the trading system and analyzes its performance.

The trading system conforms to the Superalgos Trading Protocol, therefore, it may function as a fully automated trading system within [Superalgos](https://superalgos.org). 

People not interested in trading automation may still obtain the strategy's rules (situations, conditions, and formulas) from Superalgos' design space and use the set of rules as they see fit. Superalgos may also be used for testing trading ideas, for backtesting, and paper-trading (to obtain live signals!).

# The Files

* ```Share - Workspace - Weak-hands buster - BTC - SDA v.0.0.3.json```: This is virtually the original file ([the original](https://github.com/Superalgos/Strategy-BTC-WeakHandsBuster/blob/8f1879adb9be491fa28f34b58344d5223f4cdf3e/Share%20-%20Workspace%20-%20Weak-hands%20buster%20-%20BTC%20-%201hr.json) was renamed several times), first published in this repository on September 2019. It is a legacy version of a workspace containing the trading system. It may not be loaded in the current version of the system due to backward-compatibility issues, but it is kept for its historical value.

* ```Weak-Hands Buster Trading System - Original.json```: This is the original version of the trading system as first published, but in a format that is usable in the current version of Superalgos.

* ```Weak-Hands Buster Trading System - v.2 - Announcements.json```: This is version 2 of the trading system, released on April 2020, and now shipping with Superalgos. It features several improvements over the original version, as per the below details. The trading system is set up with optional [Telegram Announcements](https://docs.superalgos.org/suite-telegram-announcements.html) that may broadcast the trading session's activity over a Telegram group (when running on Superalgos).


# Weak-hands Buster (WHB)

## WHB V.2 Performance in Backtests (Binance) at the Time of Publishing

| Details | Jan 2018 - Mar 2020 | 2020 (Jan - Mar) | 2019 | 2018 | 
| :--- | :---: | :---: | :---: | :---: |
| Trades: | **24** | 2 | 9 | 13 |
| Hits: | **19** | 1 | 8 | 10 |
| Fails: | **5** | 1 | 1 | 3 |
|Hit Ratio: | **79%** | 50% | 89% | 77% |
| ROI*: | **2662%** | 75% | 142% | 551% |

[ * ] The above table shows the results for different periods tested independently. Each backtest starts with an *initial capital* and the system reinvests accumulated profits in every trade. ROI is calculated over the *initial capital* for each backtest and the result is rounded to the closest integer. Because the system reinvests accumulated profits, the sum of ROI in different periods is not the same as ROI for all periods run in one single test (first column).

**Assumptions**:

* Slippage: 0.1% in all orders.
* Fees: 0.1% in all orders.

## Market

USDT-BTC, with BTC as the base asset.

## Strategy Goal

Accumulate bitcoin during bear markets and / or consolidation periods, with a conservative approach to minimize risk.

## Approach

Split the goal into two fundamental notions:

1. **Focus on potentially big market moves**. The strategy is optimized for major trend reversals resulting in long bear markets. Significant consolidations during bull markets are targetted as well.

2. **Take the clearest and most promising opportunities only**. We pass on everything else to avoid failures and to preserve capital.

## Trading Idea

The original system is dissected [in this Hackernoon article](https://hackernoon.com/how-to-increase-your-bitcoin-holdings-in-a-bear-market-part-1-kjwp2gwu). Version 2 maintains the trading idea and the take position event almost intact. 

The main trading idea is to identify short-term reversals as well as continuations and deepening of trends marked by a break down of the Bollinger Bands (BB) in the 1-hour chart, using the Percentage Bandwidth (%B) indicator, the Bollinger Bands Moving Average (BB MA) and the Bollinger Band deviation to assess momentum and volatility, optimize the take position event, and filter out late entries.

## WHB V.2&mdash;What Changed

* The two different situations making up the take position event were split into two separate strategies operating under the same trading system. This means that take profit and stop targets may be managed separately for each take position situation, as it should have been from the start. This is the first case of two complementary strategies running under the same trading system.

* An additional condition was implemented at the take position event of each strategy so that each specializes in two different volatility ranges. The *Xtreme* strategy works best in extreme volatility situations (*e.g.* ATH period in late 2017 and early 2018). The *Steep* strategy works best in *normal* (by BTC standards) volatility situations.

* Management of take profit implemented originally was greatly improved for the *Steep* strategy, with a few simple additions and checks in the conditions that determine the events that switch phases.

* The trailing stop for the *Steep* strategy was raised from 5 to 5.25% above the 20 MA. The trailing was delayed to kick-in only after the market has dropped 5%. The initial stop target remains the same at 3%.

## Original WHB Live Performance

| Details | Sep 2019 - Mar 2020 |
| :--- | :---: |
| Trades: | 7 |
| Hits: | 4 |
| Fails: | 3 |
| Hit Ratio: | 57% |
| ROI*: | 76% |

## Original WHB Main Live Trades

### Sep 2019

![6th Sep  2019](https://user-images.githubusercontent.com/13994516/79866577-43febb00-83dd-11ea-851a-398db2c4a60c.PNG)

### Nov 2019

![19th Nov  2019](https://user-images.githubusercontent.com/13994516/79866595-4d882300-83dd-11ea-9608-b57a342690e3.PNG)

### Mar 2020

![8th Mar  2020](https://user-images.githubusercontent.com/13994516/79866599-4eb95000-83dd-11ea-9c51-66ffd99b41bd.PNG)

### Original WHB Performance in Backtests (Poloniex)

| Details | 2019 | 2018 |
| :--- | :---: | :---: |
| Trades: | 9 | 19 |
| Hits: | 8 | 12 |
| Fails: | 1 | 7 |
| ROI: | 106% | 549% |

# Disclaimer

> THIS IS NOT FINANCIAL ADVICE. ALTHOUGH THE STRATEGIES IN THIS REPOSITORY MAY BE FULLY FUNCTIONAL, WE DO NOT MAKE ANY EXPRESS OR IMPLIED RECOMMENDATION AS OF HOW YOU SHOULD USE THEM. WE SHARE STRATEGIES FOR EDUCATIONAL PURPOSES ONLY. TRADE AT YOUR OWN RISK.

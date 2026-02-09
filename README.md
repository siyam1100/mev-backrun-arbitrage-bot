# MEV Backrun Arbitrage Bot

This repository contains a high-performance bot designed to capture arbitrage opportunities created by large swaps on Decentralized Exchanges. By monitoring the mempool for "pending" swaps that move the price significantly, this bot prepares a "backrun" transaction to restore price equilibrium and capture the spread.

## How it Works
1. **Mempool Monitoring**: Streams pending transactions using WebSockets.
2. **Impact Simulation**: Uses `eth_call` or `tenderly` to simulate the price impact of a pending trade.
3. **Calculation**: Determines the exact amount of input tokens needed to maximize profit post-swap.
4. **Execution**: Submits a bundle via Flashbots or Eden Network to ensure the transaction is executed immediately after the target trade without risk of being frontrun.



## Strategy Features
* **Atomic Transactions**: All trades happen within a single smart contract execution to prevent partial fills.
* **Gas Optimization**: Minimalist Solidity code to ensure the lowest possible overhead.
* **Flashbots Integration**: Bypasses the public mempool to avoid being frontrun by other bots.

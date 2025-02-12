# Rare Protocol Core Smart Contract

## Deploy

### RareStakingDeploy

Follow `script/staking/RareStakingDeploy.sol` script to deploy and get the address for `stakingRegistry` which will be used when deploying `SuperRareBazaar`.

`forge script script/staking/RareStakingDeploy.s.sol:RareStakingDeploy --broadcast --rpc-url https://goerli.infura.io/v3/02a2a786a118479dbadfd39431aca051`

### .env

`RARE_ADDRESS=SuperRareGovToken.sol`

`WETH_RARE_POOL_ADDRESS` we have to create a uniswap v3 pool. RARE - WETH and use the UniswapV3Pool address here.

### SuperRareBazaar

Follow `script/NetworkDeploy.sol` to deploy the `SuperRareBazaar.sol` marketplace.

## Contracts

### Staking

#### Staking Registry

The `RareStakingRegistry` serves as a registry where staking contracts (see Rarity Pools), reward swapping contracts, and configuration settings related to staking can be managed and accessed.

#### Rarity Pool

The `RarityPool` provides functions for initializing the contract, adding rewards, taking snapshots, staking, unstaking, and claiming rewards. It also includes various read functions to query information about stakers, rounds, rewards, historical rewards, calculations, and more.

The `RarityPool` is where users can stake tokens, earn rewards, and claim them based on their stake during the round.

#### Reward Accumulator

The contract provides functions for initializing the contract, accumulates rewards and performs a reward swap, and estimates the discounted price of RARE for a given token. The reward swap function allows users to specify the token they want to receive, the minimum amount they are willing to accept, and the amount of RARE they want to trade. The contract also includes a read function to estimate the discounted price of RARE for a specific token.

Overall, the contract serves as an interface for a sending rewards and reward swapping where users can trade their RARE tokens for other ERC20 tokens and ether at a discounted price.

### Bazaar

The Bazaar is the interface to Rare Protocol's market mechanisms which include: offers, general and direct sale prices/purchases, Coldie Auctions (aka Reserve auctions), and scheduled auctions.

## Building

### Require Dependencies

- [forge](https://github.com/foundry-rs/foundry)

Be sure to run `forge install` when first cloning the repo.

```bash
make build
```

## Tests

```bash
forge test
```

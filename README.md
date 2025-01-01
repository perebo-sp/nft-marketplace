# NFT Marketplace with Fractional Ownership and Staking

A sophisticated smart contract implementation for a decentralized NFT marketplace featuring fractional ownership and staking capabilities, built on the Stacks blockchain.

## Features

### Core NFT Functionality

- **Minting**: Create new NFTs with customizable URIs and collateral requirements
- **Transfers**: Secure token transfers between users with ownership validation
- **Ownership Tracking**: Robust tracking of token ownership and metadata

### Marketplace Features

- **Listing Management**: List NFTs for sale with customizable pricing
- **Purchase System**: Secure buying mechanism with automatic fee handling
- **Protocol Fees**: 2.5% marketplace fee on all transactions
- **Price Controls**: Validation to prevent zero-price listings

### Fractional Ownership

- **Share-based System**: Divide NFT ownership into tradeable shares
- **Share Transfers**: Transfer partial ownership between users
- **Balance Tracking**: Accurate tracking of share distribution
- **Overflow Protection**: Safe arithmetic operations for share calculations

### Staking Mechanism

- **Flexible Staking**: Stake NFTs to earn yield
- **Annual Yield**: 5% annual yield rate for staked tokens
- **Reward Distribution**: Automatic calculation and distribution of staking rewards
- **Unstaking**: Secure unstaking process with final reward distribution

### Security Features

- **Collateral Requirements**: 150% minimum collateral ratio
- **Ownership Validation**: Strict checking of token ownership for all operations
- **Input Validation**: Comprehensive validation for URIs and operations
- **Overflow Protection**: Safe arithmetic operations throughout

## Technical Details

### Constants

```clarity
min-collateral-ratio: 150%  // Minimum required collateral
protocol-fee: 2.5%          // Marketplace fee
yield-rate: 5%             // Annual staking yield
```

### Data Structures

#### Token Data

```clarity
{
    owner: principal,
    uri: string-ascii,
    collateral: uint,
    is-staked: bool,
    stake-timestamp: uint,
    fractional-shares: uint
}
```

#### Listing Data

```clarity
{
    price: uint,
    seller: principal,
    active: bool
}
```

#### Fractional Ownership Data

```clarity
{
    shares: uint
}
```

#### Staking Rewards Data

```clarity
{
    accumulated-yield: uint,
    last-claim: uint
}
```

## Error Codes

| Code | Description             |
| ---- | ----------------------- |
| u100 | Owner-only operation    |
| u101 | Not token owner         |
| u102 | Insufficient balance    |
| u103 | Invalid token           |
| u104 | Listing not found       |
| u105 | Invalid price           |
| u106 | Insufficient collateral |
| u107 | Already staked          |
| u108 | Not staked              |
| u109 | Invalid percentage      |
| u110 | Invalid URI             |
| u111 | Invalid recipient       |
| u112 | Arithmetic overflow     |

## Public Functions

### NFT Operations

- `mint-nft`: Create new NFT with URI and collateral
- `transfer-nft`: Transfer NFT ownership
- `list-nft`: List NFT for sale
- `purchase-nft`: Purchase listed NFT

### Fractional Ownership

- `transfer-shares`: Transfer ownership shares
- `get-fractional-shares`: Query share ownership

### Staking Operations

- `stake-nft`: Stake NFT for yield
- `unstake-nft`: Unstake NFT and claim rewards
- `calculate-rewards`: Calculate current staking rewards

## Read-Only Functions

- `get-token-info`: Retrieve token metadata
- `get-listing`: Get listing information
- `get-fractional-shares`: Query share balances
- `get-staking-rewards`: Get staking reward data

## Security Considerations

1. **Collateral Management**

   - Enforced minimum collateral ratio
   - Validated collateral transfers
   - Protected withdrawal mechanisms

2. **Access Control**

   - Owner-only operations
   - Token ownership validation
   - Staking state validation

3. **Transaction Safety**

   - Safe arithmetic operations
   - Protected against reentrancy
   - Validated token transfers

4. **Input Validation**
   - URI format checking
   - Price validation
   - Recipient validation

## Best Practices

1. **When Minting**

   - Ensure sufficient collateral
   - Provide valid URI
   - Consider gas costs

2. **When Trading**

   - Verify listing status
   - Check price accuracy
   - Confirm ownership

3. **When Staking**

   - Calculate potential yields
   - Monitor reward accumulation
   - Plan unstaking timing

4. **For Fractional Ownership**
   - Track share distributions
   - Validate share transfers
   - Monitor total shares

## Implementation Notes

1. **Yield Calculation**

   - Based on block height
   - Approximately 52,560 blocks per year
   - Linear reward accumulation

2. **Protocol Fees**

   - Automatically deducted
   - Sent to contract owner
   - Based on transaction value

3. **Share Management**
   - Zero-share transfers prevented
   - Overflow protection
   - Accurate balance tracking

## Testing Recommendations

1. **Core Functionality**

   - Minting with various URIs
   - Transfer scenarios
   - Ownership validation

2. **Marketplace Features**

   - Listing creation/removal
   - Purchase processes
   - Fee calculations

3. **Staking Mechanics**

   - Reward calculations
   - Staking/unstaking flows
   - Time-based scenarios

4. **Fractional Ownership**
   - Share transfers
   - Balance tracking
   - Edge cases

## Future Considerations

1. **Scalability**

   - Batch operations
   - Gas optimization
   - Storage efficiency

2. **Features**

   - Automated market making
   - Advanced staking strategies
   - Enhanced reward mechanisms

3. **Integration**
   - Cross-chain compatibility
   - Oracle integration
   - External price feeds

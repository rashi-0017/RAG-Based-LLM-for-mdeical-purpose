# Polynomial Interpolation Solver

A robust JavaScript implementation for solving polynomial interpolation problems using Gauss-Jordan elimination with exact rational arithmetic. This solution provides precise coefficient calculations for scenarios requiring high numerical accuracy, such as cryptographic applications or mathematical computations where floating-point precision is insufficient.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Algorithm Details](#algorithm-details)
- [API Reference](#api-reference)
- [Example](#example)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Overview

This project implements a definitive solution for polynomial interpolation using the Gauss-Jordan elimination method. The core innovation lies in the use of a custom `Fraction` class that maintains exact rational arithmetic throughout the computation, eliminating floating-point errors and ensuring precise results.

The solver is particularly suited for problems where:
- Exact rational coefficients are required
- High precision is critical (e.g., cryptographic applications)
- Input values are provided in various number bases
- Large integer values need to be handled accurately

## Features

- **Exact Rational Arithmetic**: Custom `Fraction` class ensures no precision loss
- **Multi-Base Support**: Handles input values in different number bases (2-16)
- **Gauss-Jordan Elimination**: Robust linear algebra solver for polynomial systems
- **BigInt Integration**: Supports arbitrarily large integers
- **Modular Design**: Clean separation of concerns with helper functions and classes
- **Error Handling**: Comprehensive validation and error checking
- **Performance Optimized**: Efficient algorithms for large-scale computations

## Prerequisites

- Node.js (version 14.0.0 or higher)
- No external dependencies required (uses only built-in JavaScript features)

## Installation

1. Clone or download the project files
2. Ensure Node.js is installed on your system
3. No additional installation steps required - the solution is self-contained

## Usage

### Basic Usage

```javascript
// Load the test case data
const testCase = {
    "keys": { "n": 10, "k": 7 },
    "1": { "base": "6", "value": "13444211440455345511" },
    // ... additional data points
};

// Execute the solver
const result = solvePolynomial(testCase);
console.log(result); // Outputs: coefficient1, coefficient2, ..., coefficientK
```

### Running the Solution

Execute the script using Node.js:

```bash
node solution.js
```

The output will be a comma-separated string of polynomial coefficients in fractional form (e.g., "123/456, 789, 101/202").

## Algorithm Details

### Polynomial Interpolation

The solver constructs a system of linear equations from k data points to find the coefficients of a degree (k-1) polynomial that passes through all given points.

### Gauss-Jordan Elimination

1. **Matrix Construction**: Creates an augmented matrix where each row represents a data point
2. **Forward Elimination**: Transforms the matrix into row echelon form
3. **Backward Substitution**: Solves for the coefficient variables
4. **Fraction Arithmetic**: All operations maintain exact rational representation

### Key Components

- **Fraction Class**: Handles rational number arithmetic with automatic simplification
- **parseBigInt()**: Converts multi-base string representations to BigInt
- **gcd()**: Computes greatest common divisor for fraction reduction
- **Gauss-Jordan Solver**: Performs the core linear algebra operations

## API Reference

### `solvePolynomial(data)`

Main solver function that takes input data and returns polynomial coefficients.

**Parameters:**
- `data` (Object): Input data containing keys and data points
  - `keys.n` (number): Total number of data points
  - `keys.k` (number): Number of points to use for interpolation
  - `[i]` (Object): Data point i with `base` and `value` properties

**Returns:**
- `string`: Comma-separated coefficients in fractional notation

### `Fraction` Class

Handles exact rational arithmetic operations.

**Methods:**
- `add(other)`: Adds two fractions
- `subtract(other)`: Subtracts two fractions
- `multiply(other)`: Multiplies two fractions
- `divide(other)`: Divides two fractions

### Helper Functions

- `gcd(a, b)`: Computes greatest common divisor
- `abs(n)`: Returns absolute value for BigInt
- `parseBigInt(str, base)`: Parses string to BigInt in specified base

## Example

Given the test case with 10 data points and k=7, the solver will:

1. Parse each value from its respective base to decimal
2. Construct a 7x8 augmented matrix
3. Apply Gauss-Jordan elimination
4. Return the exact rational coefficients

Sample output format:
```
123456789/987654321, 2468013579/1357924680, 369258147/258147369, ...
```

## Testing

The solution includes a comprehensive test case (`testCase2`) that demonstrates:

- Multi-base input handling (bases 3, 6, 7, 8, 12, 15, 16)
- Large integer processing
- Exact coefficient calculation
- Error-free execution

To verify correctness:
1. Run the script: `node solution.js`
2. Compare output coefficients with expected values
3. Validate that the polynomial passes through all input points

## Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch
3. Implement your changes with comprehensive tests
4. Ensure all existing tests pass
5. Submit a pull request with detailed description

### Development Setup

```bash
# Clone the repository
git clone <repository-url>

# Make your changes
# Ensure Node.js compatibility

# Test your implementation
node solution.js
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Note**: This implementation is designed for educational and research purposes. For production use in critical systems, additional validation and testing may be required.

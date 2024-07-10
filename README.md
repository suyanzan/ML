# Optimization Problem

## Problem Description

We aim to optimize two variables, `y1` and `y2`, with the following constraints and goals:

- **y1**:
  - Value range: 0.1 to 1
  - Goal: Maximize (higher is better)

- **y2**:
  - Value range: 1 to 15
  - Goal: Minimize (lower is better)

Each variable has an equal weight of 50% in the overall optimization objective.

## Objective Function

To express the optimization objective mathematically, we need to normalize both variables to ensure they are on the same scale. Here’s how we can do it:

1. **Normalization of y1**:
   - Normalized \( y1 \) ( \( y1_{norm} \) ) = \( \frac{y1 - y1_{min}}{y1_{max} - y1_{min}} \)
   - For \( y1 \): \( y1_{norm} = \frac{y1 - 0.1}{1 - 0.1} \)

2. **Normalization of y2**:
   - Normalized \( y2 \) ( \( y2_{norm} \) ) = \( \frac{y2_{max} - y2}{y2_{max} - y2_{min}} \)
   - For \( y2 \): \( y2_{norm} = \frac{15 - y2}{15 - 1} \)

3. **Overall Objective**:
   - Objective function \( Z \):
   \[
   Z = 0.5 \times y1_{norm} + 0.5 \times y2_{norm}
   \]
   - This function \( Z \) should be maximized.



### Example Calculation

Assume we have \( y1 = 0.5 \) and \( y2 = 5 \):

1. Normalize \( y1 \):
   \[
   y1_{\text{norm}} = \frac{0.5 - 0.1}{1.0 - 0.1} = \frac{0.4}{0.9} \approx 0.444
   \]

2. Normalize \( y2 \):
   \[
   y2_{\text{norm}} = \frac{15 - 5}{15 - 1} = \frac{10}{14} \approx 0.714
   \]

3. Calculate the combined score:
   \[
   \text{score} = 0.5 \times 0.444 + 0.5 \times 0.714 = 0.579
   \]

By following this approach, we can evaluate and optimize the given variables to achieve the best possible outcome.

## Implementation

Here is a simple Python implementation to compute the objective function given `y1` and `y2`:

```python
def normalize_y1(y1):
    return (y1 - 0.1) / (1 - 0.1)

def normalize_y2(y2):
    return (15 - y2) / (15 - 1)

def compute_objective(y1, y2):
    y1_norm = normalize_y1(y1)
    y2_norm = normalize_y2(y2)
    Z = 0.5 * y1_norm + 0.5 * y2_norm
    return Z

# Example usage
y1 = 0.5
y2 = 10
objective_value = compute_objective(y1, y2)
print(f'The objective value is: {objective_value}')

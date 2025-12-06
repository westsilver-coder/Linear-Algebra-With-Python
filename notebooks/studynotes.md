# Chapter 1 — Linear Equation System  
RAW Markdown Studynote (all symbols visible)

---

## 1. Basic Concept of Linear Equation Systems

A linear system can be written in matrix form:

$$A\mathbf{x} = \mathbf{b}$$

Where:  
- A : coefficient matrix  
- x : vector of unknowns  
- b : constant vector  

In Python:

```python  
A @ x          # matrix multiplication  
A @ x - b      # residual of Ax = b  
```
## 2. Matplotlib Structure (fig, ax)  
```python  
fig, ax = plt.subplots(figsize=(12,7))  
```  
- fig = the entire figure (canvas)  
- ax = the actual axes where plots are drawn  
Most plotting functions use ax:  
- ax.plot()  
- ax.scatter()  
- ax.text()  
- ax.grid()

## 3. Common Plotting Functions  
ax.plot()  
```python
ax.plot(x, y, lw=3, label='line')  
```  
- lw = line width

ax.scatter()  
```python
ax.scatter(X, Y, s=200, color='red', zorder=3)
```  
- s = marker size  
- zorder = drawing order (larger -> drawn above)  

ax.text()  
```python
ax.text(1, 5,5, '(1, 5)', fontsize=20)
```  
Texts are placed slightly above the actual point to avoid overlap.

alpha (transparency)  
```python
alpha=0.5  
```   
- 1.0 = fully opaque  
- 0.0 = fully transparent  
- used to see overlapping surfaces/plots clearly

### 4. Meshgrid vs. Mgrid  
meshgrid   
```python    
x = np.arange(-3, 4)  
y = np.arange(-3, 4)  
X, Y = np.meshgrid(x, y)  
```  
Creates a full 2D grid from 1D arrays.  

mgrid  
```python
X, Y = np.mgrid[-2:2:21j, 2:6:21j]  
```  
21j = "create 21 evenly spaced points".  
More compact and often used for 3D surfaces.

### 5. 3D Plotting  
Create 3D axis  
```python  
fig = plt.figure(figsize=(9,9))
ax = fig.add_subplot(111, projection='3d')
```  

3D scatter  
```python  
ax.scatter(X, Y, Z, s=100)
```  

3D surface  
```python  
ax.plot_surface(X, Y, Z, cmap='viridis', alpha=0.5)
```

### 6. SymPy rref()  
To compute the reduced row echelon form.  
```python  
A_rref = A.rref()  
```  
The return value is a tuple:  
```python  
(RREF_matrix, (pivot_column_indices))  
```  

### 7. Converting RREF Matrix to NumPy  
```python    
A_rref = A.rref()
A_rref_matrix = np.array(A_rref[0])
```  
A_rref[0] = the actual RREF matrix  
Converting to NumPy is useful for numerical operations.

### 8. Extracting the Last Column (constants)  
```python  
poly_coef = [A_rref[0][i, -1] for i in range(A_rref[0].shape[0])]  
```  
Meaning:  
- loop through each row  
- take the last column (-1)  
- collect them into a list  
This extracts the constant terms from the augmented matrix.

### Summary of Chapter 1
- Linear systems are represented as A x = b  
- @ = matrix multiplication  
- meshgrid/mgrid produce coordinate grids  
- 3D plots require projection='3d'  
- alpha controls transparency  
- rref() gives (RREF matrix, pivot columns)  
- extract last column for solution vector  
- use np.full() to create constant-filled arrays  
- smooth lines come from dense x-values

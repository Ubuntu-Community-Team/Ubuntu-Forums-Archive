---
title: "Define global variables"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by newport_j on 2010-01-11
```


#include <stdio.h>
#include <stdlib.h>
#include <cuda.h>
#include <cuda_runtime.h>
#include <time.h>

// Matrices will be stored in row major order
// M(row, col) = *(M.elements + row * M.stride + col)
typedef struct  {
       int width;
       int height;
       int stride;
       float *elements;
} Matrix;

// Thread block size
#define BLOCK_SIZE 16

// Get a matrix element
__device__ float GetElement(const Matrix A, int row, int col)
{
    return A.elements[row * A.stride + col];
}
// Set a matrix element
__device__ void SetElement(Matrix A, int row, int col, float value)
{
  A.elements[row * A.stride + col] = value;
}

// Get the BLOCK_SIZExBLOCK_SIZE sub-matrix Asub of A that is
// located col sub-matrices to the right and row sub-matrix down 
// from the upper-left corner of A
__device__ Matrix GetSubMatrix(Matrix A, int row, int col)

{
   Matrix Asub;
   Asub.width    = BLOCK_SIZE;
   Asub.height   = BLOCK_SIZE;
   Asub.stride   = A.stride;
   Asub.elements = &A.elements[A.stride * BLOCK_SIZE * row + BLOCK_SIZE * col];

   return Asub;
}


```When I am in subroutine in GDB debugger and I ask it to print out BLOCK_SIZE  it says no symbol "BLOCK_SIZE" in current context. Yet,  I define it globally at the top of the program. Like :

#define BLOCK_SIZE 16

So BLOCK_SIZE equals 16. Now in the calculations in    __device__ Matrix GetSubMatrix(Matrix A, int row, int col)., are all okay. Everything that includes BLOCK_SIZE in the calculation is works out to what it should be if BLOCK_SIZE were 16.. They would be 

Asub.width    = BLOCK_SIZE;
   Asub.height   = BLOCK_SIZE;
   Asub.stride   = A.stride;
   Asub.elements = &A.elements[A.stride * BLOCK_SIZE * row + BLOCK_SIZE * col];

So how can it do those calculations if it does no know the BLOCK_SIZE is 16? At least it says it does not know that, but the calculations say otherwise.


Newport_j.

---

### Post by Anatashinu on 2010-01-11
I think it might be useful to know what language you're using hehe

---

### Post by newport_j on 2010-01-12
I am using c the variation of it is for NVIDIA CUDA, but i believe that the lanaguage issue here is basic c. 
 
newport_j

---

### Post by avidday on 2010-01-14
> Yet,  I define it globally at the top of the program. Like :

#define BLOCK_SIZE 16

So BLOCK_SIZE equals 16.

BLOCK_SIZE is only a preprocessor symbol. During preprocessing, all references to block size are replaced with the constant 16 by macro expansion. The compiler never sees BLOCK_SIZE, never generates a symbol for it, and that is why you can't see anything in the source debugger. 

This is covered in the first few pages of any decent book on the C programming language, like this one:  [http://cm.bell-labs.com/cm/cs/cbook/](http://cm.bell-labs.com/cm/cs/cbook/) . I am sure one of the libraries you have at your disposal has a copy you could borrow and read.

---

### Post by lorsen on 2010-01-14
naive question: Can't you just write 
```
int BLOCK_SIZE; 
```(instead of #define BLOCK_SIZE 16) and in an init function (or in the first one you use) BLOCK_SIZE=16;

---

### Post by avidday on 2010-01-14
> **lorsen said:**
> naive question: Can't you just write 
```
int BLOCK_SIZE; 
```(instead of #define BLOCK_SIZE 16) and in an init function (or in the first one you use) BLOCK_SIZE=16;

Not in this case, no.

The compilation process used for this sort of code (it is NVIDIA CUDA rather than plain C90) won't permit that. The code you see winds up being split into pieces, compiled with two separate  compilers into completely separate code objects and run in separate memory spaces (some on the host CPU, some on the GPU).

There is a method of constant propagation which will do what you are thinking of, but it is rather different to your code. It is also considerably slower than using the preprocessor, which is why you wouldn't use it for something like this which is an algorithm structure constant, rather than a constant data value or coefficient.

---


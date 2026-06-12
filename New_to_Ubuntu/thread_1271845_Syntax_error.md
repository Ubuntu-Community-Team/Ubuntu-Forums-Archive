---
title: "Syntax error?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by newport_j on 2009-09-21
My cuda_instrument program analysis is gagging on this file:

cuseful.h

void fatal(const char * msg);
void getComputeNumber(int * major, int * minor);
void checkDoubleCapable(const char * failMsg);
// void * xmalloc(size_t nbytes);
// float * fMalloc(size_t numElts);
// double * dMalloc(size_t numElts);
// size_t * stMalloc(size_t n);
char * getTime();
void getRandVect(float * vect, size_t n);
void printVect(int n, const float * vect, const char * msg);
void printMat(int rows, int cols, const float * mat, const char * msg);
void checkCudaError(const char * msg);
int hasCudaError(const char * msg);
float * getMatFromFile(int rows, int cols, const char * fn);james ~/Desktop


Now it gives an output error message as:


james ~/Desktop/cuda_instrument$ ./cuda_instrument.pl  kendall.cu instr.cu race
-E- Fatal error parsing input file (see errors below for line numbers in temporary file)

/usr/include/cuseful.h[9:18-31] : syntax error
Parsing error
Fatal error: exception Frontc.ParseError("Parse error")


Which is the literal output. I am not sure what is wrong with this code. It says the syntax error is in line 9. Which is now shown separately:


void getRandVect(float * vect, size_t n);

It looks fine to me. What is the syntax error?


Respectfully,

newport_j

---

### Post by avidday on 2009-09-21
There is no syntax error. To quote directly from the cuda_instrument readme:

> Although only CUDA kernels are instrumented, the tool must parse the entire
source file, including any host code. If the tool is having trouble parsing
your source file, and your source file contains more than just the CUDA
kernel that you want to instrument, try creating a new file that contains
only the CUDA kernel of interest and re-running the tool on the new file.You are misusing the cuda_instrument tool. It isn't intended for parsing host code, particularly host code which relies on C++ and C99 language features which are not supported by the C90 compiler nvcc uses to compile device code. I would invite you to actually try compiling the code, but I am guessing you still don't have a functional CUDA installation or hardware with which to do so.

---


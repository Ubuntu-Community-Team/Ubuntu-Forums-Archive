---
title: "CUDA thread"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by cherishcc on 2009-07-23
```

#include <stdio.h>
#include <stdlib.h>
#include <cuda_runtime.h>

#define BLOCK_DIM 512

const int size_x=512;
const int size_y=1;

__global__ static void ThreadDemo1(unsigned int* ret)
{
  unsigned int xindex=blockDim.x*blockIdx.x+threadIdx.x;
  unsigned int yindex=blockDim.y*blockIdx.y+threadIdx.y;

  if(xindex<size_x && yindex<size_y)
  {
     unsigned int index=xindex+size_x*yindex;
     ret[index]=xindex;
     ret[index+size_x*size_y]=yindex;
  }
}

void ThreadDemo1()
{
  unsigned int* ret=0;
  unsigned int  host_ret[size_x*size_y*2]={0};
  int i=0;

  cudaMalloc((void**) &ret, sizeof(unsigned int)*(size_x*size_y*2));

  dim3 grid(size_x / BLOCK_DIM, 1);
  dim3 block(BLOCK_DIM,1,1);

  ThreadDemo1<<<grid,block>>>(ret);

  cudaMemcpy(&host_ret, ret, sizeof(unsigned int)*(size_x*size_y*2), cudaMemcpyDeviceToHost);

  for(i=0; i<size_x*size_y; i++)
  {
    [COLOR=Red] printf(¨(%d,%d)¨,host_ret[i],host_ret[size_x*size_y*i]);[/COLOR]
  }
  cudaFree(ret);
}


```

This is a CUDA programme about testing the threads. When I compile it, it says 

threadDemo.cu(41): error: unrecognized token

threadDemo.cu(41): error: expected an expression

threadDemo.cu(41): error: unrecognized token

threadDemo.cu(41): error: unrecognized token

threadDemo.cu(41): error: unrecognized token

the line 41 is the line in red. 

who can tell me why it is unrecognized? Thanks

---


---
title: "Mpi"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by AlwaysNewbie on 2011-06-18
Hello! I am trying to learn MPI in Ubuntu. :)

I am installed mpich2:
```

sudo apt-get install mpich2

```After succesfull installation, I wrote this simple code and "Makefile" to test libraries:
```

#include <stdio.h>
#include <mpi.h>

int main(int argc, char *argv[]) {
}

``````

all:
    mpicc -o test.bin ./test.c
run:
    mpirun ./test.bin

```And I got message that telling me about  "lcr" library. Linker can not find it. It is strange for me. What can I install to make "mpicc" working properly? 

Thanks!;)

---


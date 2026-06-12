---
title: "kdevelop doesn't create executable program"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by nfbueno on 2009-01-25
In kdevelop I created a new project (I named it myhello2) and selected a C simple hello world program. Kdevelop generated the following code
> 
#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
  printf("Hello, world!\n");

  return EXIT_SUCCESS;
}



Then I clicked the run icon. The output from the console reads
> 
/bin/sh: /home/nestor/myhello2/debug/./src/myhello2: not found
Press Enter to continue!


I tried to compile a simple "hello world" program at the command line using gcc and the gcc was able to create the executable program. It run ok.

Any help, please? I would appreciate it.

---


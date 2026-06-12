---
title: "Trying to execute a C program in bash."
date: 2009-06-21
forum: New to Ubuntu
---

### Post by billcurtis14 on 2009-06-21
I've used gcc and it compiles fine. When I try to run the program, I get this
```
./99chan.c: line 8: syntax error near unexpected token `('
./99chan.c: line 8: `int main()'
```Here's the C program:
```
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <stdlib.h>

int main()
{
int x[100];
int i = 0;
for(; i < 100; i++){
    x[i]=i;
}
int fd = open("abc", O_WRONLY|O_CREAT);
write(fd, x, 100);


exit(0);
}
```

---

### Post by Bachstelze on 2009-06-21
You can't run C code directly (well you can with [font="monospace"]tcc[/font], but it's probably not what you want). You must compile it before:

```
cc -o 99chan 99chan.c
./99chan
```

---


---
title: "Help on using VI editors and GCC compilers"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by madhanacdc on 2008-07-10
hi friends....

im madhan, studying b.tech computer science and engineering 3rd year. i have a practical lab called "Network Programming" . we did a program on establishing tcp/ip connection between client and server. i should practice these programs in my pc. first i tried on my pc by writing a simple program

```
#include<stdio.h>
int main()
{
 printf("hi linux");
 return 0;
}
```

when i compile this program in my pc, a error message called "stdio.h file or folder doesn't exist". how to resolve it....
how do i install gcc compiler in ubuntu???? 
since im new to ubuntu i have no idea what to do now. 
someone help me. thanks in advance

---

### Post by HalPomeranz on 2008-07-10
Hmmm, sounds like you don't have all the packages installed that you need.  stdio.h is part of the libc6-dev package, so run this command:

```

sudo apt-get install libc6-dev

```

---


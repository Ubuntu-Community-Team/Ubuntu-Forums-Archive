---
title: "C array array max"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by lizards160 on 2009-12-30
Hello
I apologize if this is in the wrong area. I am new to the forum.

I am working on a complex simulation in C. I will end up with a huge number of array of this length.

 ```
const long int length = 500000;
```When I was doing this I added the first 5 arrays and it was working like a charm. When the next set of 5 arrays was added it kept giving me a 

```
Program has been terminated receiving signal 11 (Segmentation fault)
```I need to have a ton of arrays that are the same length and are incredibly long. I am using a format similar to this( I wont post the actual code as it would be to long and it can be simplified. )

```

#include <stdio.h>
#include <stdlib.h>

const long int length = 500000;// this is the preferred length

int main (int argc, char *argv[])
{
// working section
int s1[length]; // these first 5 arrays
int s2[length]; // are the ones that 
int s3[length]; // work with the current length
int s4[length]; 
int s5[length];

//this is the section i added that gave me the segmentation error
int s6[length];
int s7[length];
int s8[length];
int s9[length];
int s10[length];

return 0;
}

```The code works fine if i lower the length down to 100000 but the legth really needs to be 500000. 

Thanks for your help!

---

### Post by lavinog on 2009-12-30
For stuff like this there is a programming talk section in the other community section.
I think the problem is that creating arrays like that require a continuous block of memory.
In other words arrays cannot be fragmented (like files on the filesystem)

What is going to be stored in these arrays?
You could use malloc to create a variable array that doesn't need the continuous block of memory.

---


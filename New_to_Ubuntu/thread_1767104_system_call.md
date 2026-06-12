---
title: "system call"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by manish411 on 2011-05-25
I am learning linux programming from a book called "Beginning Linux Programming"
we are writing a simple  program called simple_copy.c:
 
#include <unistd.h>
#include <stdlib.h>
int main()
{
if ((write(1, &#8220;Here is some data\n&#8221;, 18)) != 18)
write(2, &#8220;A write error has occurred on file descriptor 1\n&#8221;,46);
exit(0);
}
and we are supposed to run it by 
$./simple_copy 

but this is not working
instead I had to compile it using gcc compiler
and run the ./a.out command.

---

### Post by Wim Sturkenboom on 2011-05-25
```

gcc simple_copy.c -o simple_copy

```

And please post your code between [noparse]```
 and 
```[/noparse] tags.

---

### Post by matt_symes on 2011-05-25
Hi

> **manish411 said:**
> I am learning linux programming from a book called "Beginning Linux Programming"
we are writing a simple  program called simple_copy.c:
 
#include <unistd.h>
#include <stdlib.h>
int main()
{
if ((write(1, “Here is some data\n”, 18)) != 18)
write(2, “A write error has occurred on file descriptor 1\n”,46);
exit(0);
}
and we are supposed to run it by 
$./simple_copy 

but this is not working
instead I had to compile it using gcc compiler
and run the ./a.out command.

You have to compile and link it because it is a C program. The C code above needs to be converted into machine code the computer can understand. This is normal.

> **Wim Sturkenboom said:**
> ```

gcc simple_copy.c -o simple_copy

```And please post your code between [noparse]```
 and 
```[/noparse] tags.

As Wim has shown, this will compile and link the program using the output name of  simple_copy and not a.out.

a.out the the default name used by the GCC when no output file name is specified.

Kind regards

---

### Post by manish411 on 2011-05-25
Thanks that worked pretty well for me!!

---

### Post by Wim Sturkenboom on 2011-05-26
Great; please mark your thread as solved using the thread tools just above the first post.

There is, by the way, a dedicated [programming section](http://ubuntuforums.org/forumdisplay.php?f=39) on Ubuntu forums.

---


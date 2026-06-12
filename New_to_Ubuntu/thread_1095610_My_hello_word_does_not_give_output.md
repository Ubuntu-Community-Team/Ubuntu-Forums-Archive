---
title: "My hello word does not give output?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by hums07 on 2009-03-13
Sorry for dumb question.
I am trying to start C programming in Linux. The program is as follows:
```
#include <stdio.h>

int main()
{
  printf("hello World!");
  return 1;
}
```

then in the terminal I run:
```
gcc test.c -o test
```
gcc compiles the file without error. However, when I run the program, it does not give the expected output. Do I miss something?

---

### Post by taurus on 2009-03-13
What kind of output so you expect?  There is no line break so you would see **hello World!**taurus@linux:~$

Why don't you modify it a little to make it look like this?

```

#include <stdio.h>

int main()
{
  printf("hello World!**[COLOR="Blue"]\n[/COLOR]**");
  return 1;
}

```

---

### Post by hums07 on 2009-03-13
Oops, I should v said: It does not give any output at all.
Thanks taurus for the quick response.

---

### Post by taurus on 2009-03-13
How did you run the binary, ./test?

```
gcc test.c -o test
./test
```
And this is what I get, after adding \n in there.

```
hello World!
```

---

### Post by ad_267 on 2009-03-13
Also, you should be returning 0 if your program executes successfully. Returning 1 means there has been an error.

---


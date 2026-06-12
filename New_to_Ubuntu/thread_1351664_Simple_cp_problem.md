---
title: "Simple cp problem"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by rchristy1 on 2009-12-10
I am very new to Ubuntu and I am having trouble with the simple cp command.

I keep getting this error:
 cp: cannot create regular file `/Desktop/Ryan': No such file or directory
I have posted what I put in below.
How is /Desktop/Ryan not a directory.


rchristy1@rchristy1-desktop:~/Desktop$ ls
Ang  Copied  firefox.desktop  Hannah  Link to Music  Link to Videos  Pictures  Ryan
rchristy1@rchristy1-desktop:~/Desktop$ cd Copied
rchristy1@rchristy1-desktop:~/Desktop/Copied$ ls
Ryan_Ubuntu_Tricks.odt
rchristy1@rchristy1-desktop:~/Desktop/Copied$ cp Ryan_Ubuntu_Tricks.odt /Desktop/Ryan
cp: cannot create regular file `/Desktop/Ryan': No such file or directory
rchristy1@rchristy1-desktop:~/Desktop/Copied$

---

### Post by llamabr on 2009-12-10
rchristy1@rchristy1-desktop:~/Desktop/Copied$ cp Ryan_Ubuntu_Tricks.odt /Desktop/Ryan

you need ~/Desktop/Ryan/

the ~ tells it to start in your home directory.  without it, you were starting at / which is the root dir.  do you see?

---

### Post by bshosey on 2009-12-10
is there a folder on your desktop called Ryan?

---

### Post by cholericfun on 2009-12-10
i dont see it but maybe it helps if you post the output of

```
ls -l
``` instead of ```
ls
```

whis way one can see a bit more detail (owners and such) and since youre using whitespace in your foldernames its hard to see where one starts and the other ends...

---

### Post by bshosey on 2009-12-10
llamabr: Good eye did not see that one!

---

### Post by CharlesA on 2009-12-10
> **llamabr said:**
> rchristy1@rchristy1-desktop:~/Desktop/Copied$ cp Ryan_Ubuntu_Tricks.odt /Desktop/Ryan

you need ~/Desktop/Ryan/

the ~ tells it to start in your home directory.  without it, you were starting at / which is the root dir.  do you see?

Nailed it.

---

### Post by cholericfun on 2009-12-10
> **llamabr said:**
> rchristy1@rchristy1-desktop:~/Desktop/Copied$ cp Ryan_Ubuntu_Tricks.odt /Desktop/Ryan

you need ~/Desktop/Ryan/

the ~ tells it to start in your home directory.  without it, you were starting at / which is the root dir.  do you see?

ahhh of course...

or use the dots...

i.e.
```
 cp file ../Ryan
```

where . means *this* directory and .. the *above* directory and
../../ *two dirs above* etc.

---

### Post by rchristy1 on 2009-12-10
Thank you very much. I did not understand what ~ meant.

---


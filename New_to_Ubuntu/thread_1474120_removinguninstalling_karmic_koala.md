---
title: "removing/uninstalling karmic koala"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by zeytin on 2010-05-05
Hi everyone,


here is the problem that i have been trying to solve for a long time :(

when i turn on my computer, there are 2 options : ubuntu and vista (until here everything is ok).

1. when i choose ubuntu, it gives an error without a number or anyhitng just this line: " error: file not found"

2. then it continuous and opens the desktop.
3. wireless is not recognized.
4. computer janitor is not open, it also gives error.



I am an ABSOLUTE BEGINER, i think i did something wrong, but i cannot fix it(i tried several suggestions from some other threads which is related with wireless problems).   So far what want to do is remove/unistall karmic koala completely, can someone please tell me (step by step) how?  thanks.

---

### Post by nhasian on 2010-05-05
Do you know if you put ubuntu on its own partition? or did you install it inside of windows vista via wubi?  

if you installed it in windows, then in vista go to the control panel-> add/remove software, and remove ubuntu.  then you can install the latest Ubuntu 10.04.

If ubuntu is on its own partition, simply boot from the 10.04 LiveCD and proceed to install it like new.  Make sure you don't overwrite your vista partition.

---

### Post by zeytin on 2010-05-05
thanks for this quick reply.

and yes, I installed ubuuntu in vista via wubi, and I do not have any idea about this "partition" thing.

I will try ur suggestion :)

---

### Post by JKyleOKC on 2010-05-05
> **zeytin said:**
> I think i did something wrong, but i cannot fix it(i tried several suggestions from some other threads which is related with wireless problems).   So far what want to do is remove/unistall karmic koala completely, can someone please tell me (step by step) how?  thanks.It sounds as if you might have, in Windows, removed the folder named Ubuntu that wubi creates. This folder is used as the Ubuntu hard disk, and the "file not found" error is probably coming from the Windows loader when it tries to switch to that folder to run Ubuntu. If this is what happened, then the attempt to remove the program from Windows' control panel will probably fail also because it won't be able to locate the folder to remove it (sounds less than logical, but that's the way "add/remove programs" has always acted in my experience going back to Windows 3.0).

There's a "boot.ini" file in WinXP, and undoubtedly something similar in Vista and Win7, that gives you the initial menu. If the add/remove attempt fails, you can edit this file to remove the line about Ubuntu and you should be in good shape. Be extremely careful with the edit, though, because if this file gets corrupted you'll probably have to go the full recovery route and lose all your data and configuration! In particular, don't try to edit it with a word processor; use a plain text editor.

---

### Post by madjr on 2010-05-05
> **zeytin said:**
> thanks for this quick reply.

and yes, I installed ubuuntu in vista via wubi, and I do not have any idea about this "partition" thing.

I will try ur suggestion :)

ok this is for you

[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

[http://youtube.com/watch?v=Z0tNpt5RZYI](http://youtube.com/watch?v=Z0tNpt5RZYI)

enjoy :)

---


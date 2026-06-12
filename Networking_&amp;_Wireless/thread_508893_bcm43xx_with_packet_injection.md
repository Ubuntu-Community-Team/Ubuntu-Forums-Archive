---
title: "bcm43xx with packet injection"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Zeroedout on 2007-07-24
hello, I'm using the bcm43xx driver for my wireless card and it seems to not support packet injection. After a google search, I came across a mailing list post about how it shouldn't be in the driver but in another part of the kernel, and in another forum of how it is terribly difficult to set up. Does anyone know where I can grab the patch to support packet injection (if someone wrote it yet), if not, how hard of a task is this? I'm using 2.6.22, compiled myself, on a Dell D400 (fiesty fawn). Thanks in advance.

---

### Post by Zeroedout on 2007-07-27
Okay, so I found the patch, unfortuantly it was for the 2.6.20 kernel, but I thought, what the hell, i'll try to patch the driver in 2.6.22 anyway, since I don't there were any changes. The patch seemed to apply okay, and diff showed that there was indeed a difference between the two modules, however packet injection doens't seem to be working. Anyone have packet injection working correctly using the bcm43xx module?

---

### Post by FXFman1209 on 2007-10-24
I'm trying to do the same thing, except I'm using Gutsy with the 2.6.22 kernel. I found this:

[http://tinyshell.be/aircrackng/forum/index.php?topic=281.msg14044#msg14044](http://tinyshell.be/aircrackng/forum/index.php?topic=281.msg14044#msg14044)

However, I have NO idea what to do with that file that they give me. Can anyone help?

---

### Post by kevdog on 2007-10-25
Ive never done what you want to do, but after reading the instructions, you need to recompile the kernel from source.  You basically need to download the source for the kernel you want -- it should be in the repository, and then patch the kernel sources (which is a one line statement as listed in the post you referenced).  You then need to compile and then reinstall the kernel.  There are some tutorials about how to do this in the tuturial section in the forums.  Please be aware that although compiling and installing the kernel isnt hard, it will probably take you a few times to configure the kernel properly -- it takes a while to learn how to do this.  This is the hardest part.

---


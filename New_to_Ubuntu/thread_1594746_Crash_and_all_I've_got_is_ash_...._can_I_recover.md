---
title: "Crash and all I've got is ash .... can I recover ?"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Gudjon on 2010-10-12
Hello!

Did som weird mistake.
Running my desktop with Ubuntu 10.04 and I was saving some work to my USB-stick.
The USB-stick has an older Ubuntu-version that I have been trying out, I have also created a folder named 'mystuff' - I copied some stuff to that stick.
Leaving home today, I did press the 'hibernate' option.
Coming back from town, I pressed the 'on/off'-button on my computer and the computer starts up from my USB - that was not what I wanted.
 
I pull out the USB and press the 'on/off'-button -wanting to get to my computer.
 
I am now met by a black-screen.
the text says:
[INDENT]'mount: mounting /dev on /root/dev failed: No such file or directory'
'Target filesystem doesn't have /sbin/init.'
'No init found. Try passing init=bootarg'
[/INDENT] 
Then it say:
[INDENT]'BusyBox v1.13..3 ( Ubuntu 1:1.13.3-1ubuntu11) built-in shell ( ash )
Enter help for a list of built-in commands '
 
[/INDENT]Is it possible to restore my system the way it was ?
I have been installing a variety of programs that took me a while ( had the version 10.x since March this year ).
 
My Best regards, Gudjon

---

### Post by ft-Orchard on 2010-10-12
Try these: 

[http://ubuntuforums.org/showthread.php?t=1244466](http://ubuntuforums.org/showthread.php?t=1244466)
[http://ubuntuforums.org/showthread.php?t=295508](http://ubuntuforums.org/showthread.php?t=295508)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8748384](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8748384)

---

### Post by Gudjon on 2010-10-12
Thanks for your reply.
 
/bin/sh: sudo : no found
 
-G

---

### Post by sandyd on 2010-10-12
> **Gudjon said:**
> Thanks for your reply.
 
/bin/sh: sudo : no found
 
-G
boot to livecd and post output of
```

sudo fdisk -l
```

---

### Post by ft-Orchard on 2010-10-12
> **Gudjon said:**
> Thanks for your reply.
 
/bin/sh: sudo : no found
 
-G

Install and setup sudo:
```

$ su
$ (enter root password)
[COLOR=Black]$ apt-get install sudo

```Then add the following line to "[/COLOR][COLOR=Black][FONT=monospace]/etc/sudoers"
(first do "su" again)
[/FONT][/COLOR][FONT=monospace][COLOR=Black]
[/COLOR][/FONT][COLOR=Black]%your username% ALL=(ALL) ALL[/COLOR]

---


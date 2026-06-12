---
title: "Gnu Grub version 1.97 - beta 4"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by zabo on 2010-02-07
Hello. This is my first post and my second week on Linux, so forgive me if I'm missing something painfully obvious.

Last night I received an update in Ubuntu and I did it.

Now when I restart I get the "Gnu Grub version 1.97 ~ beta 4" screen.

So, I tried following the instructions here:
[http://ubuntuforums.org/showthread.php?t=1398113](http://ubuntuforums.org/showthread.php?t=1398113)

but when I typed in 'search -f/boot/grub/grub.cfg'
I get the error message "unknown argument '-/'

Can someone give me a newbie-friendly solution?
Thanks a lot!

---

### Post by Kevbert on 2010-02-07
Welcome to Ubuntu. 
There should be a space between -f and /boot
```
search -f /boot/grub/grub.cfg
```
What version of Ubuntu are you using ? Use
```
uname -a
```
in Applications-Accessories-Terminal.
What are you trying to achieve ?

---

### Post by zabo on 2010-02-07
Thanks for the correction.

The goal here is to get back into Ubuntu -- see my desktop and access my documents.

Will following your instructions get me there?

---

### Post by zabo on 2010-02-07
When I type in 'search -f boot/grub/grub.cfg' the reply is 'loop0' and then I get just sh:grub> again...

How can I get back into Ubuntu?
Please help.
Thanks!

---

### Post by meierfra. on 2010-02-07
You have been hit by a bug in Grub2 . For more details and how to solve the problem see:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by jcdlinux on 2010-02-12
Hi,

Currently when I boot to Ubuntu using wubi I get the Gnu Grub version 1.97~beta 4 error as well. I have had this problem twice. The first time, I replaced the wubildr file and it worked. This time (after updating Ubuntu again) I get the error except replacing the file does not work anymore (maybe because I'm replacing with the same file). This means that even if you replace the file, it will eventually happen again.

Are there any other possible solutions? Or maybe a newer version of the wubildr file?

---

### Post by meierfra. on 2010-02-12
> This means that even if you replace the file, it will eventually happen again.
I think you have the same symptoms but a different problem.
Could you start a new thread? To get started follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt in your new thread.

Also post a link to your new thread in this thread.

---


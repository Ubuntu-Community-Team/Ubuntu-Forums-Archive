---
title: "Wireless problems:"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by calvinps on 2008-07-12
Hello!

I am having a few problems trying to get my wireless card to work.

I have used Terminal codes in a thread by Tinkel:
[http://ubuntuforums.org/showthread.php?p=5371596](http://ubuntuforums.org/showthread.php?p=5371596)

I have the resulting images here.

---

### Post by falcon61102 on 2008-07-12
Ok... yeah, because your hardware is different from Tinkel, this will be easier.  I'm trying to get some information from your card, is the an integrated chip or an addon such as USB or PCMCIA?

---

### Post by calvinps on 2008-07-12
Integrated chipset.

---

### Post by falcon61102 on 2008-07-12
Ok... I did some searching and what it appears is that Ubuntu is trying to use the wrong drivers for your card and you need to disable those and install the correct ones...  If you do a search for AR242x in the forums, you should come up with some hits, I'm reading through a couple now to try to find a fix.

---

### Post by falcon61102 on 2008-07-12
Found something... do you have a wired connection in Ubuntu.  Can you access the internet at all in Ubuntu?  If so follow the steps in this link and you should be good to go:

[http://ubuntuforums.org/showthread.php?t=849303&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=849303&highlight=AR242x)

If not, you can download the files in windows and then put them on a flash drive or somewhere else you can access in Ubuntu and then go through these steps with some modification and you should be set.

Also, you can check out this link and there is an automated script that might work for you.  You can give it a try or use the link about to do it manually.  Personally, I'd try the link above first, if that works then great otherwise try this one:

[http://ubuntuforums.org/showthread.php?t=798485&highlight=eee+wireless](http://ubuntuforums.org/showthread.php?t=798485&highlight=eee+wireless)

---


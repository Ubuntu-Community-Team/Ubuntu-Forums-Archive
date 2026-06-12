---
title: "fsck log at boot"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-12-22
fsck ran after a restart said somthing about a check was required but no log in /var/log/fsck were did it go?

---

### Post by the-penguin on 2010-12-22
What OS are you running on? Ubuntu? Fedora? etc..

and could you try to post the exact output.. it would help to clear the entire thing up.

--regards
the-penguin

---

### Post by lance bermudez on 2010-12-23
I run the computer as a server so it is always running unless it need a restart then i get the message saying it need to run a fsck. it is running ubuntu 1004. I did that the other day and saw no log in /var/log/fsck

---

### Post by plucky on 2010-12-23
I think the file is called **checkfs**

Try ```
cat /var/log/fsck/checkfs
``` and see what it contains.

Good Luck

---

### Post by lance bermudez on 2010-12-23
computer@server:/var/log/fsck$ cat checkfs
(Nothing has been logged yet.)

computer@server:/var/log/fsck$ cat checkroot
(Nothing has been logged yet.)

why is nothing logged?

---

### Post by Jay_E on 2011-02-03
Greetings!
I have same problem/question.
I have installed Ubuntu 10.10 desktop.
I did a    sudo touch /forcefsck
I did a reboot/restart.
The Ubuntu start up page said it was doing a fsck  - BUT I can not find the results.
In /var/log/fsck there are two files. Both are same length. Both are time-stamped with the boot up time.
Both say:
  " (Nothing has been logged yet.)"

I did a grep -i fsck /var/log and did not find the results....

Thanks in advance!!
Jay

PS
Is there a way to tell Ubuntu to display the startup logs instead of the Ubuntu screen with the for red dots??

Thanks again!!

---

### Post by Jay_E on 2011-03-29
3/27/2011

This is *may* a disk problem.

The problem repeats after system is shut down over 12 hours.

Problem fixed by using sysresccd.org disk mounting the hard drive and touching
/forcefsck  .

After a reboot - and running fsck, the system booted OK. 

--

I ran a detailed disk diagnostic (Gibson Research Spin-rite).
It ran for several hours and found no bad sectors.

--
Still stumped.
Jay

---


---
title: "Computer playing up after 9.04 --&gt; 9.10 upgrade"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by OllieGab on 2009-11-06
Here's my last attempt before I do a clean install and loose all my installed applications and settings etc.....

Since my upgrade to 9.10 the computer has really started to behave strangely. Right after boot up it works fine, normally for half an hour or so but sometimes only for a minute.
Menus disappear, applications don't start up, I can't even shut it down properly as the icons sometimes disappear. I can't open a terminal etc, so all I can do is turn the power off and start again, and hope for the best.

I un-installed some old kernels and re-installed the latest (for 9.10). 

Sometimes I get error messages - eg "Can't find parent directory" when trying to open an application - sometimes not.

Any suggestions? I don't want to make a clean install but will if I have to.
I have most of my stuff backed up but the latest back-up wouldn't work either: "Problems when trying to copy. Access denied".
But as I said, these things happen at random, there seems to be no pattern in it at all.

Help!

Ollie

---

### Post by cariboo on 2009-11-06
I would suggest booting from a Live CD, and running fsck on you partition.

---

### Post by samh785 on 2009-11-06
> **OllieGab said:**
> Here's my last attempt before I do a clean install and loose all my installed applications and settings etc.....

If you must do a clean install, make sure you back up your home folder. It contains hidden folders that hold the settings of the programs you have installed. :D

---

### Post by OllieGab on 2009-11-06
> **cariboo907 said:**
> I would suggest booting from a Live CD, and running fsck on you partition.

At one time I actually didn't get further than a blank screen, with a "command line environment".

I did fsck from there, it reported several errors, asked if I wanted to fix, answered yes to all requests that came up.

I've just done fsck via a live CD: 'sudo fsck /dev/sda5' (which is the partition I have for  Linux) and it came back:

'/dev/sda5 clean, 268280/6553688 files, ........'

Does that mean the partition is OK?

---


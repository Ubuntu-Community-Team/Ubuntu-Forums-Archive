---
title: "Slow Internet"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by CrazzzyBudha on 2010-11-17
I'm new to Ubuntu, and new to Linux in general. I am multi booting Ubuntu, Windows 7, and Peppermint. The problem is that the internet is very slow with Ubuntu, but not with my other OS. I have a Broadcom wireless card, the drivers were installed automatically when I installed Ubuntu. I have tried getting rid of ipv6, or whatever it is called, by changing something the etc/default/grub file as instructed by [http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)
I mainly use Chromium, and get daily builds. The problem is the same if I use Firefox as well. 

I am using wireless and 10.10 Ubuntu. Thought I should mention that.

Thanks for any help you can provide!

---

### Post by ubername on 2010-11-17
[http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/](http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/)

---

### Post by CrazzzyBudha on 2010-11-17
I tried using Open DNS by following the above instructions, and then using the instructions on their website, but that made the internet even slower.

---

### Post by SkepticalHippo on 2010-11-19
Hi, I may have a fix for this. I just updated 10.10 and noticed that both firefox and chrome were taking a long time to resolve URLs. I tried disabling ipv6 and changing DNS servers but to no avail. Then I found this old thread:

[http://www.chromeboard.com/showthread.php?p=130628](http://www.chromeboard.com/showthread.php?p=130628)

and followed the advice to edit /etc/nsswitch.conf changing the "hosts" line order by putting files and dns first and leaving the rest. Mine now looks like this:

hosts: files dns wins mdns4_minimal [NOTFOUND=return] mdns4

All browsers are now working fine :D

Hope that helps anyone else having this problem. Now I just need to fix Compiz... ;)

---

### Post by tejdig on 2010-11-20
Thank you SkepticalHippo !!! , your advice worked for me.

---

### Post by CrazzzyBudha on 2010-11-20
Dido! Thanks a lot! I will change to fixed.

---


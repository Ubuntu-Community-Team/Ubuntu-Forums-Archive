---
title: "UNE upgrade killed computer"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by LaoTan on 2010-07-03
The Windows 7 Starter OS on my new Samsung NP-140 was slow so I downloaded and installed the Ubuntu-9.10 netbook remix i-586 on it as a dual boot.  Later I started an upgrade to the Ubuntu Netbook Edition (a choice offered along with some updates). During the process everything froze up. Now when I turn on the computer all I get is this message:  
 

 error: no such device: 196f241b-3bee-4528-be53-ce854b314a79.
 grub rescue>
 

 I am a complete novice with Ubuntu and Linux but I like the Linux philosophy.  I enjoy the speed of the Ubuntu netbook remix (and many other things) but need to useWindows 7 for some programs.  Please help me to get the computer operating again.  Thanks.

---

### Post by wilee-nilee on 2010-07-03
Couple of questions, did you resize W7 with its disk manager and make sure it was booting before installing UNR.

Next post the boot script in my signature in code tags as described. Code tags can also be done by highlighting pasted text then clicking on the # in the reply panel.

---

### Post by LaoTan on 2010-07-03
Thanks for the prompt reply.  As I understand it the Samsung NP-140 hard  drive comes already divided into two partitions of equal size. The  Windows OS is in C; a Samsung recovery system in D. Following some  on-line instructions and working in Windows I created a CD with the 9.10  netbook remix on it and told it to install on D.  The remix ran  perfectly. I could choose and use either Ubuntu or Windows at each start-up.  But when the upgrade to UNE/UNR started everything jammed. I can't use  the Samsung at all and am on a different computer.  I'm sorry but I am  so Linux-illiterate that I don't understand the rest of your reply  (starting "Next...") or what appears when I click the "bootscript" link.  [Both of us sigh.]  Thanks again.

---

### Post by wilee-nilee on 2010-07-04
As far as the link goes it is set to be run from a live cd ISO like the one you installed with. Either burned to a cd or loaded onto a thumb. It sounds like you did a wubi install Ubuntu installed from a live Windows environment.

Not much can be done with your computer I believe unless you get a live Ubuntu cd to boot. If you can get booted into a live environment down load the script, follow the instructions, and copy and paste the results to a reply and highlight the text and click on the # in the panel.

If you are still confused tell me where your stuck at this may be new to you; it is and was for all of us, at some time.

---

### Post by Samulus on 2010-07-04
You can also consider using a live cd environment called "Slitaz" to run the boot script.

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

Slitaz is a slightly less user friendly (although easy to use) live environment that is only 30MBish. That's a major advantage over the Ubuntu Live CD which is around 700MB. So it saves you time and bandwidth downloading and will help you fix your problem quicker.

---


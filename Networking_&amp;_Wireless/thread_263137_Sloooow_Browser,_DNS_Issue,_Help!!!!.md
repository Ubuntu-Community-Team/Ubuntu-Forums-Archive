---
title: "Sloooow Browser, DNS Issue, Help!!!!"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by deniro0311 on 2006-09-22
I am no expert, but I will try to explain this logically.  I have 6.06 32bit on my workstation, and I love it.  I decided to replace Centos on my server and go with 6.06 64bit.  My specs are...opteron 175, dfi mobo, 4x1gb ram, 4 sata 3g 120gb drives, dual gig ethernet(nvidia port and marvell port).  I used the 6.06 64bit alternative installation disk.  I successfully got it installed with raid 1, raid 5, and LVM.  I also had to go into rescue mode to get the nvidia drivers installed.  The problem now is the internet is very slow.  I am behind an ipcop firewall/router.  It is all setup correctly as is my network settings for ubuntu.  This all worked fine in centos, so i am assuming this problem is with an ubuntu setting.  I have tried everything I could...disable ipv6 in firefox and ubuntu, fine tune browser settings in about:config, etc.  I have searched and searched and can't find an answer.  Here is a little more info.  My internet connection is dhcp going into the ipcop router.  On ubuntu i have set a static ip, and the dns has to be set to my isp's.  That is the way ipcop works.  For those of you familiar with ipcop, this is a web server so it is in the orange segment (dmz).  Again, this all worked in centos.  Could it be a driver issue?  Almost forgot.  I can ping throughout my network.  I can't ping my isp's dns servers, host unreachable.  If I ping yahoo for example, it usually times out.  My browser takes a very long time to bring up a page, if at all.  Thanks in advance for any help.

---

### Post by deniro0311 on 2006-09-22
Update

I believe its more than dns.  If i ping anything (name or ip) it usually just hangs.  Browser still works, but still very slow.

---

### Post by schmelck on 2006-09-23
[http://www.ubuntuforums.org/showthread.php?t=260538&highlight=slow+internet](http://www.ubuntuforums.org/showthread.php?t=260538&highlight=slow+internet)

---


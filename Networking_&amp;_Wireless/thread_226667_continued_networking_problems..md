---
title: "continued networking problems."
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by elleric on 2006-07-31
I have recently set up a dual boot system between XP:MCE and 6.06... Now the dual boot works wonderfuly, and windows continues to function the same as before i added the new partitions and ubuntu.

I am having trouble with my network when running ubuntu though. At first, there was no connection to the internet at all, then oddly, the connection started working... so all was well and good. but then last night i had to reboot, when i came back into ubuntu there was again no internet connectivity.

the dual booting PC is connected to a switch with several other computers, all of which have access to the internet. the switch is connected to a router which is connected to my cable modem. I can get the exact products when i get home from work, i dont have them here.

any help out there for this problem? While i am not a total beginner when it comes to linux, i am pretty far from any thought of being well versed in it so help would be much appreciated.

thanks!

---

### Post by mips on 2006-07-31
Disable IPv6 and manually configure your ISP's DNS servers in the resolv.conf file. If your router has a nameserver entry hash it out or put below the other nameservers.

[http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)

---


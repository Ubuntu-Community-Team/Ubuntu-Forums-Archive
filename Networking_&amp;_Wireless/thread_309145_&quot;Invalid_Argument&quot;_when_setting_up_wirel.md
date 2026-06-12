---
title: "&quot;Invalid Argument&quot; when setting up wireless adapter"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by sankarj12 on 2006-11-29
Hi.  I have properly installed ndiswrapper on the final release of Edgy Eft.  I added the proper driver for the NETGEAR WG111 v1 USB adapter.  I did ```
sudo ndiswrapper -m
``` to write modprobe information.  When I do ```
sudo modprobe ndiswrapper
``` I get an invalid argument.  What am I doing wrong?](*,)

---

### Post by sankarj12 on 2006-12-04
Is there anyone out there that can help me?:sad:

---

### Post by sankarj12 on 2006-12-09
The ```
sudo modprobe ndiswrapper
```works, but when I want to set my options manually (```
sudo iwconfig eth2 mode managed
``````
sudo iwconfig eth2 key XXXXXXXXXXXXXXXXXXXXXXXXXX
``````
sudo iwconfig eth2 essid XXXXXX
```) either on the key or essid setting, I get a failure.  It could not configure the adapter.  It is connected properly, and the "mode managed" works fine.  When I remove it and insert it, the lights go on for less than a second, then come off.  Can someone help?

---

### Post by coup_detat on 2007-02-24
I get the same error when I am trying to set up a netgear wg111 wireless USB adapter. It then shows the following when I look up the installed drivers

whumphrey@Linux-desktop:~$ sudo ndiswrapper -l
Installed drivers:
net111v2        invalid driver!
netwg111        invalid driver!

---


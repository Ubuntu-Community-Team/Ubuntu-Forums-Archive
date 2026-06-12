---
title: "no internet connection after installing Lubuntu 14.04.2 on hp mini 110"
date: 2015-07-04
forum: Networking &amp; Wireless
---

### Post by tuvecino808 on 2015-07-04
Hi guys, I installed lubuntu 14.04.2 on an hp mini 110 and I can't access internet at all, neither via Ethernet or wi-fi. I already spend several hours doing some research and I can't figure it out, I'm close to give up :mad: and get back to the awful windows  just cause with that OS I do get access to internet.
Is there a way to update drivers offline? or what do you recommend me to do?
Thank you for your help!

---

### Post by ajgreeny on 2015-07-04
Can you show us the output of the command **lspci**

---

### Post by tuvecino808 on 2015-07-04
> **ajgreeny said:**
> Can you show us the output of the command **lspci**

reyes@reyes-HP-Mini-110-1100:~$ sudo lspci
[sudo] password for reyes: 
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


Thank you for sharing some of your time helping me to figure this out.

---

### Post by tuvecino808 on 2015-07-04
I FIGURE IT OUT!!! :guitar: I'm so happy :p now I can get access to my WI-FI and solve an issue that i came across while experimenting. I just had to install different kernel. The next link is what opened the door for me.

[http://ubuntuforums.org/showthread.php?t=2245254](http://ubuntuforums.org/showthread.php?t=2245254)


I hope this thread can help someone else in the future ):P

---

### Post by tuvecino808 on 2015-07-04
do I have to mark as SOLVED? Or the administrator will do for me? :confused:

---

### Post by ajgreeny on 2015-07-05
You should do it even though I could do it for you.
Go to the Thread Tools menu up top and you can mark it solved from.there.

---


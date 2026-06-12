---
title: "intel eaglelake"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by acidrock on 2009-03-25
guys im trying to configure my graphic card for my new hp dc7900

here is the out put of lspci:

```
m@m-pc:~$ lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation Eaglelake HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation Eaglelake PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation Eaglelake Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation ICH10 PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation ICH10 6 port SATA AHCI Controller (rev 02)

```


here is the output of compiz --replace:

```
m@m-pc:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```


thanks all

---

### Post by NT4usB on 2009-03-25
Here's a couple [threads]("http://ubuntuforums.org/search.php?searchid=57134001") to get you started.

---

### Post by acidrock on 2009-03-26
thanks for that

but it didnt take me any where! it says:

Sorry - no matches. Please try some different terms. 

help da n00b

---

### Post by NT4usB on 2009-03-26
huh... It worked yesterday. Oh well.
Put x4500 in the searchbox at the top of the page. 
GMA graphics have been a real challenge in Ubuntu.
I have The G41 version sort of working on a Intrepid box.

---


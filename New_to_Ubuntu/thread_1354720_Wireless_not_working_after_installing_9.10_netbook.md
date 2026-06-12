---
title: "Wireless not working after installing 9.10 netbook remix"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by sophie1983 on 2009-12-14
Hi I have just installed ubuntu 9.10 netbook remix on my Samsung N140 netbook and I now don't have wireless internet. I have tried a some of the suggestions that have been posted in the forums, but so far have had no luck. Any suggestions about how to solve this would be great!!

Thanks


sophie@sophie-laptop:~$ sudo lshw -C network
[sudo] password for sophie: 
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:09:c2:83
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:3000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)


sophie@sophie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

hso0      no wireless extensions.

sophie@sophie-laptop:~$

---

### Post by bit mad on 2009-12-14
Try a search in these forums for **N130**, which is the model below and has the same problem.

---

### Post by mikewhatever on 2009-12-14
It would be interesting to know what suggestions you've tried, however, one possible solution would be to get a cable connected and then check under System->Administration->Hardware-Drivers for the wireless driver for your card.

---

### Post by ankur1990 on 2009-12-14
i m using the dell inspirion 1525 and facing the same problem abt the wireless network....
no wiireless detected.....
plz help us out

---

### Post by bit mad on 2009-12-14
> **bit mad said:**
> Try a search in these forums for **N130**, which is the model below and has the same problem.

i.e. post #5 here
[http://ubuntuforums.org/showthread.php?t=1321340&highlight=N130](http://ubuntuforums.org/showthread.php?t=1321340&highlight=N130)

Good luck

---

### Post by ukripper on 2009-12-14
> **ankur1990 said:**
> i m using the dell inspirion 1525 and facing the same problem abt the wireless network....
no wiireless detected.....
plz help us out

can you post output of this command:
```
lspci
```

---

### Post by nothingspecial on 2009-12-14
From what I've read your going to have to use ndiswrapper.


Get a wired connection

Go to Realteks site and download the driver

Then

```
sudo apt-get install ndiswrapper-common ndisgtk
```

Launch ndisgtk and browse to the downloaded driver. It is the .inf file you want.

---

### Post by Jac123 on 2009-12-14
Greetings.

Am *very* new to the world of Linux & think this might be the place to ask if anyone else has encountered a problem connecting HP Mini (notebook) to Dynalink wireless router.

I have Karmic Koala installed. Connection via ethernet is fine; just wireless refuses to show up.

Looking under System > Admin > Hardware Drivers, I see there is Broadcom STA Proprietary Wireless Driver (only).

Any advice appreciated. Otherwise it's back to XP.

Jac123.

---

### Post by mikewhatever on 2009-12-14
> **ankur1990 said:**
> i m using the dell inspirion 1525 and facing the same problem abt the wireless network....
no wiireless detected.....
plz help us out

> **Jac123 said:**
> Greetings.

Am *very* new to the world of Linux & think this might be the place to ask if anyone else has encountered a problem connecting HP Mini (notebook) to Dynalink wireless router.

I have Karmic Koala installed. Connection via ethernet is fine; just wireless refuses to show up.

Looking under System > Admin > Hardware Drivers, I see there is Broadcom STA Proprietary Wireless Driver (only).

Any advice appreciated. Otherwise it's back to XP.

Jac123.

All Broadcom users, please follow [-->this howto<--]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html") and do not hijack this thread. Your solution was just a google search away.

---

### Post by ankur1990 on 2009-12-14
> **mikewhatever said:**
> All Broadcom users, please follow [-->this howto<--]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html") and do not hijack this thread. Your solution was just a google search away.

hey thanx a lot :)
this really fixed the problem :)
thanx :)

---

### Post by ukripper on 2009-12-15
> **ankur1990 said:**
> hey thanx a lot :)
this really fixed the problem :)
thanx :)

BTW , panchkula is nice town. Better than Chandigarh IMO

---

### Post by vze326ff1 on 2009-12-19
I am have the sqme problem. I just bought a n130 samsung and I am not sure if it has a realtek or a atheros in it.  I already installed ubuntu remix and updated it. I installed ndiswrapper and installed drivers for both atheros and realtek.  realtek I get invalid driver and atheros I get hardware no persent.   But if I go the system testing  and perform network testing it saids it detects realtek semiconductor co. ltd device 8192 (rev 01)  and realtek semiconductor co. ltd rtl8101e/rtl8102e pci express fast ethernet controller (rev 2) 
 I have a wireless light on and check my BIOS and it said wireless card on all the time. I hook ethernet cable up and it connects fine and I stole my kids Belkin wifi stick and it connects fine with that    Please Help!!

---


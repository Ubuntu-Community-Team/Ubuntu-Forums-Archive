---
title: "Help needed"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Mandamus on 2010-08-30
Hi all:

I am very new to Linux Ubuntu and just sat it up on my lap top after I decided to get it of windows .
However, I have tried ubuntu previously and main problem for me is setting up drivers for my laptop.
My laptop is not a brand name (OEM ) but i can gie a little information about what it has.

I am currently having the following two issues need to be solved ASAP to do my work:

Network:
I contacted the laptop company and they said the chip set is realtek and the package driver is r8168-8.018.00.tar.bz2. However, the wired network connection is working normally but the wireless is not working (wifi) and when i checked the network it only says eth0 , i need to figure out the wireless ASAP because all my work depend on it.

VGA:
what i am sure about is that my vga is NVIDIA . I checked the driver coming the laptop and the original driver for windows says so. which NVIDIA ,  I don't know as i deleted windows frm my system and i really don't want to reinstall it only for this issue.
I tried to download NVDIA driver and googled a bit and got some information on how to install it using : sudo sh ./Nxxx .run , but it keeps telling me that i haven't NVIDIA something installed (which is absolutely incorrect because i did on windows) .

Kindly I need help on how to figure out both issues as soon as possible.
I am a newbie in ubunto and really i don't want to get frustrated and get back to windows.

thx and best regards,

---

### Post by chaanakya_chiraag on 2010-08-30
Did you go into System->Administration->Hardware Drivers?  You can have Ubuntu automagically install your NVIDIA drivers :)

---

### Post by howefield on 2010-08-30
Have you tried updating your packages and then trying Hardware Drivers ?

Open a terminal and type

```
sudo apt-get update
```

Enter your password if prompted, (you won't see it being entered).

Then go to System > Administration > Hardware Drivers.

Do you see anything listed ?

---

### Post by chaanakya_chiraag on 2010-08-30
As for your wifi issues, I would again check the Hardware Drivers application to see if you can install the driver for that as well through there, which means less headaches for you in the end.  If it still doesn't work, just post back here and we'll see what we can do.

---

### Post by chaanakya_chiraag on 2010-08-30
Same response lol

---

### Post by Mandamus on 2010-08-30
when I checked the system > Admin > Hardware drivers.
there is nothing listed in it , and I have already used sudo apt-get update to update the system and it is already up to date now.

I can not see any driver for any hardware

---

### Post by c2tarun on 2010-08-30
it is not always possible that ubuntu takes the driver automatically from hardware drivers or by updating.
if u have windows parallely running in ur system just go there and check the name of the wifi driver and post it.

---

### Post by Mandamus on 2010-08-30
I deleted Windows Today , I really don't want to go back to Install it just for this reason

---

### Post by Mandamus on 2010-08-30
I also tried to use Virtual Box and installed windows there to check my computer information. but when i put the cd for windows drivers it rejects to download the drivers for windows, maybe because it is controlled by ubunto not real windows.

---

### Post by Mandamus on 2010-08-30
here is the check result for the network using the command sudo lshw -c network


 description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4c:01:02:12
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:2000(size=256) memory:f4000000-f4000fff memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by Mandamus on 2010-08-30
anyone can help here

---

### Post by Mandamus on 2010-08-31
is it possible for any one to reply to me. I really searched the forum but none of the ways mentioned was ok.

---


---
title: "Wireless WG311v3 Problem"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by leadarc on 2011-01-28
Hello, I am new to the forums and recently I decided to upgrade my desktop to Ubuntu 10.04 LTS 64 bit edition (Seeing I have over 4 gigs of ram). I installed the OS with little to no trouble and also got all my needed drivers. My problem is though I cannot seem to get the wireless working, I have googled and searched but I have not found the answer I seek.
Basicly I have fully installed ndiswrapper and the windows driver for my wireless card.
I have tried as much as I can to get it to detect a wireless signal. I took the liberty of typing iwconfig and got this message.
> 
user@user-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.After looking around I found another cammand, lshw -c network. I got the following message:

> 
user@user-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:7d:a4:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=XXX.XXX.XXX.XX latency=0 multicast=yes
       resources: irq:27 ioport:d800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8fe0000-f8feffff(prefetchable) memory:feae0000-feafffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=64
       resources: memory:febf0000-febfffff memory:febe0000-febeffffSo currently I have no clue on what to do, the driver is installed, and it is configured in x64 and the windows wireless drivers tab has the driver loaded and it saying it is detected.
My idea is its thinking that this wireless driver is an ethernet modem, so please if anyone could help fell free to answer.

---

### Post by plucky on 2011-01-28
> *-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:04:00.0
version: 03
[color=red]width: 32 bits[/color]
clock: 66MHz
capabilities: cap_list
configuration: latency=64
resources: memory:febf0000-febfffff memory:febe0000-febeffff 

Just a thought

As the wireless interface is 32-bit,have you installed the libraries to allow 32-bit software to run on a 64-bit system?

I believe what you need to install is **32-bit compatibility libraries (ia32-libs)**

Open Synaptic Package Manager and search for 1a32-libs and install.

Good Luck

---

### Post by leadarc on 2011-01-28
I got ia32 installed but when i try to install/reinstall drivers now i get a message saying WARNING: All config files need .conf /etc/modprobe.d/ndiswrapper, it will be ignored in a future release

---


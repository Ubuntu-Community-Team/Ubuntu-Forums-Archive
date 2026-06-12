---
title: "Cant connect"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by Big4wheeler on 2008-08-01
Hello guys! I recently finally installed Ubuntu along side Vista, so im dual booting. I would love to make a full transition over to Ubuntu, but my wireless card is not working, I tryed following MANY tutorials. (I dont even see the network to connect to, I also made it un-encrypted, and it still did not work) All though none worked, on my restricted drivers, I see the HAL thing, and the Atheros 802.11b/g driver. I can get you any specs you want, just ask!

> chris@chris-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: RTL8101E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 01
serial: 00:1d:60:e0:f5:2f
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR5413 802.11abg NIC
vendor: Atheros Communications Inc.
physical id: 4
bus info: pci@0000:01:04.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=96 maxlatency=28 mingnt=10

Thanks for any help

---

### Post by Big4wheeler on 2008-08-05
Bump.

---

### Post by wessie on 2008-08-05
Hey Big4Wheeler,

Please run the lsusb command in a terminal and post the output.

---

### Post by Big4wheeler on 2008-08-07
> **wessie said:**
> Hey Big4Wheeler,

Please run the lsusb command in a terminal and post the output.

Here you go:

```

chris@chris-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
chris@chris-desktop:~$ 

```

---

### Post by Big4wheeler on 2008-08-08
24 hour bump.

---

### Post by Iowan on 2008-08-08
Post results of **iwconfig** and contents of **/etc/network/interfaces.**

---

### Post by Big4wheeler on 2008-08-08
iwconfig:

```
chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chris@chris-desktop:~$
```

/etc/network/interfaces.:

```
 
auto lo
iface lo inet loopback

```

---

### Post by Big4wheeler on 2008-08-09
Bump

---

### Post by Iowan on 2008-08-09
A quick search for "AR5413" yielded [these]("http://ubuntuforums.org/search.php?searchid=45977160") results.  I haven't researched them yet.

---

### Post by Big4wheeler on 2008-08-09
I clicked the link, and it says nothing was found.

---

### Post by Big4wheeler on 2008-08-10
Bump.

---

### Post by Iowan on 2008-08-11
Oops, doesn't work for me now, either... Anyway, try the [Search ]("http://ubuntuforums.org/search.php") Option, enter "AR5413" as keyword. A Tag Search (under Search pulldown) for "Atheros" might yield some useful results, too.

---

### Post by Big4wheeler on 2008-08-11
I pulled the card out today, discovered that it is a Liteon WN5301A. I searched that and found some people using NDISwrapper, hoew exactly would I intall that?

---

### Post by Big4wheeler on 2008-08-11
Found a guide for NDISwrapper. I got it working! Very simple

If anyone in the feature needs help, feel free to PM me!

I know how frustrating it can be.

---

### Post by RoyHobbs on 2008-08-21
> **Big4wheeler said:**
> Found a guide for NDISwrapper. I got it working! Very simple

If anyone in the feature needs help, feel free to PM me!

I know how frustrating it can be.

Hi, can you send me a link for the guide?  I think I am having the same problem as you, so anything would help:)  I have no internet access on the PC I am installing ubuntu on otherwise I would pm you.  Thanks

---

### Post by Iowan on 2008-08-21
> **RoyHobbs said:**
> Hi, can you send me a link for the guide?  Better yet, post it here...

---

### Post by Big4wheeler on 2008-08-26
This is fairly simple to do, download the drivers you need that are for windows. You can just google your model and you should be able to find them. Now you need to install NDISwrapper, I moved my computer to the router for easy installation, but if you cant do that, theres a work around. 

> #

Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).
#

Open ndisgtk (System &#8594; Administration &#8594; Windows Wireless Drivers).


Thats only if you have internet connection, I don't have time to find a guide on how to install it offline. You can try searching, or wait for me to find a guide.

---


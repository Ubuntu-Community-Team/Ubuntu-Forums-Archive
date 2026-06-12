---
title: "SuperOS - Linksys Issue"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by mikefullersg on 2009-05-02
I'm an EXTREME beginner to Linux in general; just got off the Microsoft boat. Loving Ubuntu. Here's the problem.
 
I recently put together a PC- dual booting XP and SuperOS. In the shop, I tried connecting to the internet. XP did just fine, but Ubuntu failed. It recognized the NIC, but couldn't seem to do anything with it (ie Connect ^_^). I tried a different NIC, and that one didn't work either.
 
I brought the PC home, and threw in a Linksys Wireless-G PCI adapter. Once again, XP is able to connect. Ubuntu doesn't even seem to recognize the hardware. How do I get my SuperOS connected? I'm assuming it's a driver issue.
 
NOTE: I JUST started with Linux. Though Ubuntu seems to be the most accessible, I still don't know jack about it. I'm trying to get better. Bottom line is, please reply in layman's terms. I don't know any Linux command line yet, or even how to go about doing simple things like driver installation. So please have patience, here.
Thanks!
 
>>>>>Mike

---

### Post by cariboo on 2009-05-02
IF you nic was detected, then it isn't a driver issue. Could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

you will be asked to enter your password, it will not echo anything back when you do. The above command will print out all the details of the network adapters you have installed in your system and create a text file that you can easily copy to your ntfs partition. Please paste the results in your next post.

---

### Post by mikefullersg on 2009-05-03
Okay, man. I ran the code. Here's what I got. I notice a pretty ugly "disabled" next to the Wireless Network Controller thing. So how do I negotiate this situation? (And by the way, thanks a lot for the simplicity of your response.

```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:c0:96:17:f9
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:04:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:7e:06:02:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:5e:f4:51:6f:27
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

>>>>>Mike

---

### Post by cariboo on 2009-05-05
Did you check System-->Administration-->Hardware Drivers to see if there was a driver listed for your wireless card?

It looks like you are most of the way there.

---

### Post by mikefullersg on 2009-05-07
Okay, no driver is present next to the Hardware Drivers section, nor in the System > Administration > Wireless Network Drivers section.
 
Sooo you're gonna tell me to pull up a Linksys driver in XP, swap it to my Linux partition, and install it, I presume. If there's anything troublesome about installing a driver in Ubuntu, please walk me through it.
 
Remember- I been a Windows user all my life.
Thanks,
>>>>>Mike

---

### Post by verakennedymiller on 2010-02-03
I Hope you got the correct answer newbie, unfortunately i cannot help you. I AM ALSO A DETERMINED NEW USER AND I HAVE A VIRTUAL BOX FOR WINDOWS XP ON MY UBUNTU, WILL I HAVE PROBLEMS WHEN I DOWNLOAD UBUNTU,BURN IT TO A CD AND REBOOT TO INSTALL? DO I COPY WINDOWS XP VIRTUAL BOX OR DO I JUST REINSTALL IN IT AGAIN? ALSO WHERE DO I GO TO SEE MY REPLY (for example,your reply to this thread). I've been registered for a month and i can never find my response to the QUESTIONS i ask on the FORUM.     



Thanks itttech50

---

### Post by HappyFeet on 2010-02-03
> **verakennedymiller said:**
> I've been registered for a month and i can never find my response to the QUESTIONS i ask on the FORUM.     



Thanks itttech50

You will see your username in the upper right corner of the web page. Click on it. It will open up your profile page. On the upper right hand side of that page you will see **Show All Statistics**. Click that and on the left you will see **Find all posts by itttech50**. Just click that. Then you can find all your posts, and go directly to that thread/post.

I suggest starting a new thread for anything you need help with. Do not hijack another person's thread.

---


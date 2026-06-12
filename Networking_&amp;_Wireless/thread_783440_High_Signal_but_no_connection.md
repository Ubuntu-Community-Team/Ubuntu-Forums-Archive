---
title: "High Signal but no connection"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by zorba_the_greek on 2008-05-05
Hello!
I have an Dell XPS M1330 Laptop and I use Ubuntu 8.04, freeBSD 7.0 and Windows XP Professional. I have a problem with my wireless connection. I use the latest drivers of my wifi network card, but I cannot connect if I am not exectly next to the router, even if I have high signal. Many times the signal is more than 73% and I can't connect, or if I connect but I can't use firefox or emesene, or everything is extremely slow. On the other hand if I use XP, I have a quick connection while I am in exactly the same place.:-(
So, in order to fix this, I just bought a LevelOne Wireless USB. More specificly it is the LEVEL ONE WNC-0305USB 11G WIRELESS USB ADAPTER. Unfortunatelly, I have higher signal, like 85%, but even now I can't connect when I use Ubuntu, or even if I finally connect, I can't use anything like before. ](*,)
What's the deal, why I can even download thinks in high speed when I use Windows XP and I can't even use Firefox when I use Ubuntu??
If I find a solution to that, I'm going to erase Windows and use only Ubuntu and freeBSD.

PS: Sorry about my poor English, as you see I am a Greek..:oops:

edit: I forgot to mention that I used Gutsy before Hardy, facing the same problem, and I were using Kubuntu for a period in the past, but again the same problem existed..

---

### Post by Ayuthia on 2008-05-05
> **zorba_the_greek said:**
> Hello!
I have an Dell XPS M1330 Laptop and I use Ubuntu 8.04, freeBSD 7.0 and Windows XP Professional. I have a problem with my wireless connection. I use the latest drivers of my wifi network card, but I cannot connect if I am not exectly next to the router, even if I have high signal. Many times the signal is more than 73% and I can't connect, or if I connect but I can't use firefox or emesene, or everything is extremely slow. On the other hand if I use XP, I have a quick connection while I am in exactly the same place.:-(
So, in order to fix this, I just bought a LevelOne Wireless USB. More specificly it is the LEVEL ONE WNC-0305USB 11G WIRELESS USB ADAPTER. Unfortunatelly, I have higher signal, like 85%, but even now I can't connect when I use Ubuntu, or even if I finally connect, I can't use anything like before. ](*,)
What's the deal, why I can even download thinks in high speed when I use Windows XP and I can't even use Firefox when I use Ubuntu??
If I find a solution to that, I'm going to erase Windows and use only Ubuntu and freeBSD.

PS: Sorry about my poor English, as you see I am a Greek..:oops:

edit: I forgot to mention that I used Gutsy before Hardy, facing the same problem, and I were using Kubuntu for a period in the past, but again the same problem existed..

Don't apologize for your English!  I can't respond back in Greek! :)
Have you tried changing the channel in your router?  There might be some other wireless signal that is causing interference.

---

### Post by zorba_the_greek on 2008-05-06
> **Ayuthia said:**
> Don't apologize for your English!  I can't respond back in Greek! :)
Have you tried changing the channel in your router?  There might be some other wireless signal that is causing interference.

Well, I have exactly the same problem with the wireless connection in my University department and a friend's router in his house. If am not exactly next to his router, I can't connect even if I have 80%, or even if I finally connect, it is EXTREMELY slow and most of the times I can't use emesene or kopete or amsn. :confused::confused:

---

### Post by tagigr on 2008-05-06
zorba i have the same problem and have also 1 pc with level1 wireless card and a laptop using windows xp.Did u fix it ur problem?:popcorn:havent found any way to fix it

---

### Post by zorba_the_greek on 2008-05-06
> **tagigr said:**
> zorba i have the same problem and have also 1 pc with level1 wireless card and a laptop using windows xp.Did u fix it ur problem?:popcorn:havent found any way to fix it

Unfortunatelly no.. As you see I created this thread yesterday... :( :(

---

### Post by ethanay on 2008-05-06
have you enabled the backports repository to upgrade the intel wireless drivers (3945/4945)?  at least the led will indicate when the wireless card is active.

that helped improve my wireless, tho still working out issues after resume from hibernate/suspend, and it doesn't seem to be scanning for new networks unless i restart network and force scan via commandline.

---

### Post by zorba_the_greek on 2008-05-06
> **ethanay said:**
> have you enabled the backports repository to upgrade the intel wireless drivers (3945/4945)?  at least the led will indicate when the wireless card is active.

that helped improve my wireless, tho still working out issues after resume from hibernate/suspend, and it doesn't seem to be scanning for new networks unless i restart network and force scan via commandline.

I do not have an Interl wireless network card. When I bought my laptop I could choose between two Broadcom and an Intel, but the Intel was a lot more expensive, so I bought one of the two Broadcom. So, now I have installed [the latest b43 driver]("http://linuxwireless.org/en/users/Drivers/b43"). The strange thing is that even if my wifi network card didn't even work, why I have exactly the same problem when I use my LevelOne Wireless USB Adapter??? :confused: :confused:

---

### Post by Ayuthia on 2008-05-06
Do you have a wired connection?  If so, can you post the results of the following from the Terminal:
```
lsusb
lspci -nnd 14e4:*
lshw -C network
```

For the lshw command, I just want to see the driver that is being used for your wireless devices.

---

### Post by zorba_the_greek on 2008-05-06
> **Ayuthia said:**
> Do you have a wired connection?  If so, can you post the results of the following from the Terminal:
```
lsusb
lspci -nnd 14e4:*
lshw -C network
```

For the lshw command, I just want to see the driver that is being used for your wireless devices.

Ok, I use now my Laptop and I am connected with my wireless connection and not the ethernet. The results are these:

lsusb
```
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp.
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp.
Bus 001 Device 004: ID 413c:8126 Dell Computer Corp.
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp.
Bus 001 Device 001: ID 0000:0000

```

lspci -nnd 14e4:*
```
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

```

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:3d:88:2c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:3a:07:75:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.4 multicast=yes wireless=IEEE 802.11g

```

---

### Post by Ayuthia on 2008-05-06
Ok, from what I understand, your Broadcom wireless card works, but is slow.  However, you are not able to connect with your new USB wireless device.

When you did the lshw -C network, was your USB wireless device plugged in?  If not, can you plug it in and see what it displays?

---

### Post by zorba_the_greek on 2008-05-07
> **Ayuthia said:**
> Ok, from what I understand, your Broadcom wireless card works, but is slow.  However, you are not able to connect with your new USB wireless device.

When you did the lshw -C network, was your USB wireless device plugged in?  If not, can you plug it in and see what it displays?

How did you understand that it is slow??? Can I fix it??

My USB wasn't plugged in, I'm gonna do that in the afternoon because I have to go now...
Thanks!!! :)

---

### Post by Ayuthia on 2008-05-07
> **zorba_the_greek said:**
> How did you understand that it is slow??? Can I fix it??

My USB wasn't plugged in, I'm gonna do that in the afternoon because I have to go now...
Thanks!!! :)
From reading your first post, you said that it is sometimes extremely slow.  You might try NDISwrapper with your Broadcom card and see if it is any better.

---

### Post by zorba_the_greek on 2008-05-07
> **Ayuthia said:**
> From reading your first post, you said that it is sometimes extremely slow.  You might try NDISwrapper with your Broadcom card and see if it is any better.

I am completely n00b with NDISwrapper, but I'm gonna try it if I don't find it very hard.
I'm still at University. When I return home I'm going to give you the results of the USB Wireless Adapter..
Thanks!!:D

---

### Post by zorba_the_greek on 2008-05-07
I returned home and I now use the commands you told me, but I am connected now with my USB Wireless Adapter. The results:

lsusb
```
Bus 007 Device 004: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp.
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp.
Bus 001 Device 004: ID 413c:8126 Dell Computer Corp.
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp.
Bus 001 Device 001: ID 0000:0000

```

lspci -nnd 14e4:*
```
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

```

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:3d:88:2c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:3a:07:75:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:11:6b:16:0a:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 802.11g

```


The strange thing is that today my wireless card works better than my USB Adapter. It's got 93%, whereas the USB Adapter has 85%, and in addition to this, my wireless card can now see other networks from the neighbour that couldn't see in the past, and that my USB Adapter can't see even now... :lolflag:
I don't understand what's going on??
Could one of this command you told me helped to improve the signal?? (I tried the last one with a "sudo", too, once...)

---

### Post by Ayuthia on 2008-05-07
Bus 007 Device 004: ID 0bda:8187 Realtek Semiconductor Corp.
This is your wireless.  You might try:
```
sudo modprobe rtl8187
```
I am not very familiar with Realtek.  It looks like there are a few options to get them to work.  There is a serialmonkey approach and NDISwrapper also.

As for the improvement in your wireless, I don't have an answer for you.  The commands that I ask from you do not make any changes.  They just gather information.

---

### Post by Kevbert on 2008-05-07
If you get a strong signal but have trouble connecting it may be due to interference from other wireless networks on the same channel number (most wireless networks run on their default channel 01) or from other devices running at the same frequency (around 2.4GHz).  These items include cordless (DECT) phones, microwave ovens and even wireless keyboards.
To change the channel number you have to open a browser to access the router/modem.  If you can connect to the router modem via a cable connection this is best.  Now you need to enter the router DNS address which will be something like [http://192.168.0.1](http://192.168.0.1)  A box will now open asking for a user name and password (defaults are normally admin and password).  A new window will open and you need to look for wireless settings.  Under wireless settings you should be able to change the channel number say to Ch 05 (as well as your passkey if you want to change this).  These settings should all be in your user manual for the router/modem.
The other thing you should do is change the password that you entered to get into the wireless settings in the first place, for security reasons, as anyone who can see your wireless network can remotely access your wireless settings.

---

### Post by zorba_the_greek on 2008-05-07
> **Ayuthia said:**
> Bus 007 Device 004: ID 0bda:8187 Realtek Semiconductor Corp.
This is your wireless.  You might try:
```
sudo modprobe rtl8187
```
I am not very familiar with Realtek.  It looks like there are a few options to get them to work.  There is a serialmonkey approach and NDISwrapper also.

As for the improvement in your wireless, I don't have an answer for you.  The commands that I ask from you do not make any changes.  They just gather information.


What will this command do?? I haven't used before modprobe, but I know that it has to do with the kernel, so I am scared to use it every time I see it... :oops: :oops:


> **Kevbert said:**
> If you get a strong signal but have trouble connecting it may be due to interference from other wireless networks on the same channel number (most wireless networks run on their default channel 01) or from other devices running at the same frequency (around 2.4GHz).  These items include cordless (DECT) phones, microwave ovens and even wireless keyboards.
To change the channel number you have to open a browser to access the router/modem.  If you can connect to the router modem via a cable connection this is best.  Now you need to enter the router DNS address which will be something like [http://192.168.0.1](http://192.168.0.1)  A box will now open asking for a user name and password (defaults are normally admin and password).  A new window will open and you need to look for wireless settings.  Under wireless settings you should be able to change the channel number say to Ch 05 (as well as your passkey if you want to change this).  These settings should all be in your user manual for the router/modem.
The other thing you should do is change the password that you entered to get into the wireless settings in the first place, for security reasons, as anyone who can see your wireless network can remotely access your wireless settings.

I am usually connected either to my University's Wifi, in which I can't do anything, or to my home's Wifi, where I use the option "Allow access by: Trusted Wireless stations only", which means that only my laptop and my USB Wireless Adapter can connect to it... ;)


Thank you both!!! :smile: :smile:

---

### Post by Ayuthia on 2008-05-07
> **zorba_the_greek said:**
> What will this command do?? I haven't used before modprobe, but I know that it has to do with the kernel, so I am scared to use it every time I see it...
It will load the rtl8187 module into the system.  The nice thing about modprobe is that it only loads modules just for this session.  If something goes wrong, you can unload the module by sudo modprobe -r rtl8187.  Unless the system locks up where you will need to reboot and it will be gone.

EDIT:
You might also want to look at this:[http://ubuntuforums.org/showthread.php?t=768446](http://ubuntuforums.org/showthread.php?t=768446)
It is a post for someone with an RTL8187.

---

### Post by Kevbert on 2008-05-07
In the case of "Allow access by: Trusted Wireless stations only" have you entered the IP addresses of your laptop and wireless adapter ?  If not, you may find that you're not as secure as you think.

---

### Post by zorba_the_greek on 2008-05-07
> **Kevbert said:**
> In the case of "Allow access by: Trusted Wireless stations only" have you entered the IP addresses of your laptop and wireless adapter ?  If not, you may find that you're not as secure as you think.

:mrgreen: :mrgreen:
Of course I have done it... And I ensure my hopes of being secure because in the beginning I haven't included both MAC addresses, so I could only access it by the one of them... :cool:

---

### Post by zorba_the_greek on 2008-05-07
> **Ayuthia said:**
> It will load the rtl8187 module into the system.  The nice thing about modprobe is that it only loads modules just for this session.  If something goes wrong, you can unload the module by sudo modprobe -r rtl8187.  Unless the system locks up where you will need to reboot and it will be gone.

EDIT:
You might also want to look at this:[http://ubuntuforums.org/showthread.php?t=768446](http://ubuntuforums.org/showthread.php?t=768446)
It is a post for someone with an RTL8187.

Thanks for your info!!!
I'm going to check this link after some time as I am stuck in an assignment in a course called something like "Database System Implementation" if I am doing correctly the translation from Greek... :oops:

---


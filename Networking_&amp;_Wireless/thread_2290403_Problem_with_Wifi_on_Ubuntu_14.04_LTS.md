---
title: "Problem with Wifi on Ubuntu 14.04 LTS"
date: 2015-08-12
forum: Networking &amp; Wireless
---

### Post by crazzyshooter on 2015-08-12
I have installed Ubuntu 14.04 LTS on my new Acer Aspire E5-573 and ubuntu is not detecting my wifi, only wired internet is working.

I have a Qualcomm Atheros Device 0042 Wifi.

```
# lshw -C net

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 2c:60:0c:88:c4:0f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:60 ioport:3000(size=256) memory:b0604000-b0604fff memory:b0600000-b0603fff
  *-network UNCLAIMED
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0400000-b05fffff
```



```
$ lspci

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 30)
```


```
$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.
```




```
$ rfkill list all

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Are there any drivers I can download to fix this issue?

Please help.

---

### Post by chili555 on 2015-08-12
Please run and post:```
lspci -nn | grep 0280
```Is this your device?```
Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
```If so, please check here:[http://askubuntu.com/questions/651341/how-to-enable-wifi-connection-in-ubuntu-14-04-lts](http://askubuntu.com/questions/651341/how-to-enable-wifi-connection-in-ubuntu-14-04-lts)> This wireless adapter is not supported by linux kernel.And this: [http://ubuntuforums.org/showthread.php?t=2281584](http://ubuntuforums.org/showthread.php?t=2281584)> Finally, until support comes along, I'd suggest an inexpensive USB wireless device. There are often threads here about working devices. I have and use a TP-Link TL-WN722N that cost all of US$12If your device is other than 168c:0042, we'll try to find a driver for you.

---

### Post by crazzyshooter on 2015-08-12
Thanks for replying chili555.

Yes you are right. I have this wifi device.

```
Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
```

I bought a new laptop just for linux. This is my first laptop and i have never expected that i would face this wireless problem. :(

I  tried **ndiswrapper** and i tried to load windows drivers from driver disk  which came with a laptop but there is no **.inf** file(s). I can't even find windows 7/XP drivers for my laptop, only windows8/8.1/10 drivers are  available. 

Now there is only one way to get wifi working on linux is to buy usb adapter.

Is this the USB wireless device i should buy?

```
http://www.flipkart.com/tp-link-150mbps-high-gain-wireless-usb-adapter/p/itmdzusgbtfhhadq
```

---

### Post by jeremy31 on 2015-08-12
That appears to be the same USB adapter that I have as a backup and it works in the Ubuntu versions I have tried it with

---

### Post by chili555 on 2015-08-12
I have it and use it, too. There are many supported devices and there are many threads here and on askubuntu about them. This one is just one example that is verified by jeremy31 and me.

I am sure there will be support for your Atheros but when is the question. I have no idea if it will be 30 days or 3 years or something in between.

---

### Post by crazzyshooter on 2015-08-12
> **jeremy31 said:**
> That appears to be the same USB adapter that I have as a backup and it works in the Ubuntu versions I have tried it with

> **chili555 said:**
> I have it and use it, too. There are many supported devices and there are many threads here and on askubuntu about them. This one is just one example that is verified by jeremy31 and me.

I am sure there will be support for your Atheros but when is the question. I have no idea if it will be 30 days or 3 years or something in between.

Thank you guys for the support. I will buy third party wireless adapter to fix this wireless problem. I have already sent a bug report, lets hope for the best.

Cheers! :p

---

### Post by weatherman2 on 2015-08-13
FYI, it's possible - and sometimes easy - to upgrade the internal wireless card.  I have done it on most of my laptops that I have owned or worked on for family and friends.  The internal wireless card is in a little slot, probably secured with a screw and has only two (or sometimes three) antenna wires clipped on to it.  It may be almost as easy as upgrading your RAM - sometimes right under the bottom panel.  Only Lenovo and HP users are restricted (by the BIOS) from upgrading an internal wireless card in my experience.

There are lots of videos on YouTube showing you how to change an internal wireless card in a laptop.  The only trick is finding out exactly where yours is on the laptop.

---

### Post by weatherman2 on 2015-08-13
I have had great luck with the Intel 6235 card myself - (802.11n dual band + bluetooth) - that's what I put in to my Acer netbook.  They can be had on eBay used for under $15 USD sometimes.  Get a version NOT for Lenovo/HP and perhaps not for Asus or Samsung...but the version for Acer, Dell, Toshiba (or generic) should work.  If you want/need 802.11ac with an AC router, you might try the Intel 7260 card.  I bought one and have only played with it briefly, but it seemed to work fine in my Ubuntu 14.04 box.

---

### Post by QDR06VV9 on 2015-08-13
<snip>by poster
Regards

---

### Post by chili555 on 2015-08-13
> **runrickus said:**
> See if this gets your WiFi up.
 	Code:


```
[COLOR=#000000]sudo add-apt-repository ppa:longsleep/bcmwl
sudo apt-get update
sudo apt-get install bcmwl-kernel-source[/COLOR]
```
RegardsDo you actually think a Broadcom driver will do anything to help his Atheros wireless?

I am quite sure it will not.

---

### Post by QDR06VV9 on 2015-08-13
> **chili555 said:**
> Do you actually think a Broadcom driver will do anything to help his Atheros wireless?

I am quite sure it will not.
Oopps Need to put my glasses on. #-o
Thanks chili555

---

### Post by crazzyshooter on 2015-08-14
> **weatherman2 said:**
> FYI, it's possible - and sometimes easy - to upgrade the internal wireless card.  I have done it on most of my laptops that I have owned or worked on for family and friends.  The internal wireless card is in a little slot, probably secured with a screw and has only two (or sometimes three) antenna wires clipped on to it.  It may be almost as easy as upgrading your RAM - sometimes right under the bottom panel.  Only Lenovo and HP users are restricted (by the BIOS) from upgrading an internal wireless card in my experience.

There are lots of videos on YouTube showing you how to change an internal wireless card in a laptop.  The only trick is finding out exactly where yours is on the laptop.

> **weatherman2 said:**
> I have had great luck with the Intel 6235 card myself - (802.11n dual band + bluetooth) - that's what I put in to my Acer netbook.  They can be had on eBay used for under $15 USD sometimes.  Get a version NOT for Lenovo/HP and perhaps not for Asus or Samsung...but the version for Acer, Dell, Toshiba (or generic) should work.  If you want/need 802.11ac with an AC router, you might try the Intel 7260 card.  I bought one and have only played with it briefly, but it seemed to work fine in my Ubuntu 14.04 box.


Hi weatherman2,

This is my new laptop which i purchased like 20days ago and it came with a 3year warranty. There are 2-3 acer seal on the back, if i try to open then warranty will void. :(

This is the only problem otherwise i was thinking of going your way. :)

Portable USB wireless adapter is the only best choice.

I have already reported this wifi bug here.: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1484159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1484159)

Lets hope this wifi bug will be fixed in near future.

Thanks!

---

### Post by fnoz123-foo on 2015-09-27
Did this driver issue every get resolved?  Apparently there is a 'Linpus' Linux distro for this laptop supported by Acer in India - so I assume there is a driver for this in that distro.

---

### Post by jeremy31 on 2015-09-27
> **fnoz123-foo said:**
> Did this driver issue every get resolved?  Apparently there is a 'Linpus' Linux distro for this laptop supported by Acer in India - so I assume there is a driver for this in that distro.

Does your ```
lscpi -nnk | grep -iA2 net
``` Show the same device?

---

### Post by fnoz123-foo on 2015-09-27
> **jeremy31 said:**
> Does your ```
lscpi -nnk | grep -iA2 net
``` Show the same device?

You mean lspci - right? :)

I am on 15.04

Here is the output:

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:0987]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Foxconn International, Inc. Device [105b:e09a]

---

### Post by jeremy31 on 2015-09-27
I searched the mailing list the ath10k developers use and found only [http://ath10k.infradead.narkive.com/DsHmjblK/support-for-qca9377](http://ath10k.infradead.narkive.com/DsHmjblK/support-for-qca9377) concerning this wifi chipset.  It will need modification of the source code and a couple firmware files extracted from windows drivers

---

### Post by fnoz123-foo on 2015-09-27
Thanks - are you sure this is the same chipset?  QCA9377?

---

### Post by jeremy31 on 2015-09-27
QCA9377 showed up in a couple searches I did on the device ID 168c:0042, right now I doubt there is any way to get it working in any Linux Distro.  This was a post from a few months ago [http://ubuntuforums.org/showthread.php?t=2281584](http://ubuntuforums.org/showthread.php?t=2281584)

If your acer doesn't have a BIOS with a whitelist(search google for your model number and whitelist) you could replace the wifi card with an Intel 7260 or just buy a USB wifi like the TP-Link WN722N 150Mbps that works soon after it is plugged in

---

### Post by fnoz123-foo on 2015-09-27
I have a wn823n on order It is supposed to be linux compatible

---

### Post by jeremy31 on 2015-09-27
You might need to install from pvaret's github site if you have any issues
[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) 

Pilot6 might have a deb on his PPA

---

### Post by fnoz123-foo on 2015-09-27
Thanks - the 8192cu just dropped through the door (7.45pm on a Sunday - and ordered on Saturday - gotta love Amazon Prime!)  appears to be working fine now, albeit a very poor signal due to the router being at the other end of the house and the minute size of the antenna on this USB Wifi dongle.  Nothing that can't be solved though :)

Spoke too soon - the stock driver was very flaky.  I downloaded and compiled pvaret's driver - it seems better now.

---

### Post by fnoz123-foo on 2015-11-09
I'm sure you've all seen this - but it is working now.

I used these steps:

[http://ubuntuforums.org/showthread.php?t=2300861&page=3&p=13386625#post13386625](http://ubuntuforums.org/showthread.php?t=2300861&page=3&p=13386625#post13386625)

---


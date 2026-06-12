---
title: "feisty beta, wireless card stops working"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by swimmer618 on 2007-04-12
My linksys PCMCIA card, which worked without a problem in Edgy, is no longer found in Feisty Beta. The model number is WPC11v4 (a kind of old wireless B card).

The card does not appear at all in the System>Administration>Networking window.

I just switched from Windows a few weeks ago, so I don't know a lot about drivers and hardware for linux, but I couldn't find it listed in the device manager either.

Thanks in advance for any help. :D

---

### Post by caffienefree on 2007-04-12
Please post the output of:

sudo lshw -C network

---

### Post by swimmer618 on 2007-04-12
*-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:eb:8f:c1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:fcffe000-fcffffff irq:7
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@03:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: iomemory:f8000000-f80001ff irq:11

---

### Post by caffienefree on 2007-04-12
Please execute this command, and post the result.

/sbin/lsmod | grep -i rtl8180

---

### Post by king_arthur on 2007-04-12
Same problem here.

Installing Feisty beta has disabled the WiFi card.

dmesg doesn't show any trace of loading the rtl modules neither does  /sbin/lsmod | grep -i rtl8180

What happened? :(

/P

---

### Post by swimmer618 on 2007-04-12
I tried /sbin/lsmod | grep -i rtl8180, but it didn't print anything.

I did, however, borrow a wireless card from another computer, and that one works (Gigabyte USB Wireless G)

---

### Post by zach12 on 2007-04-12
linksys wireless cards do not like ubuntu
i use for my laptop (dell inspiron 8000)  asua card
it worked very well

---

### Post by swimmer618 on 2007-04-15
can anyone help me with this, or would it be better to just wait for the final Feisty release?

---

### Post by king_arthur on 2007-04-15
The problem with rtl seems to be a buggy module that has been blacklisted and therefore doesn't load.
See [https://launchpad.net/ubuntu/+source/module-init-tools/+bug/88430](https://launchpad.net/ubuntu/+source/module-init-tools/+bug/88430)
and [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)
However I enabled the driver and it works like a charm (on my hardware) with the suggested hack on ESSID.

No point waiting for final release of Feisty as this bug is on a fairly low priority and not Feisty related.

/P

---

### Post by swimmer618 on 2007-04-15
Sry, I'm really new to Ubuntu. How can I enable this driver?

---

### Post by king_arthur on 2007-04-15
> **swimmer618 said:**
> Sry, I'm really new to Ubuntu. How can I enable this driver?
Hum, you are now venturing in treacherous waters :)

To enable the module, try first **sudo modprobe r818x** (that will load the module) and see how you go.

To make this permanent you have to edit /etc/modprobe.d/blacklist.

Mind you that if a module is blacklisted there might be some good reasons.

You have been warned. ;)

/P

---

### Post by swimmer618 on 2007-04-15
Thanks for your help...
The wireless card appears now in the System>Administration>Network window, and I've configured it for my network. Wifi radar can even use it to scan for networks, but it still won't connect.

---

### Post by alvaro.ballesteros2 on 2007-04-15
I have the same problem that you.  My ADMtek wifi card installed on a Thinkpad 40 was working well on Edgy 6.10 (after 1 month trying to configure it using ndiswrapper and wifi-radar).  Today I have upgraded Edgy 6.10 to Feisty 7.04.  Result:  I have not wireless connection.  In Edgy, even with the Live CD the link light on the card was green, with Feisty 7.04 the light remains yellow.

running 
sudo lshw -C network

I get the following display:
 *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:2e:29:72
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.65 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:c0200000-c0200fff ioport:8000-803f irq:11
  *-network
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 1
       bus info: pci@03:00.0
       logical name: wmaster0
       version: 11
       serial: 00:06:f4:04:ae:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=adm8211 latency=64 maxlatency=128 mingnt=64 multicast=yes wireless=IEEE 802.11b
       resources: ioport:4000-40ff iomemory:c4000000-c40003ff irq:11

I ran also:
/sbin/lsmod | grep -i rtl8180

but didn't get any text

Is it possible to run this card running with Feisty 7.04, is so, what do you suggest me to do?  Or get a new card (as this is very old).

Regards
Alvaro

---

### Post by SDE on 2007-04-16
may be pretty stupid, but i installed feisty server since my laptop didn't like the desktop cd.  my wireless didn't work because it was booting the -server kernel which was listed 1st by default.  when i booted -generic, it worked fine.

probably more of a special situation for me .. but if anyone else does have that problem, you can edit /boot/grub/menu.lst and move the generic options above the server so it will boot it by default.

---

### Post by king_arthur on 2007-04-16
> **swimmer618 said:**
> Thanks for your help...
The wireless card appears now in the System>Administration>Network window, and I've configured it for my network. Wifi radar can even use it to scan for networks, but it still won't connect.

OK so the card is working but you can't connect.
Can you see any available networks?

If that is the case, you must set up the properties, in particular ESSID with the proper settings (and workaround)

/P

---

### Post by king_arthur on 2007-04-16
> **alvaro.ballesteros2 said:**
> 
/sbin/lsmod | grep -i rtl8180

but didn't get any text

Is it possible to run this card running with Feisty 7.04, is so, what do you suggest me to do?  Or get a new card (as this is very old).

Regards
Alvaro

You are checking if a realtek module has been loaded whereas your card uses a different chip. :)

You may find some useful info here: [http://www.latinsud.com/adm8211/](http://www.latinsud.com/adm8211/)

However, your card appears to be detected according to the log posted.
Try **iwconfig** to check connection.

If the card is working it's the properties (setup) you must focus on now.

/P

---

### Post by swimmer618 on 2007-04-16
I figured it out!!

just in case someone else has the same problem:
I put in the correct essid, but when I ran 'iwconfig', the last letter from the essid was missing (I was supposed to be connected to 'wireless', but it said I was connected to "wireles". To fix it, I entered the essid as "wireless1", and iwconfig came back as "wireless", and it worked!

thanks for your help, King Arthur

---

### Post by king_arthur on 2007-04-16
> **swimmer618 said:**
> I figured it out!!

just in case someone else has the same problem:
I put in the correct essid, but when I ran 'iwconfig', the last letter from the essid was missing (I was supposed to be connected to 'wireless', but it said I was connected to "wireles". To fix it, I entered the essid as "wireless1", and iwconfig came back as "wireless", and it worked!

thanks for your help, King Arthur
You are welcome swimmer! 
Please note that this workaround was mentioned in the links previously posted .;)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)

In any case, well done!

/P

---

### Post by DoctorMO on 2007-08-09
anyone suffering from missing essid chars can follow this link [http://ubuntuforums.org/showthread.php?p=3159934](http://ubuntuforums.org/showthread.php?p=3159934) maybe it will help you so you don't have to use the work around... although it will break other cards so be careful.

---


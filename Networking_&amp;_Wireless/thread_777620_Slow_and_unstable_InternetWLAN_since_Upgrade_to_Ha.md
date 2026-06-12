---
title: "Slow and unstable Internet/WLAN since Upgrade to Hardy"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by don_emilio_juan on 2008-05-01
Hi,

I ve been upgrading to Hardy two days ago and cannot get my WLAN/internet connection to work properly. While my XP PC is running with a download-rate of 1.3 MB my Hardy Laptop reaches its max with 30 KByte. I had no problems with feisty and also my WLAN Card (Asus WL 107g /PCMCIA) worked out of the box with 7.04. But with Hardy it s not only very slow it also looses connection very often.

My wireless network is encryptet with WPA2 Personal and I made no changes to the network since my upgrade.

In another thread with WLAN problems I read the following information might help to solve the problem (although I have no idea what to do with the info...):

lspci gives me:
```
juan@juan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
03:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```

"ifconfig -a" tells us:
```
juan@juan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  Hardware Adresse 00:02:3f:91:68:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Basisadresse:0x3000 

eth0:avahi Link encap:Ethernet  Hardware Adresse 00:02:3f:91:68:1a  
          inet Adresse:169.254.4.86  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          Interrupt:17 Basisadresse:0x3000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2431 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:122444 (119.5 KB)  TX bytes:122444 (119.5 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:0e:a6:a6:20:5f  
          inet Adresse:192.168.0.137  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::20e:a6ff:fea6:205f/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:28310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20952 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:37307727 (35.5 MB)  TX bytes:2520899 (2.4 MB)

wmaster0  Link encap:UNSPEC  Hardware Adresse 00-0E-A6-A6-20-5F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And finally the content in "/etc/network/interfaces" is: 
```
auto lo
iface lo inet loopback

```

Hopefully someone can help me.
Thanks in advance
Juan

---

### Post by nbitting on 2008-05-01
I'm having this same issue...yesterday I was installing nmap and my dl rate was 300 Bytes/s...What's up with that?  In XP, I'm rate is like 700KB/s at the least.

---

### Post by don_emilio_juan on 2008-05-01
I ve now been looking for a solution for more san 4 hours and it seems that there is a massive bunch of people who has similar problems or problems with internet connection / network etc.

Unfortunately, I havent found a solution yet - I guess I need a pro now...

---

### Post by bedfordd on 2008-05-01
I'd recommend reading post [http://ubuntuforums.org/showthread.php?t=768301](http://ubuntuforums.org/showthread.php?t=768301)

---

### Post by don_emilio_juan on 2008-05-01
Thank you. The solution described there worked for me.
Anyhow this is just a workaround. I ve found out, that the problem is my WLAN card has the chipset RT2500, which creates some problems.

There is also a bug in launchpad already:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660")

There they describe the following solution:
```
SOLUTION:
1. Find out which version of a serialmonkey driver works properly with each ralink card.
2. Implement ralink serialmonkey drivers in Ubuntu.

http://rt2x00.serialmonkey.com/

Most likely the newest CVS version of each ralink driver works correctly.
```

Somehow I didnt find out how to install the serial monkey driver. Has someone done this already? Or is this the solution to be applied by the Ubuntu developer to a future Kernel?

---


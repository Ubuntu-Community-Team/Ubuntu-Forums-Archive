---
title: "eth0 is up but no networking (not even ping)"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by UeB on 2008-09-12
I posted this in ["Installation & Upgrades"]("http://ubuntuforums.org/showthread.php?t=917894") already but maybe here is a better place.
I installed Ubuntu on a new HP Pavilion dv7-1001eg yesterday but I cannot connect to the internet.

I need my ethernet to work for this. ifconfig says:

```
eth0      Link encap:Ethernet  Hardware Adresse 00:1e:ec:a4:b0:f3  
          inet Adresse:172.16.78.32  Bcast:172.16.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:3802062978 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Basisadresse:0x2000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2106 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:107644 (105.1 KB)  TX bytes:107644 (105.1 KB)
```

But I cannot even ping the gateway that is suppost to give me internet access. The gateway is definitly up because I im surfing with the pre installed vista right now.

```
moritz@skynet:~$ ping 172.16.0.1
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
From 172.16.78.32 icmp_seq=1 Destination Host Unreachable
From 172.16.78.32 icmp_seq=2 Destination Host Unreachable
From 172.16.78.32 icmp_seq=3 Destination Host Unreachable
From 172.16.78.32 icmp_seq=4 Destination Host Unreachable
From 172.16.78.32 icmp_seq=5 Destination Host Unreachable
From 172.16.78.32 icmp_seq=6 Destination Host Unreachable

--- 172.16.0.1 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6015ms
, pipe 3
```

And this is the lspci information:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
08:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```


I have no idea what I should try od do.

Thanks in advance for any help.

---

### Post by GibsonSGKing on 2008-09-12
ok, im super new to ubuntu, but this may help [http://ubuntuforums.org/showthread.php?t=715187](http://ubuntuforums.org/showthread.php?t=715187) . i think it said something about HP laptops in there, so u might wanna try it. i cant get it to work on my acer extensa, but you may have better luck. hope this helps!

---

### Post by UeB on 2008-09-12
I browesed very quickly through this thread and could not find anything about HP laptops but I read a lot about wireless networking stuff.
I need my wired network to work. I do not care for the wireless at the moment.

---

### Post by superprash2003 on 2008-09-13
did you enter this ip manually or got it via dhcp?

---

### Post by UeB on 2008-09-13
> **superprash2003 said:**
> did you enter this ip manually or got it via dhcp?

Manually

There is also alternatively a DHCP server runnig in our network but this did not work, too.

---

### Post by UeB on 2008-09-13
This is what ifconfig says after switching to DHCP in this Gnome network app:

```
moritz@skynet:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:1e:ec:a4:b0:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:2345055024 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Basisadresse:0xe000 

eth0:avahi Link encap:Ethernet  Hardware Adresse 00:1e:ec:a4:b0:f3  
          inet Adresse:169.254.11.98  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          Interrupt:218 Basisadresse:0xe000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4399 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:222200 (216.9 KB)  TX bytes:222200 (216.9 KB)

moritz@skynet:~/Desktop$ ping -c 4  172.16.0.1
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
From 169.254.11.98 icmp_seq=1 Destination Host Unreachable
From 169.254.11.98 icmp_seq=2 Destination Host Unreachable
From 169.254.11.98 icmp_seq=3 Destination Host Unreachable
From 169.254.11.98 icmp_seq=4 Destination Host Unreachable

--- 172.16.0.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3003ms
, pipe 3
```

And this after switching back to fixed ip:

```
moritz@skynet:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:1e:ec:a4:b0:f3  
          inet Adresse:172.16.78.32  Bcast:172.16.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:2746215920 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Basisadresse:0xe000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4425 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:224836 (219.5 KB)  TX bytes:224836 (219.5 KB)

moritz@skynet:~$ ping -c 4 172.16.0.1
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
From 172.16.78.32 icmp_seq=2 Destination Host Unreachable
From 172.16.78.32 icmp_seq=3 Destination Host Unreachable
From 172.16.78.32 icmp_seq=4 Destination Host Unreachable

--- 172.16.0.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3009ms
, pipe 2
```

---

### Post by UeB on 2008-09-13
damit. It is the driver looks like a lot of fun I have to go through:

[https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012)

I am ready for the sleghammer :mad:

---

### Post by fisfia on 2008-09-13
Is this for 8.04 too? In the bugreport it says 7.10???

---

### Post by UeB on 2008-09-13
yes for 8.04 , too
see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499)

or

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307)

if you search for 8168B + linux in the internet you will see that lots of people on various ditros have problems with this piece of hardware.

And now I am one of them :-(

I am really pissed because I need a working linux envoiroment for univerity. I have to hand in my graduation theses on December the 1. and all what I did so far is in typical unix apps like latex and gnuplot. The prgramming I did for the thesis was in fortran 90 and C++ alsways using the gnu compilers.
Everything was fine until last week the hard disk of my 3 years old acer laptop broke ( I could rescue my data ). Because I put already so much addition money in it ( ram was not enough, power adapter broke a year aga) I ordert a notebook instead of just buying a new hard drive and wating for the next thing to brake.

I did no reseach if my new model would work well with linux because a) no time
and b) because I thought "ah theses cheap realtek things have 70% market share and therefor alway work with linux only wireless lan might me problematic and I do not need that".

And now I am sitting here: it is 21:20 and instead of drinking a bear in the pub with friends being pround of the pages I would have written for my theses I am despeatly trying to fix this ****. If these things weren't so expansive I would just throw the hole thing out of the window.

---

### Post by UeB on 2008-09-14
Problem solved by using this instructions:

[https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012)

(I mentioned these 2 posts earlier already) 

The Problem is a r8168 ethernet device is correctly found but the r8169 driver gets loaded, a driver that cannot handle the r8168 chip.

The solution is to download an install the linux driver from realtek for the r8168 chip and blacklist the r8169 driver that does not get loaded again.
Location of realtek driver:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---


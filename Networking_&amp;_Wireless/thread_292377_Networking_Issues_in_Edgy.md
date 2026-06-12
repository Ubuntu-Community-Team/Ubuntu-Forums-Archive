---
title: "Networking Issues in Edgy"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by danbert on 2006-11-03
I recently installed a fresh copy of Edgy over my old bloated Breezy install on my laptop.

Wireless worked fine for me in the past, but after installing Edgy, I have to connect to the internet via wired.  I haven't gotten wireless to work after installing every wireless network manager there is.  The wireless managers scan the networks, but Edgy refuses to connect even though it claims it is connected and sending packets.

However, it reports that the IP for my wireless is 10.0.2.12, which is definitely not in my DHCP range.  I also lose my internet connection when I disconnect the wired cable.

I was wondering if there were any suggestions on a certain other network device that I've never seen before.  It is listed as sit0.  I was wondering if it was interfering with my wireless connection somehow.

Thanks for your help.

---

### Post by epere4 on 2006-11-04
I think I am having a similar problem. 

I updated from Dapper to Edgy and my wireless card is no longer detected as wireless.

Before the update it was detected as eth1, and now it is detected as wlan0, but not as wireless (and it does not work, obviously).

The wired connection works fine and has the same name as before: eth0

Here is what ifconfig gives me:
```
root@prewe-laptop:/home/epere4# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:89:BB:D8
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe89:bbd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16869651 (16.0 MiB)  TX bytes:2100857 (2.0 MiB)
          Interrupt:10 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21116 (20.6 KiB)  TX bytes:21116 (20.6 KiB)

```

With ifconfig -a:
```
root@prewe-laptop:/home/epere4# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:89:BB:D8
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe89:bbd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16930396 (16.1 MiB)  TX bytes:2111608 (2.0 MiB)
          Interrupt:10 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21116 (20.6 KiB)  TX bytes:21116 (20.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:f8970000-f8971000

```

Iwconfig:
```
root@prewe-laptop:/home/epere4# iwconfig
lo        no wireless extensions.

wlan0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

lspci:
```
root@prewe-laptop:/home/epere4# lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

I don't know what to do. I have searched in google and in this forum, but apparently the problems people are having with wireless networks are different (like not being able to connect using WPA or similar)

Any help will be appreciated. If need some extra info, please ask.

---

### Post by bootz on 2006-11-05
Unfortunately I cannot help you but I'm having the same problem with Edgy.

My Netgear MA111 USB 802.11b adapter is showing as a Wired connection (wlan0).  

My iwconfig output is the same as yours.

---

### Post by epere4 on 2006-11-12
I finally could solve my problem.

It was a problem of incorrect driver.

```

# Go to super user mode
epere4@prewe-laptop $ sudo -s -H
Password:

# I found out that I have a prism2_pci driver:
root@prewe-laptop:~# lsmod | grep prism
prism2_pci             72960  0
# ... and remove it
root@prewe-laptop:~# rmmod prism2_pci
```

```

# I install the orinoco and orinoco_pci drivers
root@prewe-laptop:~# modprobe orinoco
root@prewe-laptop:~# modprobe orinoco_pci
# ... and check the got installed
root@prewe-laptop:~# lsmod | grep orinoco
orinoco_pci             7168  0
orinoco                41748  1 orinoco_pci
hermes                  8576  2 orinoco_pci,orinoco
# ... and finally restart the network:
root@prewe-laptop:~# /etc/init.d/networking restart

```

It works, now, but it stops working after I reboot because the damn prism2_pci module gets loaded again. I am looking into that right now. I'll keep you posted.

---

### Post by epere4 on 2006-11-12
> **epere4 said:**
> It works, now, but it stops working after I reboot because the damn prism2_pci module gets loaded again. I am looking into that right now. I'll keep you posted.

I could finally solve that, too. 

I added the following line at the end of the file [COLOR="Red"]/etc/modprobe.d/blacklist[/COLOR], to prevent the [COLOR="Red"]prism2_pci[/COLOR] module from being loaded:

```
# This module is not the correct one for my wireless. Instead, we have to load orinoco and orinoco_pci
blacklist prism2_pci
```


Please, feel free to correct me if there is a better aproach to solve this kind of problems.

---

### Post by Drain on 2006-11-18
I found this thread to be helpful - I wish I could take credit for the solution.  Hope it helps you out. 

[http://www.ubuntuforums.org/showthread.php?t=288649](http://www.ubuntuforums.org/showthread.php?t=288649)

---


---
title: "wireless shows signal, can't connect (ath_pci)"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by bandofmercy on 2007-05-10
i just bought a cheap circuit city (400$) laptop--hoping to switch back into linux after a year's break & mainly want it for light web browsing, doc editing, email, etc.  feisty installed rather fine (besides a few minor issues that i can worry about later) & detected my network card right away as an atheros 5005g chipset.  network manager found my router and prompts me for a key (wep/hex/open).  i enter the key and a signal bar pops up at about 30%, better than i get on my desktop, but assigns no ip address... 

so it appears to be connected, but isn't.  is this a wireless manager issue or a module issue?  what should i do?  connecting through my ethernet card is possible, but i'd like to know what i'll be doing before i begin as it is a bit of a hassle to reach.

---

### Post by dbott67 on 2007-05-10
Can you post the output of the following commands:
```
scpl@dns2:~$ [COLOR=Blue]**cat /etc/network/interfaces**[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

``````
scpl@dns2:~$ [COLOR=Blue]**ifconfig -a**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:E0:29:7C:65:3F
          inet addr:192.168.128.59  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe7c:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:352562729 (336.2 MiB)  TX bytes:6776681 (6.4 MiB)
          Interrupt:9 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1740 (1.6 KiB)  TX bytes:1740 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``````
scpl@dns2:~$ [COLOR=Blue]**iwlist scanning**[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

``````
scpl@dns2:~$ [COLOR=Blue]**sudo lshw -C network**[/COLOR]
  *-network
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:e0:29:7c:65:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.128.59 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:feafbc00-feafbcff irq:9

``````
scpl@dns2:~$ [COLOR=Blue]**cat /etc/iftab**[/COLOR]
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:29:7c:65:3f arp 1

```*Note: if you can't get online with your system & you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (**cd ~**):*

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
iwlist scanning > iwlist.txt
``````
sudo lshw -C network > lshw.txt
``````
cat /etc/iftab > iftab.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by bandofmercy on 2007-05-10
ok- i'll get it up this evening~6pm us central time

thanks

---

### Post by bandofmercy on 2007-05-11
i've attached the files, but here they are
ifconfig
```

ath0      Link encap:Ethernet  HWaddr 00:C0:A8:D5:08:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:9826 (9.5 KiB)

eth0      Link encap:Ethernet  HWaddr 00:14:0B:0A:67:F1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x4800 

eth0:avah Link encap:Ethernet  HWaddr 00:14:0B:0A:67:F1  
          inet addr:169.254.6.154  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64164 (62.6 KiB)  TX bytes:64164 (62.6 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-C0-A8-D5-08-47-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3627 errors:0 dropped:0 overruns:0 frame:95198
          TX packets:459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:337655 (329.7 KiB)  TX bytes:30136 (29.4 KiB)
          Interrupt:22 


```

iftab
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:14:0b:0a:67:f1 arp 1
ath0 mac 00:c0:a8:d5:08:47 arp 1

```

interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

iwlist
```
ath0      Scan completed :
          Cell 01 - Address: 00:12:25:55:7D:47
                    ESSID:"Mission Haus"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100


```

lshw
```
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:14:0b:0a:67:f1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=half latency=24 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: ioport:4800-48ff iomemory:c9400400-c94004ff irq:21
  *-network
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@05:01.0
       logical name: wifi0
       version: 01
       serial: 00:c0:a8:d5:08:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c9000000-c900ffff irq:22

```

---

### Post by dbott67 on 2007-05-11
Hi,
 
Your wireless card does see the AP, which is good.  I'm assuming that your APs ESSID is "Mission Haus".
 
The next step is trying to get it to connect.
 
I generally recommend disabling security (WEP/WPA) as we attempt to trouble shoot.  It just eliminates the potential for trouble spots.
 
So, log in to your router and turn off any encryption and then try to connect.  If you can connect, the next step is to turn encryption back on and try to get it going.
 
What is the make & model of your router & what types of encryption does it support?
 
-Dave

---

### Post by bandofmercy on 2007-05-11
i tried disabling encryption a few nights ago--didn't help, although maybe i didn't give it enough time to work.  it is my parents,' some kind of motorola router, but i'll actually be moving into a new apartment in the next few weeks and am hoping for a laptop i can take to cafe hotspots and such.  i'll disable encryption when i get home and try it again, though.

i've also read that ubuntu's default network manager applet is buggy and that there are more reliable alternatives...?

---

### Post by dbott67 on 2007-05-11
> **bandofmercy said:**
> i've also read that ubuntu's default network manager applet is buggy and that there are more reliable alternatives...?

I had an old Toshiba laptop that I used wifi-radar with, but since buying my new laptop & finding out about network-manager I've never gone back (never any problems or reason to find an alternative).

So, you could try wifi-radar:
```
sudo apt-get install wifi-radar
``````
 sudo aptitude remove network-manager network-manager-gnome
```

[IMG]http://www.linux.com/blob.pl?id=1c42146ced37ecb861dc79247c56ccd9[/IMG]

Read this thread for some good tips:
[http://ubuntuforums.org/showthread.php?t=432933](http://ubuntuforums.org/showthread.php?t=432933)

Another ubuntu-related article here:
[http://www.linux.com/article.pl?sid=06/07/11/1354237](http://www.linux.com/article.pl?sid=06/07/11/1354237)

-Dave

---

### Post by bandofmercy on 2007-05-11
disabling encryption worked after i gave the router a few minutes to set itself up.  what now?

---

### Post by dbott67 on 2007-05-11
What's the make & model of your router?

And what types of encryption does it support?

---

### Post by bandofmercy on 2007-05-14
just to update, i took the laptop to my new apt and it set up fine after replacing wifi-radar with network-manager.  i don't know if it was changing to a new router or that this network has a password instead of a 26-digit hex key or just re-installing the network manager, but it works quite well--now i just need to get fixes for my resolution, my boot errors, & suspend/hibernate & i'll be good.

---


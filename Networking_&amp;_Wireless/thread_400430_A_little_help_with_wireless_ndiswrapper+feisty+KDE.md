---
title: "A little help with wireless: ndiswrapper+feisty+KDE+bcm4306"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by yojimbosteel on 2007-04-03
Okay so I've gone through about six guides for wireless with the broadcom card and I think I'm finally getting close. I just need a little bit more help.

This is my current problem: I am using KNetworkManager, the wireless network is detected so my card seems to be working partially, but when I click it to connect it hangs at 28%

[IMG]http://farm1.static.flickr.com/254/445149327_ecac90de32.jpg?v=0[/IMG][IMG]http://farm1.static.flickr.com/176/445149333_956682a5ed.jpg?v=0[/IMG]

**Here are my computer specs:**
Ubuntu 7.04 beta, Feisty Fawn
KDE
KNetworkmanager
ndiswrapper 1.9
dell 1350 broadcom 4306 wireless card
bcmwl5 driver from the dell site

**Here is all the related networking info:**

ifconfig:
```
cailan@tiger: ~ cailan@tiger:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:1C:4F:BE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:947 (947.0 b)  TX bytes:947 (947.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:C3:63:CC  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:327405 (319.7 KiB)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:faffc000-faffe000 
```

iwconfig:
```
cailan@tiger: ~ cailan@tiger:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"BigWave"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:40:96:58:65:B8   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

To confirm my hardware:
```
cailan@tiger: ~ cailan@tiger:~$ lspci | grep Broadcom\ Corporation
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

Ndiswrapper driver:
```
cailan@tiger: ~ cailan@tiger:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)
```

Loaded modules:
(/etc/modules)
```
cailan@tiger: ~ cailan@tiger:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper
```

Ndiswrapper alias:
(/etc/modprobe.d/ndiswrapper)
```
cailan@tiger: ~ cailan@tiger:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
```

Interfaces:
(/etc/network/interfaces)
```
cailan@tiger: ~ cailan@tiger:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
```

iftab:
(/etc/iftab)
```
cailan@tiger: ~ cailan@tiger:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0f:1f:1c:4f:be arp 1
wlan0 mac 00:90:96:c3:63:cc arp 1
```

Kernel:
```
cailan@tiger: ~ cailan@tiger:~$ uname -r
2.6.20-13-generic
```


**I have blacklisted bcm43xx**

This is what everything looks like under the network settings:

[IMG]http://farm1.static.flickr.com/231/445149337_4408df363a.jpg?v=0[/IMG]

I'm not sure whats going on. 
I've tried rebooting and have also tried a /etc/init.d/networking restart.

-Thanks in advance

---

### Post by garlik42 on 2007-04-03
I had a similar problem with a dell laptop and a broadcom wireless, think it was with 6.06.

The system locked up I can't remember where but 28% sounds close, I determined it was the security I was using on my wireless network. I tried a few different settings, but the only one I was able to get working was no security.

---

### Post by revmc on 2007-04-04
Have you blacklisted bcm43xx?

---

### Post by yojimbosteel on 2007-04-04
> Have you blacklisted bcm43xx?

Yes I have. 

I think I've pretty much decided that I don't like Broadcom and unless something works out, I'm just going to buy a new wireless card for my laptop. The Intel Pro/Wireless 2200 looks really good, fully supported and all, that way I won't have to deal with ndiswrapper.

---

### Post by styven on 2007-04-04
Hi there,

Do you intend to replace the internal card, I have been thinking about that, it comes out easy enough.

I am led to believe though that certain makers lock the bios to prevent you swapping the card over?

Any thoughts.

Steve.

---

### Post by yojimbosteel on 2007-04-04
> Do you intend to replace the internal card, I have been thinking about that, it comes out easy enough.

Yes, I do have an internal card. Its a mini PCI card which comes in a few different flavors.
The Intel Pro/Wireless card that I was looking at is a mini PCI 3B which is different from my current dell/broadcom 3A but after a little research it turns out that the connectors are the same and the difference is in size. So a 3B is considered more universal since it works for both 3A & 3B. This might not be new information for you but here's a link anyway:[http://en.wikipedia.org/wiki/Mini_PCI]("http://en.wikipedia.org/wiki/Mini_PCI")

> I am led to believe though that certain makers lock the bios to prevent you swapping the card over?

I havn't heard of this but check out this place
This is where I am buying my card from. They say they have been confirmed by buyers that the card works in the noted laptops, and they have a return policy ;) :[http://cgi.ebay.com/Intel-Pro-Wireless-2915ABG-Mini-PCI-2915-ABG-2200-A_W0QQitemZ190096909778QQcategoryZ45003QQrdZ1QQcmdZViewItem]("http://cgi.ebay.com/Intel-Pro-Wireless-2915ABG-Mini-PCI-2915-ABG-2200-A_W0QQitemZ190096909778QQcategoryZ45003QQrdZ1QQcmdZViewItem")

---


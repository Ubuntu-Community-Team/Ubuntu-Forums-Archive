---
title: "WiFi connection unstable -- RT2500 with ndiswrapper + Wicd"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by sergi-3 on 2013-12-23
Hello everybody,

I tried to get this to work a couple of years ago, but I eventually gave up and kept using a wired connection. Now I'm determined to get rid off the cable and get WiFi to work.

Basically: I have a Ralink 2500. With network manager and the drivers in the kernel, I got a very unstable connection and a low signal strenght. I read somewhere that Wicd would solve the issue, so I installed Wicd and removed network manager. Improved a bit, but still very bad. So I decided to remove the kernel modules for RT2500 and use ndiswrapper instead (blacklisted the original modules accordingly). Signal strenght and speed improved considerably, but I had the famous "Bad passwod" problem. Fixed it, but still had unstable connection. It would disconnect after a few minutes, or simply drop the speed to a point where it is unusable. I tried reverting back to network manager, which didn't really make it better, and now I've gone back to Wicd. The signal that Wicd reports seems to be good (75% and connecting at 36 or 54 Mbps). I also tried disabling IPv6 as advised in some forum -- still no improvement.

 At the moment, it takes it some time to connect, but it eventually does and it seems to work pretty well, but after some time (minutes, or just seconds) it becomes unusable. Pages won't load, and ping shows good times but with some intermittent drops.

 I'm lost here, don't really know what else to try. What am I missing? Help will be MUCH appreciated.

Here's some info you might find useful, please let me know if I can provide something else:

My wireless card:
```
sergi@shak:~$ lspci | grep Ralink
01:08.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
```

Ubuntu and kernel versions:
```
sergi@shak:~$ lsb_release -d
Description:    Ubuntu 12.04.3 LTS
sergi@shak:~$ uname -mr
3.2.0-57-generic x86_64
```

Modprobe outputs for ndiswrapper:
```
sergi@shak:~$ modprobe -l | grep ndis
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/usb/rndis_host.ko
updates/dkms/ndiswrapper.ko
```

and for RT2500:
```
sergi@shak:~$ modprobe -l | grep rt2500
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
```

Funny enough, the RT2500 modules show still in modprobe, although they are blacklisted?!

```
sergi@shak:~$ more /etc/modprobe.d/blacklist
blacklist rt2500
blacklist  rt2500pci
```

Also, I noticed that other Ralink related modules are also loaded, could this be a conflict? (notice the rt2x00 one...)
```
sergi@shak:~$ modprobe -l | grep rt2
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
```

_**EDIT:** my bad. Yes, ***modprobe*** shows the RT2500 and 2x00 modules, but as confirmed by ***lsmod*** these are **NOT** loaded. So this shouldn't really affect, should it?_

The network configuration over lshw:
```
sergi@shak:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2500 Wireless 802.11bg
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:91:7e:20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.57+Ralink Technology, Inc.,06/ ip=192.168.2.112 latency=32 link=yes multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:faefe000-faefffff
```


It took me several attempts to finally connect and be able to post the following:


Output from iwconfig:
```
sergi@shak:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"pizzaiolo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:8D:E0:E0   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-109 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2736  Invalid misc:4637   Missed beacon:0

eth0      no wireless extensions.
```

And iwlist scan, odd that my network 'pizzaiolo' shows weaker than some neighbours' 'Mensa', which is further away and with obstacles...:
```
sergi@shak:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 9C:C7:A6:03:AE:6A
                    ESSID:"Mensa"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACE131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 02 - Address: 00:1B:11:8D:E0:E0
                    ESSID:"pizzaiolo"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

eth0      Interface doesn't support scanning.
```


A typical ping shows good times, with some bad ones inbetween:
```
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=552 ttl=47 time=53.5 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=553 ttl=47 time=57.1 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=554 ttl=47 time=56.8 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=555 ttl=47 time=61.3 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=556 ttl=47 time=53.4 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=557 ttl=47 time=54.5 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=558 ttl=47 time=170 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=559 ttl=47 time=1066 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=560 ttl=47 time=165 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=561 ttl=47 time=1102 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=562 ttl=47 time=1864 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=563 ttl=47 time=867 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=564 ttl=47 time=659 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=565 ttl=47 time=232 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=566 ttl=47 time=75.4 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=567 ttl=47 time=55.7 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=568 ttl=47 time=62.1 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=569 ttl=47 time=55.6 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=570 ttl=47 time=54.5 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=571 ttl=47 time=1157 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=572 ttl=47 time=152 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=573 ttl=47 time=56.9 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=574 ttl=47 time=57.2 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=575 ttl=47 time=80.0 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=576 ttl=47 time=213 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=577 ttl=47 time=55.6 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=579 ttl=47 time=57.9 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=580 ttl=47 time=61.6 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=581 ttl=47 time=64.8 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=582 ttl=47 time=55.3 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=583 ttl=47 time=67.4 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=585 ttl=47 time=61.0 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=586 ttl=47 time=58.5 ms
64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=587 ttl=47 time=53.9 ms
^C64 bytes from bk-in-f147.1e100.net (173.194.69.147): icmp_req=588 ttl=47 time=55.3 ms

--- www.google.com ping statistics ---
588 packets transmitted, 557 received, 5% packet loss, time 707459ms
rtt min/avg/max/mdev = 51.889/73.544/1864.173/123.151 ms, pipe 2

```



Any ideas? I couldn't even post this through wireless... had to go back to eth0 :(

Thanks in advance!

---

### Post by chili555 on 2013-12-23
I feel like you just drove into my shop in your car with the trunk open, a couple of bullet holes in the passenger door and only three wheels and, when asked what was wrong, said, "My heater is not working." Wow! That's it??

You have multiple issues here. Let's see if we can sort them out one at a time and get this thing going. First, I wish to make a disclaimer; ndiswrapper is seldom the answer if a native driver is available. However, let's clean up what's wrong and see if we can get it going better. First:> sergi@shak:~$ more /etc/modprobe.d/blacklist
blacklist rt2500
blacklist  rt2500pciIn Ubuntu, since about 3-4 years ago, the file is called /etc/modprobe.d/blacklist**.conf**. I suspect you have such a file already so let's move the listings over to it and delete the incorrect file:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```At the end, add this line:```
blacklist rt2500pci
```Proofread, save and close gedit. There is no need to blacklist rt2500 because there is no such module. Now delete the incorrect file:```
sudo rm /etc/modprobe.d/blacklist
```> Yes, modprobe shows the RT2500 and 2x00 modules, but as confirmed by lsmod these are NOT loaded. So this shouldn't really affect, should it?Rather than guess, let's just see it:```
lsmod
```Are there any clues as to what's going on here?```
dmesg | grep ndis
```If we tweak ndiswrapper as far as we can tweak it and it's still not working, we may remove it and try a later version of rt2500pci. What Ubuntu version are you running?```
lsb_release -d
uname -r
modinfo rt2500pci | grep -i version
```Is your router set up to do N speeds? I doubt ndiswrapper, based on a creaky old XP driver, works well with N. I suggest you experimentally turn off N and see if the performance improves.

---

### Post by sergi-3 on 2013-12-23
Thanks for your answer. 

True! Massive mistake... but I checked the /etc/modprobe/blacklist.conf and there was, indeed, a blacklist entry for rt2500pci. I guess I had blacklisted it twice, in the wrong and the right blacklist file. I moved the blacklist entry to the end of the file, just in case it makes any difference, but I assume it doesnt. Also deleted the old file. 

Output of dmesg in regards to ndiswrapper:
```
sergi@shak:~$ dmesg | grep ndis
[   39.087778] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   39.285518] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/01/2006, 3.02.00.0000) loaded
[   39.285886] ndiswrapper 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[   39.286597] ndiswrapper: using IRQ 18
[   40.812740] usbcore: registered new interface driver ndiswrapper
```

Notice that I had run lsmod on my original post already, and confirmed that rt2500pci was not running.

And yes, I forgot to mention what version of Ubuntu I'm running and what version of rt2500 I had tried: 
```
sergi@shak:~$ lsb_release -d && uname -r && modinfo rt2500pci
Description:    Ubuntu 12.04.3 LTS
3.2.0-57-generic
filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B0FB755986B42553D4F3F0E
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.2.0-57-generic SMP mod_unload modversions 


```

My router supports 54Mbps, but I'll try downgrading the speed of the link anyway and see if it helps. 

Any more ideas?

---

### Post by chili555 on 2013-12-23
>  I moved the blacklist entry to the end of the file, just in case it makes any difference, but I assume it doesnt. Also deleted the old file. Excellent.> Notice that I had run lsmod on my original post already, and confirmed that rt2500pci was not running.And no other little rt2x00 cousins, either, I hope. > [   39.087778] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   39.285518] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/01/2006, 3.02.00.0000) loaded
[   39.285886] ndiswrapper 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[   39.286597] ndiswrapper: using IRQ 18
[   40.812740] usbcore: registered new interface driver ndiswrapperPerfect. In other words, nothing to fix here, because there is nothing wrong. I do see that you are running version 1.57 of ndiswrapper; 1.59 is available so we might try compiling it to see if it helps.> filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
[COLOR="#FF0000"]version:        2.3.0[/COLOR]
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)For comparison, here is what's on my 3.12 system:> filename:       /lib/modules/3.12.0-031200-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
[COLOR="#FF0000"]version:        2.3.0[/COLOR]
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
In other words, there doesn't appear to be an updated driver available.

I suggest you try disabling N in the router. If that doesn't help, let's compile ndiswrapper 1.59. If that doesn't help, except for Newegg, I am out of ideas.

---

### Post by chili555 on 2013-12-23
Oops! What does this mean? I thought it was a PCI device:> [COLOR="#FF0000"]usbcore[/COLOR]: registered new interface driver ndiswrapper Where did you get the driver files for the device? May I see:```
ndiswrapper -l
```Interesting!

---

### Post by sergi-3 on 2013-12-23
mmmm.... right, I hadn't realised either. I'm pretty sure the drivers were off a PCI device though. Here's the requested info:

```

sergi@shak:/$ ndiswrapper -l
rt2500 : driver installed
    device (1814:0201) present (alternate driver: rt2500pci)


```

---

### Post by chili555 on 2013-12-23
Let's see if there are any interesting clues in the .inf file:```
cat /etc/ndiswrapper/rt2500/rt2500.inf | head -n15
```Fascinating...

---

### Post by sergi-3 on 2013-12-23
Not much in there...

```
sergi@shak:/$ cat /etc/ndiswrapper/rt2500/rt2500.inf | head -n15
;****************************************************************************************
;
; RT2500.inf
;
;   This installation script supports Windows 98,Me,2000 & XP for the
;   Ralink RT2500 series Wireless LAN Card.
;
;   Copyright (c)2002-2004, Ralink Technology Corp., All Rights Reserved
;   All Rights Reserved.
;   Developed by RaLink Technology, Corp. -- http://www.ralinktech.com
;
;****************************************************************************************

[Version]
Signature       = "$Chicago$"


```

---


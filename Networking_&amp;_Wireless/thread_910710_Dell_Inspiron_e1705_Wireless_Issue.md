---
title: "Dell Inspiron e1705 Wireless Issue"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by Boompoet on 2008-09-04
:confused:   **O.k.... I know there are a ton of wireless problem posts, but I'm a noob when it comes to Linux, just installed it for the first time two days ago. I am having issues with my wireless internet connection. The network is recognized fine, but I'm not being assigned an IP for the wireless connection. I have it plugged in now and after reading some of the other posts, I took some steps to help you great and brilliant people figure this out. Here goes:**
[B]
I typed in Lshw -C and got the following:[/B]

Hardware Lister (lshw) - B.02.12.01

usage: lshw [-format] [-options ...]

       lshw -version



	-version        print program version (B.02.12.01)



format can be

	-html           output hardware tree as HTML

	-xml            output hardware tree as XML

	-short          output hardware paths

	-businfo        output bus information



options can be

	-class CLASS    only show a certain class of hardware

	-C CLASS        same as '-class CLASS'

	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )

	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

	-quiet          don't display status

	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


**Then I did the ifconfig command and got this:**

eth0      Link encap:Ethernet  HWaddr 00:14:22:f5:19:3e  

          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::214:22ff:fef5:193e/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1203 errors:1 dropped:1 overruns:0 frame:0

          TX packets:971 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:1481153 (1.4 MB)  TX bytes:119788 (116.9 KB)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1847 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1847 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:93251 (91.0 KB)  TX bytes:93251 (91.0 KB)



wlan0     Link encap:Ethernet  HWaddr 00:16:ce:6a:53:2b  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:10728 (10.4 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-16-CE-6A-53-2B-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[B]

And finally, I typed this iwconfig and got the following:[/B]

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:""  

          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:78:04:AA   

          Bit Rate=12 Mb/s   Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality=98/100  Signal level=-37 dBm  Noise level=-64 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[B]
Now all that being said, Keep in mind I'm really new at this. The closest I've messed with anything remotely similar was the unix server in college and that was so long ago, I'm windows sloppy now. If anyone can help, I'd greatly appreciate it.[/B]

:popcorn:

---

### Post by Crafty Kisses on 2008-09-05
You forgot this command, I'd like to see it:
```
lshw -C network
```

---

### Post by Ayuthia on 2008-09-05
> **Codename said:**
> You forgot this command, I'd like to see it:
```
lshw -C network
```

By the way, the command is case-sensitive.  It looks like you tried in the first part of your post and left out the word network but you also had a capital L instead of the lower-case l.

---

### Post by Boompoet on 2008-09-05
**Alrighty. I've got the corrected lshw -C network typed in and here's what I got.**


WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
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
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:f5:19:3e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.2 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:6a:53:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


**I hope it's a solvable problem. I travel for work and this system is my window on the world. :) In all other ways, I'm really loving Linux.**

---

### Post by Ayuthia on 2008-09-05
> **Boompoet said:**
> **Alrighty. I've got the corrected lshw -C network typed in and here's what I got.**


WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
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
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:f5:19:3e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.2 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:6a:53:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


**I hope it's a solvable problem. I travel for work and this system is my window on the world. :) In all other ways, I'm really loving Linux.**

Does it produce any results when you do the following:
```
sudo iwlist scan
```
This should produce a list of wireless access points.

---

### Post by Boompoet on 2008-09-05
**I typed sudo iwlist scan and here's what I got.**

sudo: unable to resolve host runabout
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:78:04:AA
                    ESSID:"ISLAND"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=83/100  Signal level=-53 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000020c38693c7
          Cell 02 - Address: 00:18:4D:9E:2F:1C
                    ESSID:"Stonejam"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/100  Signal level=-68 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000002d2953437

**Island is my network and "Stone Jam" is the neighbor's. Runabout is the name of the computer.**

---

### Post by ursus262 on 2008-09-05
Hi there.

You might be better off installing Kubuntu, as that seems to handle wireless better, thanks to the Knetworkmanager.

Other options:  try downloading ndiswrapper and the windows driver for your wireless card.  Ndiswrapper will enable this driver to work.  You can determine the driver name by looking in your Windows driver directory.

The other thing you could do is to try re-installing Ubuntu, and doing it with an ethernet cable connecting your laptop to your router/switch.  Doing it this way means that Ubuntu is automatically updated with the very latest updates. Usually, this helps. Just a thought.

I had problems with Ubuntu and wireless, and it was only when I installed Kubuntu that I found my wireless was working OK.

Hope this helps

---

### Post by Boompoet on 2008-09-05
When I installed Ubuntu was connected directly so I did get the updated drivers and programs. I was worried I might have issues with wireless so I left the cable connected. I just checked and Ndiswrapper is installed. Can you install Kubuntu over ubuntu or would I have to format? I would hate to start all over.

---

### Post by ursus262 on 2008-09-05
Please PM Me.  I've got a list of software repositories, but can't seem to copy them here, so I need to email it to you.

Dave

---

### Post by ursus262 on 2008-09-05
Take a look at these:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/i-just-bought-a-new-dell-inspiron-e1705-and-it-will-not-detect-the-wireless-network-423449/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/i-just-bought-a-new-dell-inspiron-e1705-and-it-will-not-detect-the-wireless-network-423449/)

and

[http://ubuntuforums.org/showthread.php?t=297092&highlight=inspiron+6400](http://ubuntuforums.org/showthread.php?t=297092&highlight=inspiron+6400)

(following the instructions at step 2 first part, then from step 4 onwards)  Note that this is for the Inspiron 6400.  They should work, but the driver, R151516.exe is the wrong driver.  Try identifying the name of the driver for your card, and substitute this with R151516.exe.  Typically, it should be in the form of Rxxxxxx.exe

Dave

---

### Post by Ayuthia on 2008-09-05
> **Boompoet said:**
> When I installed Ubuntu was connected directly so I did get the updated drivers and programs. I was worried I might have issues with wireless so I left the cable connected. I just checked and Ndiswrapper is installed. Can you install Kubuntu over ubuntu or would I have to format? I would hate to start all over.

I am thinking that you could just install Knetwork manager without having to reinstall everything, but I have never tried.  However, Ubuntu should work just fine with your card (I have the same card and it works with Hardy and Intrepid).  If you are using ndiswrapper, please check ndiswrapper -l to make sure that the device is present.  If it is, please try the following:
```

sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
```
This will only work for this session.  It is just a way to test out if ndiswrapper will work or not.  If it does connect, please post the results of the following:
```
cat /etc/modules |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
cat /etc/modprobe.d/blacklist|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
```
This will help us determine what we will need to add/remove to get the card working.

---

### Post by xfire on 2008-09-05
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Boompoet on 2008-09-05
I'm not getting it. I'm copying and pasting into terminal so I don't screw up, but changing directories and trying to get everything in the right place, running as root, etc. I don't know what most of this stuff means. I followed the directions found here -> [http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL) which I found from one of your links Dave. That's my card there, the 3945. I got the new drivers for linux which I believe were installed, and tried best I could to follow the instructions, but I'm at a loss. Now, the wireless isn't detecting anything. Before it was detecting the network, but I wasn't able to get online.

Correction, it's still recognizing the network, but still no joy on the internet

---

### Post by Ayuthia on 2008-09-05
> **Boompoet said:**
> I'm not getting it. I'm copying and pasting into terminal so I don't screw up, but changing directories and trying to get everything in the right place, running as root, etc. I don't know what most of this stuff means. I followed the directions found here -> [http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL) which I found from one of your links Dave. That's my card there, the 3945. I got the new drivers for linux which I believe were installed, and tried best I could to follow the instructions, but I'm at a loss. Now, the wireless isn't detecting anything. Before it was detecting the network, but I wasn't able to get online.

Correction, it's still recognizing the network, but still no joy on the internet
Actually, you don't have the 3945.  You have a Broadcom card.  This is based on the information that you posted earlier:
```

WARNING: you should run this program as super-user.
*-network
description: Network controller
product: BCM4311 802.11b/g WLAN
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
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: 00:14:22:f5:19:3e
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.2 latency=64 module=ssb multicast=yes
*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:16:ce:6a:53:2b
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
Did you try the commands that I posted in post 11?  If so, are you still able to see the wireless networks:
```
sudo iwlist scan
```
You might also try to see if you can connect without having encryption on the router.  It will help us see where the problem might be.

---

### Post by Boompoet on 2008-09-05
here you go Ayunthia...thanks for your help

jones@runabout:~$ sudo iwlist scan
sudo: unable to resolve host runabout
[sudo] password for jones: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:78:04:AA
                    ESSID:"ISLAND"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=81/100  Signal level=-55 dBm  Noise level=-64 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000255bca8195
          Cell 02 - Address: 00:18:4D:9E:2F:1C
                    ESSID:"Stonejam"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/100  Signal level=-70 dBm  Noise level=-64 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000024fb6f777

---

### Post by Ayuthia on 2008-09-05
> **Boompoet said:**
> here you go Ayunthia...thanks for your help

jones@runabout:~$ sudo iwlist scan
sudo: unable to resolve host runabout
[sudo] password for jones: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:78:04:AA
                    ESSID:"ISLAND"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=81/100  Signal level=-55 dBm  Noise level=-64 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000255bca8195
          Cell 02 - Address: 00:18:4D:9E:2F:1C
                    ESSID:"Stonejam"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/100  Signal level=-70 dBm  Noise level=-64 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000024fb6f777

Can you post the results of the following:
```
ndiswrapper -v
ndiswrapper -l
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e wl -e ndiswrapper
```
The first command will check and see if you have a valid version of ndiswrapper.  The second command will check and see if you have a valid Windows driver installed.  The third command will check and see what wireless module is currently loaded.

---

### Post by Boompoet on 2008-09-05
**ISSUE RESOLVED**

I had a buddy come by, the one that turned me on to Linux and it was a simple fix. After about fifteen minutes, he realized the 128 bit encryption was set wrong. My router was set to 64 bit. He set the encryption correctly and ran the hardware test and it's working fine now.

I want to say that the community here is the absolute best. You don't find people who care like you guys do on any other OS forums. Thank you all so much for the assistance. You rock.  :)

---

### Post by ursus262 on 2008-09-06
Aaaah!  So it was really that simple:rolleyes:

One really learns as one goes along!  Glad you've got it sorted though.

---

### Post by ursus262 on 2008-09-07
... And another thing...

I've just found out that I don't have ndiswrapper installed on my laptop.  Yet my dell wirless is working perfectly.  This gets stranger and stranger.  My linux installation is working like a dream and I don't even know why! :lolflag:

---

### Post by Ayuthia on 2008-09-07
> **ursus262 said:**
> ... And another thing...

I've just found out that I don't have ndiswrapper installed on my laptop.  Yet my dell wirless is working perfectly.  This gets stranger and stranger.  My linux installation is working like a dream and I don't even know why! :lolflag:

Dell uses various wireless cards so it might be possible that your card just works out of the box in Linux.  If you are really curious, can you post the following info:
```
lspci -nn
lshw -C network
uname -a
```
They will help us see your network card info, the driver your network card is using, and what kernel version you are using.

---


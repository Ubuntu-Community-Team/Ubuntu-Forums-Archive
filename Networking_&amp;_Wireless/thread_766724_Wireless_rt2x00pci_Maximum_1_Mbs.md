---
title: "Wireless rt2x00pci Maximum 1 Mb/s"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by LEMONed on 2008-04-25
OK, so I had Kubuntu 7.04 where my wireless support was the greatest anyone had ever seen.

I then moved to Debian, had to compile and install the rt2x00 drivers myself but aside from that, it was on par to 7.04.

I've just moved back to Kubuntu and seem to be having major issues with my wireless speed. Output from iwconfig shows instantly my problem:

> joshua@Lemon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Miaow"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:11:50:80:94:88
          Bit Rate=1 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=68/100  Signal level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

You can see the "Bit Rate is a meagre 1 Mb/s (on a 54 Mb/s card?). I know it's not the location because (afaik) the router hasn't been moved and a laptop running Vista placed next to it gets an 'Excellent' connection with throughput.

ifconfig (removing eth0 and l0):
> joshua@Lemon:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:11:50:90:d1:35
          inet addr:192.168.2.23  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe90:d135/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:118177079 (112.7 MB)  TX bytes:6133391 (5.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-90-D1-35-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lspci (the wireless card is at 00:09.0):
> joshua@Lemon:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 47)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter
00:05.0 IDE interface: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2)

uname -a:
> joshua@Lemon:~$ uname -a
Linux Lemon 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

lsmod | grep rt2 -i:
> 
joshua@Lemon:~$ lsmod | grep rt2 -i
rt2500pci              22656  0
rt2x00pci              12800  1 rt2500pci
rt2x00lib              25344  2 rt2500pci,rt2x00pci
rfkill                 10128  1 rt2x00lib
input_polldev           6928  1 rt2x00lib
crc_itu_t               3584  1 rt2x00lib
mac80211              192532  3 rt2500pci,rt2x00pci,rt2x00lib
eeprom_93cx6            3840  1 rt2500pci


In a possibly related manner, Wireshark fails to find *any* network interface but that isn't the largest problem. What I'm asking is, how do I further go on to diagnose my problem? (As is normally the problem with Linux for me...) Should I consider compiling my own drivers from source that I know to work?

---

### Post by ernstblaauw on 2008-04-25
I have this problem too. I hope someone can find a solution to this! (I'm not able to solve it :-( )

---

### Post by shivans on 2008-04-25
Same problem here.

I'm currently at work so I can't post my connection info, but I do know I have the same 1mb/s bit rate when it should be 54mb/s.
I'm unable to download faster than 18kbs. I've booted back into windows to make sure it wasn't a connection problem and can download at the usual 2000+kbs. I also have the full 4 bars coverage.

I'm a linux noob so I'd be grateful for any solution/walkthrough.

:)

---

### Post by LEMONed on 2008-04-25
More output, lshw -C net (removed the listed wired network card):
>   *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 01
       serial: 00:11:50:90:d1:35
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.2.23 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g


I think I'm going to try and compile the rt2x00 drivers from source, will post a step-by-step if it works!

---

### Post by shivans on 2008-04-25
Good luck, let us know how you get on :D

---

### Post by LEMONed on 2008-04-25
Ha! Look what I found on the [rt2x00 home page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page):

> two days ago, January 24th, Linux Kernel 2.6.24 was released. This is the first mainline kernel that includes (sadly a somewhat buggy) rt2x00 release.

Which corresponds to the Kernel I'm running (which I haven't changed at all).

---

### Post by shivans on 2008-04-25
I need to get home and find out what chipset my wireless is using.
I wonder if anyone notices if I sneak out of work an hour early...

---

### Post by LEMONed on 2008-04-25
Weey heeey! [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4579](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4579)

That link describes the problem, the last post describes what I will attempt to do. Hopefully all will go well and I'll have a decent Internet connection again!

---

### Post by jcmeliton on 2008-04-25
I solved but....

my system...
root@Antarez:/home/jcmeliton# sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wmaster0
       version: 00
       serial: 00:80:5a:39:23:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.10 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g

root@Antarez:/home/jcmeliton# modinfo rt61pci
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.0.10
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     D71C36F67F7A0F8B005A78F
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,mac80211,eeprom_93cx6
vermagic:       2.6.24-16-generic SMP mod_unload 586 

root@Antarez:/home/jcmeliton# iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WLAN_3B"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:01:38:9A:2F:60   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          Link Quality=47/100  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@Antarez:/home/jcmeliton# lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0a.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

/etc/network/interfaces
auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:XXXXXXXXXXXXX
wireless-essid WLAN_3B

auto wlan0

root@Antarez:/home/jcmeliton# route
Tabla de rutas IP del núcleo
Destino Puerta de Enlace Genmask Banderas Metrica Ref Uso Interfaz
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0


root@Antarez:/home/jcmeliton# uname -r
2.6.24-16-generic


I Solved with this.....

sudo apt-get install build-essential linux-headers-`uname -r`
cd ~
mkdir ~/rt61
cd ~/rt61
wget [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
tar -zxvf rt61-cvs-daily.tar.gz
cd rt61-cvs*/Module
make
sudo modprobe -r rt61pci
echo 'blacklist rt61pci' | sudo tee -a /etc/modprobe.d/blacklist

sudo make install
echo 'rt61' | sudo tee -a /etc/modules

And Edit the right parameters for your connexion

sudo gedit /etc/network/interfaces


AND NOW...

root@Antarez:/home/jcmeliton# iwconfig
lo        no wireless extensions.

wlan0     RT61 Wireless  ESSID:"WLAN_3B"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:01:38:9A:2F:60   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:5830-3030-3133-3839-3945-3033-42
          Link Quality=38/100  Signal level:-60 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



BIT RATE IS OK,....But still the navigation is very slow, and slow to resolve, I change in resolv.conf OPENDNS server to my ISP SERVER and it is slow.....
any solution....

---

### Post by shivans on 2008-04-25
> **LEMONed said:**
> Weey heeey! [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4579](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4579)

That link describes the problem, the last post describes what I will attempt to do. Hopefully all will go well and I'll have a decent Internet connection again!


The very last post in that thread shows his subsystem as MSI with a very similar device id to my own.
I have a feeling this could be the answer to the problems I have also. 

Thanks for posting the link :)

---

### Post by LEMONed on 2008-04-25
Here is how to rectify the problem, you will need to open a new shell and execute the following commands:

[list=1]
[*]mkdir rt2500
[*]cd rt2500
[*]wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
[*]tar -xzf rt2500-cvs-daily.tar.gz
[*]cd rt2500-cvs-2008042510/Module/
[*]make
[*]sudo make install
[*]cd ../../../
[*]rm -R rt2500
[/list]

The last two commands should delete the directory you created at the start.

You're now at a point where you've installed the module you want but isn't loaded and won't be loaded at boot time. Before we do this, however, we want to test that it actually works.

In the same shell as before, attempt the following commands. Feel free to replace sudo su with many laborious sudo commands:

[list=1]
[*]sudo su
[*]rmmod rt2500pci
[*]rmmod rt2x00pci
[*]rmmod rt2x00lib
[*]rmmod mac80211
[*]Utter your own trademarked catchphrase suggesting a inevitable farewell to your current wireless connection.
[*]modprobe rt2500
[*]ifconfig ra0 up
[*]iwlist ra0 scan
[/list]

Now hopefully, if all is well, you'll get a nice happy scan result showing your router. If it doesn't give any results but no apparent indication of an error at any of the steps above, it's bad, but not as bad as an error. You're probably just to far away from the router itself or something else way beyond this mini-tutorial.

Now to connect to our router:
[list=1]
[*]ifconfig ra0 down
[*]iwconfig essid <Name of your network>
[*]iwconfig key <Your network key>
[*]ifconfig ra0 up
[*]dhclient ra0
[/list]


You should be given an IP address and be able to load t'inernet at, and I quote for added dramatic effect:
> Bit Rate=54 Mb/s

Now, you should blacklist your old drivers so that they aren't used when you next restart your computer (as root) type:
> nano /etc/modprobe.d/blacklist
Add the following to the bottom of the file on a separate line:
> #User added, remove rt2x00 from 2.6.24 kernel
blacklist rt2500pci
blacklist rt2x00pci
blacklist rt2x00lib
blacklist mac80211

---

### Post by LEMONed on 2008-04-25
There are a few problems, however.

KNetowrkManager can't use it which means programs that wait for an active network connection will refuse to connect to the Internet (including Firefox 3 and Pidgin).

Some nice guy on IRC suggested that I: just disable the "network status daemon" in systemsettings->advance->service manager

It didn't work for me and I reckon this is Kubuntu specific but, a restart might fix things.

Also, you'll need to set up a script to automatically enter in your details at boot time. I think the README in the Modules/ folder (in the tar ball) provided details on that.

---

### Post by shivans on 2008-04-25
Thanks LEMONed, thats a detailed walkthrough.

I've got a problem though. I've scanned for my network and found it using:-

IFCONFIG wlan0 scan (I need to use wlan0 instead of ra0) 

However when I try to connect with:-

IWCONFIG essid Mikes-Network

I get the error message:- 

iwconfig: unknown command "Mikes-Network"


Hope you can help further, cheers.

---

### Post by ernstblaauw on 2008-04-25
> **shivans said:**
> Thanks LEMONed, thats a detailed walkthrough.

I've got a problem though. I've scanned for my network and found it using:-

IFCONFIG wlan0 scan (I need to use wlan0 instead of ra0) 

However when I try to connect with:-

IWCONFIG essid Mikes-Network

I get the error message:- 

iwconfig: unknown command "Mikes-Network"


Hope you can help further, cheers.
I think you should do:
```
IWCONFIG wlan0 essid Mikes-Network
```
However, the 'key' command doesn't work here. It says, after doing ' iwconfig wlan0 key "<thekeyIentered>"':
```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "<thekeyIentered>".
```

If I do: 
```
iwpriv wlan0 set WPAPSK="<thekeyIentered>"
```
I get 
```
wlan0     no private ioctls.
```

---

### Post by ernstblaauw on 2008-04-25
> **LEMONed said:**
> Here is how to rectify the problem, you will need to open a new shell and execute the following commands:

[list=1]
[*]mkdir rt2500
[*]cd rt2500
[*]wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
[*]tar -xzf rt2500-cvs-daily.tar.gz
[*]cd rt2500-cvs-2008042510/Module/
[*]make
[*]sudo make install
[*]cd ../../../
[*]rm -R rt2500
[/list]

The last two commands should delete the directory you created at the start.

You're now at a point where you've installed the module you want but isn't loaded and won't be loaded at boot time. Before we do this, however, we want to test that it actually works.

In the same shell as before, attempt the following commands. Feel free to replace sudo su with many laborious sudo commands:

[list=1]
[*]sudo su
[*]rmmod rt2500pci
[*]rmmod rt2x00pci
[*]rmmod rt2x00lib
[*]rmmod mac80211
[*]Utter your own trademarked catchphrase suggesting a inevitable farewell to your current wireless connection.
[*]modprobe rt2500pci
[*]ifconfig ra0 up
[*]iwlist ra0 scan
[/list]

Now hopefully, if all is well, you'll get a nice happy scan result showing your router. If it doesn't give any results but no apparent indication of an error at any of the steps above, it's bad, but not as bad as an error. You're probably just to far away from the router itself or something else way beyond this mini-tutorial.

Now to connect to our router:
[list=1]
[*]ifconfig ra0 down
[*]iwconfig essid <Name of your network>
[*]iwconfig key <Your network key>
[*]ifconfig ra0 up
[*]dhclient ra0
[/list]


You should be given an IP address and be able to load t'inernet at, and I quote for added dramatic effect:


Now, you should blacklist your old drivers so that they aren't used when you next restart your computer (as root) type:

Add the following to the bottom of the file on a separate line:

After disabling the kernel modules, you modprobe rt2500pci. Isn't the pci version the new, experimental version and thus you just reactivate the just disabled driver?

I also tried modprobe rt2500, but no netwerk devices come up.

---

### Post by odiseo77 on 2008-04-25
Hi people, I'm having the same issue (I posted it [here]("http://ubuntuforums.org/showthread.php?t=767469")). I blacklisted the rt2500pci module and installed the rt2500 cvs driver from the serialmonkey site, and even though there was a slight speed improvement (very subtle), my connection is still slow (no more than 45 kb/s in the best of cases), so it doesn't seem to be directly related to the rt2x00 driver that comes by default on Hardy, but something else. If I manage to solve this, I'll report back (and if someone has found the solution, I'd appreciate it).

Greetings.

EDIT: It finally worked. I just had to reboot. now everything is working fine. Just in case, I also issued the following command:

```
sudo iwconfig ra0 rate 54M auto
```

Now my download speed is 120-130 kb/s (which is my average).

Hope this helps someone

---

### Post by ernstblaauw on 2008-04-26
I solved it by doing:

```
cd ~
mkdir ~/rt2500
cd ~/rt2500
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -zxvf rt2500-cvs-daily.tar.gz
cd rt2500-cvs*/Module
make
sudo modprobe -r rt2500pci
echo 'blacklist rt2500pci' | sudo tee -a /etc/modprobe.d/blacklist
sudo make install
echo 'rt2500' | sudo tee -a /etc/modules
```

After this, I replaced the content of /etc/network/interfaces with:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "******"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="*********"
pre-up ifconfig ra0 up
```

I don't now if I restarted the computer of only restarted the network services (sudo /etc/init.d/networking restart). For sure, a reboot will be fine.

It works now! However, NetwrokManager doesn't work with this driver; you can use RutilT, a very well working replacement for NetworkManager:
```
sudo apt-get install rutilt
```

Inside System --> Preferences --> Sessions, you can deselect the NetworkManager from the startup list, and add RutilT.

For me, it works beautifully!

---

### Post by shivans on 2008-04-26
> **ernstblaauw said:**
> I solved it by doing:

```
cd ~
mkdir ~/rt2500
cd ~/rt2500
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -zxvf rt2500-cvs-daily.tar.gz
cd rt2500-cvs*/Module
make
sudo modprobe -r rt2500pci
echo 'blacklist rt2500pci' | sudo tee -a /etc/modprobe.d/blacklist
sudo make install
echo 'rt2500' | sudo tee -a /etc/modules
```

After this, I replaced the content of /etc/network/interfaces with:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "******"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="*********"
pre-up ifconfig ra0 up
```

I don't now if I restarted the computer of only restarted the network services (sudo /etc/init.d/networking restart). For sure, a reboot will be fine.

It works now! However, NetwrokManager doesn't work with this driver; you can use RutilT, a very well working replacement for NetworkManager:
```
sudo apt-get install rutilt
```

Inside System --> Preferences --> Sessions, you can deselect the NetworkManager from the startup list, and add RutilT.

For me, it works beautifully!


I can confirm that this worked for me too.

Thank you sooo much. I now have wireless working at full speed.

Goodbye WinDOH, you won't be missed.

---

### Post by RedPillMode on 2008-11-22
Confirmed; This was still necessary for me at the time of 8.10. Thank you ernstblaauw!

Wonder why this is not fixed, perhaps this is is not necessary for newer cards.

---

### Post by heyho on 2009-01-01
Can anybody else confirm that the RT2X00 drivers are still problematic - I bought my card specifically because they worked so well on previous releases!!!  AAAARRGGHHH!!!!

---

### Post by dukeinlondon on 2009-01-02
A note to all those using serial monkey's drivers, don't forget to recompile when you upgrade to a new kernel.

If using network manager matters more than having a permanent connection then you can use this trick :

iwconfig wlan0 rate 36M (or 54 48 24 whatever works best)

bug report thread where I've pick this up suggest putting the following script (under any name and suitably executable) in /etc/network/ip-up.d

#!/bin/bash
# Only for wlanX...
[[ $IFACE == wlan* ]] || exit 0
iwconfig $IFACE rate 36M

doesn't seem to work for me but maybe I've missed something

---

### Post by Wally_dog on 2009-01-16
Well, I followed the above for Ubuntu, except now I can see the network and it has about 80% strength, but when I try to connect only the first green dot lights up, and then I get the message "Unable to connect to the network". :(

---

### Post by dukeinlondon on 2009-01-22
Sorry can't help any more than that, one thing which works is that I get a connection quickly and reliable. If it could be fast, it'd be awsome. 

Anyway, the rt2x00pci has been broken for a long time and serial monkey's version doesn't get usually get included in distros cause it doesn't work with Network manager. Are there other wifi chips that have better opensource drivers ?

---

### Post by RavanH on 2009-07-15
Hi all,

I am an (X)Ubuntu user, so have no experience with KDE. However, I did fix my RT2500 slow connection problem by way of installing Wicd (replacing Network Manager) and adding a little pre-connection script. No core files or hacks needed.

Follow the how-to on [http://ubuntuforums.org/showthread.php?p=7605785](http://ubuntuforums.org/showthread.php?p=7605785)

Wicd is not Gnome dependent so this should work on KDE too. Please ty it out and let me know how it works for KDE. Any feedback is most welcome! :)

---


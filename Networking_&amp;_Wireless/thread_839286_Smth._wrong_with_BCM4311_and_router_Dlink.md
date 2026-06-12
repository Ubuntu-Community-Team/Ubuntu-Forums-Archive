---
title: "Smth. wrong with BCM4311 and router Dlink"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by player999 on 2008-06-24
I have wlan card BCM4311 with ndiswrapper driver and router DLink DI-524. Sometimes they are working together, but most times not, and i don`t know WHY. On router turned on DHCP server. When i use DHCP in connection , i see two interfaces wlan0 and wlan0:avahi, when i use static IP everything looks good(only looks, but it is not).
In both cases i can`t ping router and don`t have internet. But wlan card discover network. Ethernet card works fine with dhcp and static ip. Here is output of some commands:
```
player999@player999-laptop:~$ lshw -C network
*-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:5b:ad:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.0.2 latency=0 link=yes  module=ndiswrapper multicast=yes wireless=IEEE 802.11g

player999@player999-laptop:~$ ifconfig wlan0; iwconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:19:7e:5b:ad:56  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128096 (125.0 KB)  TX bytes:95476 (93.2 KB)
          Interrupt:16 Memory:68000000-68004000 

wlan0     IEEE 802.11g  ESSID:"WirelessTaras"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:11:FD:E2:5A   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:185  Invalid misc:6306   Missed beacon:0
 
```
S h i t happens!!!
](*,) Anybody please help me!!!

---

### Post by chili555 on 2008-06-24
> *-network DISABLEDDo you have a switch or key combination on your laptop that turns the wireless on and off? It appears to be off. Check with:```
sudo cat /var/log/messages | grep switch
```

---

### Post by player999 on 2008-06-24
Led on laptop, shows that wlan is up, when i turn off and then turned on wifi switch on laptop that "DISABLED" dissapeared, but wlan still not working. Output of your command din`t show any interesting:
```
Jun 24 10:34:00 player999-laptop kernel: [ 1336.039743] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00db2001
Jun 24 10:34:49 player999-laptop kernel: [   14.448359] SMP alternatives: switching to UP code
Jun 24 10:34:49 player999-laptop kernel: [   15.257186] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 11:00:11 player999-laptop kernel: [   13.682358] SMP alternatives: switching to UP code
Jun 24 11:00:11 player999-laptop kernel: [   14.490450] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 11:45:14 player999-laptop kernel: [ 1265.422969] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00db2001
Jun 24 11:46:09 player999-laptop kernel: [   14.695298] SMP alternatives: switching to UP code
Jun 24 11:46:09 player999-laptop kernel: [   15.502894] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 11:59:04 player999-laptop kernel: [   14.720081] SMP alternatives: switching to UP code
Jun 24 11:59:04 player999-laptop kernel: [   15.527564] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 12:05:28 player999-laptop kernel: [   14.649142] SMP alternatives: switching to UP code
Jun 24 12:05:28 player999-laptop kernel: [   15.456872] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 12:22:29 player999-laptop kernel: [  540.973486] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00db2001
Jun 24 12:23:18 player999-laptop kernel: [   14.803015] SMP alternatives: switching to UP code
Jun 24 12:23:18 player999-laptop kernel: [   15.611596] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 12:27:22 player999-laptop kernel: [   14.269982] SMP alternatives: switching to UP code
Jun 24 12:27:22 player999-laptop kernel: [   15.077368] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 13:25:01 player999-laptop kernel: [   14.089563] SMP alternatives: switching to UP code
Jun 24 13:25:01 player999-laptop kernel: [   14.897190] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 14:31:55 player999-laptop kernel: [   14.328510] SMP alternatives: switching to UP code
Jun 24 14:31:55 player999-laptop kernel: [   15.136091] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 24 15:38:50 player999-laptop kernel: [   14.605442] SMP alternatives: switching to UP code
Jun 24 15:38:50 player999-laptop kernel: [   15.413190] ACPI: EC: non-query interrupt received, switching to interrupt mode

```

---

### Post by player999 on 2008-06-24
Some details about network configuration on router
Channel 1
Security WPA-PSK/WPA2-PSK

---

### Post by chili555 on 2008-06-24
When you boot with the wireless switch enabled, and then do:```
sudo modprobe ndiswrapper
```does your wireless come to life?

---

### Post by player999 on 2008-06-24
It doesn`t help
I run(manually) script at sturtup to activate wireless card(led turned on):
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

One more: packets captured with wireshark during connection attachment

---

### Post by chili555 on 2008-06-24
> sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44I think these are in conflict. 

What is loaded on boot if you do *not* run these commands?```
lsmod | grep b4
lsmod | grep ssb
```Shouldn't the modules you *don't* want be blacklisted?

I actually think b44, and it's henchman ssb, is for a wired ethernet Broadcom card. Your *lshw* does not show one. From *modinfo b44:*> filename:       /lib/modules/2.6.25.5-1.1-default/kernel/drivers/net/b44.ko
version:        2.0
license:        GPL
description:    Broadcom 44xx/47xx 10/100 PCI ethernet driver

---

### Post by player999 on 2008-06-24
```
player999@player999-laptop:~$ lsmod | grep b4
b43                   159152  0 
rfkill                 10128  9 rfkill_input,b43
mac80211              192532  1 b43
input_polldev           6928  1 b43
led_class               7176  2 b43,acer_acpi
ssb                    39428  1 b43
player999@player999-laptop:~$ lsmod | grep ssb
ssb                    39428  1 b43

```
To set card up i used this tutorial:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")
Due to this tutorial i blackliseted only b43. These commands(post #6) change boot order of drivers to right.

---

### Post by chili555 on 2008-06-24
> **player999 said:**
> ```
player999@player999-laptop:~$ lsmod | grep b4
b43                   159152  0 
rfkill                 10128  9 rfkill_input,b43
mac80211              192532  1 b43
input_polldev           6928  1 b43
led_class               7176  2 b43,acer_acpi
ssb                    39428  1 b43
player999@player999-laptop:~$ lsmod | grep ssb
ssb                    39428  1 b43

```
To set card up i used this tutorial:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")
Due to this tutorial i blackliseted only b43. These commands(post #6) change boot order of drivers to right.Well, that is a bug, a big, ugly bug! Evidently, even though *b43* is blacklisted, it loads anyway and, furthermore, if you have a Broadcom card that uses *b44* and *ssb*, that card won't work correctly either. 

You, however, do not have a Broadcom 44xx/47xx 10/100 PCI ethernet card that needs *b44*, so you can omit the b44 and ssb stuff from your commands. You can simply do:```
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```I also see that farther along in the tutorial, it explains how to make the process automatic by modifying /etc/modprobe.d/ndiswrapper:> This is a much slicker solution than the previous versions (listed below), but it's unproven. This will customize how ndiswrapper loads:```

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```Have you tried this?

---

### Post by player999 on 2008-06-25
Much better:
```
player999@player999-laptop:~$ lsmod | grep b4
b44                    33168  0 
ssb                    39428  1 b44
mii                     7552  3 b44,8139cp,8139too
player999@player999-laptop:~$ lsmod | grep ssb
ssb                    39428  1 b44

```
But I still not have wlan!
Look at this:```

player999@player999-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:7e:5b:ad:56
Sending on   LPF/wlan0/00:19:7e:5b:ad:56
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

See that connections:
```

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:5b:ad:56  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11964 (11.6 KB)  TX bytes:9328 (9.1 KB)
          Interrupt:16 Memory:68000000-68004000 
wlan0:avahi Link encap:Ethernet  HWaddr 00:19:7e:5b:ad:56  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:68000000-68004000 

```
Why i can not get IP via dhcp:confused:

---


---
title: "Broadcom 4309 w/ Hardy"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by MrWES on 2008-10-15
Ok..I done several desktop installs with success. I've got my hands on a Dell D600 with a broadcom 4309 card:

```
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
```

I tried several howto's, using both ndiswrapper and bcm43xxcutter, both with no luck. I don't even see the network in network manager. Anyone successfully running the card in Hardy?

Thanks,
Bill

---

### Post by Ayuthia on 2008-10-15
Can you post the results of lspci -nn and ndiswrapper -l?  I would like to know the chipset of the 4309 card.

---

### Post by MrWES on 2008-10-15
> **Ayuthia said:**
> Can you post the results of lspci -nn and ndiswrapper -l?  I would like to know the chipset of the 4309 card.

bill@bill-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)
 
---------------------------------------------------

bill@bill-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4324) present (alternate driver: bcm43xx)

---

### Post by MrWES on 2008-10-15
This doesn't look right either:

bill@bill-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:73:3d:49
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5702-v2.25 ip=192.168.1.100 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:1b:e1:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Ayuthia on 2008-10-15
> **MrWES said:**
> This doesn't look right either:

bill@bill-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:73:3d:49
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5702-v2.25 ip=192.168.1.100 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:1b:e1:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Did you install bcm43xx-fwcutter or b43-fwcutter?  If you are not sure, please post the results of:
```
ls /lib/firmware
```
Since you have ndiswrapper installed, please try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
sudo iwlist scan
```
It looks like you might not have b43 and ssb blacklisted.

---

### Post by MrWES on 2008-10-15
> **Ayuthia said:**
> Did you install bcm43xx-fwcutter or b43-fwcutter?  If you are not sure, please post the results of:
```
ls /lib/firmware
```
Since you have ndiswrapper installed, please try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
sudo iwlist scan
```
It looks like you might not have b43 and ssb blacklisted.

bill@bill-laptop:~$ ls /lib/firmware/
2.6.24-16-generic     bcm43xx_initval05.fw  bcm43xx_microcode11.fw
2.6.24-21-generic     bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw  bcm43xx_pcm5.fw

-----------------------------------

bill@bill-laptop:~$ sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
FATAL: Module ssb is in use.

I take it that means ssb is NOT blacklisted

-----------------------------------

bill@bill-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

--------------------------
I just added bcm43xx and ssb to the blacklist file. I'm going to reboot and see if that helps.

Bill

---

### Post by MrWES on 2008-10-15
Ok..still no luck after a reboot. Dmesg still logging an error

 b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
bill@bill-laptop:~$ 

ssb module is still in use -- here's my blacklist; did I enter this correctly?

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist ssb

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

---

### Post by Ayuthia on 2008-10-15
> **MrWES said:**
> bill@bill-laptop:~$ ls /lib/firmware/
2.6.24-16-generic     bcm43xx_initval05.fw  bcm43xx_microcode11.fw
2.6.24-21-generic     bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw  bcm43xx_pcm5.fw

-----------------------------------
This shows that you instaled bcm43xx-fwcutter and not b43-fwcutter

> bill@bill-laptop:~$ sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
FATAL: Module ssb is in use.

I take it that means ssb is NOT blacklisted
It also means that there is another module that is using it.  By any chance, did you load b44?  The b43 and b44 are the only modules that I have seen use it.  If so, you should try the following instead:```

sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan
```

> -----------------------------------

bill@bill-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

--------------------------
I just added bcm43xx and ssb to the blacklist file. I'm going to reboot and see if that helps.

Bill
You should also include b43 and b43legacy into the blacklist file.  The bcm43xx is the depreciated module and b43/b43legacy are the replacements.

---

### Post by MrWES on 2008-10-15
> **Ayuthia said:**
> This shows that you instaled bcm43xx-fwcutter and not b43-fwcutter

It also means that there is another module that is using it.  By any chance, did you load b44?  The b43 and b44 are the only modules that I have seen use it.  If so, you should try the following instead:```

sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan
```


You should also include b43 and b43legacy into the blacklist file.  The bcm43xx is the depreciated module and b43/b43legacy are the replacements.

Ok I added b43 and b43legacy to the blacklist -- dmesg is now clean on boot.

sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper wl bcm43xx

returns a black line

sudo modprobe ndiswrapper

returns a blank line

sudo iwlist scan

returns: 
bill@bill-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results


ifconfig now shows a wlan1 -- that seems like progress.

bill@bill-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:73:3d:49  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe73:3d49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:665471 (649.8 KB)  TX bytes:60950 (59.5 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84700 (82.7 KB)  TX bytes:84700 (82.7 KB)

wlan1     Link encap:Ethernet  HWaddr 00:90:4b:1b:e1:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:fafee000-faff0000 

Although my wireless router does not show in the applet, nor System | Administration | Network. What am I missing here? -- I smell wireless :)

Bill

---

### Post by Ayuthia on 2008-10-15
For some reason, it is not picking up wireless sites.

You might try and see if you can connect manually.  If you are not using encryption try the following:
```
sudo iwconfig wlan1 essid <name-of-router without brackets>
sudo dhclient wlan1
```
You will most likely need to be disconnected from the wired connection.

---

### Post by MrWES on 2008-10-15
> **Ayuthia said:**
> For some reason, it is not picking up wireless sites.

You might try and see if you can connect manually.  If you are not using encryption try the following:
```
sudo iwconfig wlan1 essid <name-of-router without brackets>
sudo dhclient wlan1
```
You will most likely need to be disconnected from the wired connection.

Hrmm..Mount Horeb WI? Isn't that like the mustard capital of Wisconsin? heh..I lived in Chicago for 10 years.

Anywho...

bill@bill-laptop:~$ sudo dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 9051
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:90:4b:1b:e1:92
Sending on   LPF/wlan1/00:90:4b:1b:e1:92
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

No ideas from here -- obviously this is pissing me off :)

Bill

---

### Post by Ayuthia on 2008-10-15
> **MrWES said:**
> Hrmm..Mount Horeb WI? Isn't that like the mustard capital of Wisconsin? heh..I lived in Chicago for 10 years.

It was, but they are now moving to Middleton (about a 10 mile move) so it is now a place for trolls.

As for your wireless, this card is a little harder than others because I can't seem to find another driver for you and the b43 driver is limited.  If you want, you can try the b43.  You will need to install the b43-fwcutter (not the bcm43xx-fwcutter) package.  You will then need to unblacklist the b43, b43legacy, and ssb modules and blacklist ndiswrapper.

The system bumped your wlan to wlan1.  Do you have another wireless card in there?

---

### Post by MrWES on 2008-10-15
> **Ayuthia said:**
> It was, but they are now moving to Middleton (about a 10 mile move) so it is now a place for trolls.

As for your wireless, this card is a little harder than others because I can't seem to find another driver for you and the b43 driver is limited.  If you want, you can try the b43.  You will need to install the b43-fwcutter (not the bcm43xx-fwcutter) package.  You will then need to unblacklist the b43, b43legacy, and ssb modules and blacklist ndiswrapper.

The system bumped your wlan to wlan1.  Do you have another wireless card in there?

I guess I'll try that, I've tried so many combinations I wouldn't know WTF worked. Any recommendations on a USB wireless dongle? Preferably something newegg sells.

BTW, I truly appreciate all you help on this one. Hardy screams on this old Dell D600, but no wireless is a killa. 

Oh...there is bluetooth on the version -- any chances that is giving me problems? I looked in the BIOS to see if I could disable it, but there's not an option to do so.

Thanks,
Bill

P.S. Spent several summers up in Eagle River, lots of fond memories up there. My labs loved the water!

---

### Post by MrWES on 2008-10-16
UPDATE:

Ok, I just happened to have a dead Dell Inspirion 6000 at work, deak LCD screen. So I started poking around and found out it had an Intel Pro 2200 inside. So I took it out; it was located underneath the keyboard, and slapped inside my Dell D600 and b00m! Wireless connection metering at 100% strength. Very happy.

Ayuthia, thanks again for your time

Bill

---


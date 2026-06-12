---
title: "Remove all trace of wireless config?"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Mark457658946 on 2007-11-05
Hey,
I recently installed Ubuntu 7.10 and have been happilyusing my Edimax EW 7128G wireless pci card (driver rt61pci) to access my home network. This card works practically straight out of the box with ubuntu 7.04+, I only needed to edit /etc/network/interfaces to include thee essid and WEP key.

I found that whenever I was disconnected it would not automatically reconnect and that I had to reboot to regain my connection. In my attempts to rectify this I edited the configuration as per some of the information i found on other threads. This has for some reason messed up my settings and I am unable to connect, I cant even see the router!

Is there any way to either diagnose and fix this, or remove all the current configurations so that I can reinstall the card as I did when I first installed?

Apologies if this doesn't make complete sense!

---

### Post by wieman01 on 2007-11-05
What files have you edited? Please post the contents of each, that will help a lot. Morevoer please do a scan & post the output:
> sudo iwlist scan

---

### Post by Mark457658946 on 2007-11-05
Unfortunately I cant remember exactly everything I did as I was following instructions on threads which I cant find! I remember using the rmmod and insmod command once, other than that I'm not too sure.

mark@mark-desktop:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.


wmaster0  no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
         
 Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
   
       Link Quality:0  Signal level:0  Noise level:0
   
       Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0




Contents of /etc/network/interfaces


auto lo

iface lo inet loopback



auto wlan0

iface wlan0 inet dhcp

wireless-essid (id here)
wireless-key (key here)




mark@mark-desktop:~$ iwlist scan

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wmaster0  Interface doesn't support scanning.


wlan0     No scan results

---

### Post by wieman01 on 2007-11-05
Oh oh... I begin to suspect that you have removed the hardware driver. Please also post these:
> lshw -C network
> sudo gedit /etc/modprobe.d/blacklist
> sudo gedit /etc/modules
Have you had these problems only after upgrading to Gutsy?

---

### Post by Mark457658946 on 2007-11-05
Yea i think that may be a possibility. I didn't experience such a problem on Feisty, but I only used it for a week or so before I upgraded so I didn't really use the net too much. Is it possible that I loaded the wrong driver by mistake?

mark@mark-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0d:87:47:e2:37
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:d8:04:b8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g


Contents of/etc/modprobe.d/blacklist
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


Contents of /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

---

### Post by wieman01 on 2007-11-05
Gutsy might be the culprit. Other uses have had similar issues with Ralink based cards after upgrading. 

Is the LED lit?

---

### Post by Mark457658946 on 2007-11-05
Yea the LED is lit up, seems odd that its just today that I've starting messing around with stuff that I have been unable to connect. Before today a computer restart would reconnect me :s

---

### Post by wieman01 on 2007-11-05
When you add these to "/etc/network/interfaces" and restart the computer, what happens?
> auto wmaster0
iface wmaster0 inet dhcp

Can you then connect through Network Manager?

---

### Post by Mark457658946 on 2007-11-05
Still no use, iwconfig says there is no wireless extentions for wmaster0. I'm thinking of reverting back to Feisty for a bit while I look into it.

---

### Post by wieman01 on 2007-11-05
I found another guide for you that you might try (next to the one in my signature if everything else fails):

[http://ubuntuforums.org/showthread.php?t=502526]("http://ubuntuforums.org/showthread.php?t=502526")

---

### Post by wieman01 on 2007-11-05
> **Mark457658946 said:**
> Still no use, iwconfig says there is no wireless extentions for wmaster0. I'm thinking of reverting back to Feisty for a bit while I look into it.
Ralink drivers have been pretty erratic these days. No idea what's going on again.

---

### Post by Mark457658946 on 2007-11-05
Thanks for your efforts, much appreciated. I'm going to install a fresh copy of Gutsy which should hopefully get my wireless up and running again and compare various command outputs to try and find what's different.

---


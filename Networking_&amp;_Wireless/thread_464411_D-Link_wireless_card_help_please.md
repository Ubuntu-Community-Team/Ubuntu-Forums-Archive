---
title: "D-Link wireless card help please"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by molsen on 2007-06-04
xubuntu 7.04

trying to get wireless PC card for laptop to work

i typed:
```
sudo ksgw -C network
```

and it returned (excluding the network card):

```
*-network UNCLAIMED
description: Ethernet controller
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
businfo: PCI@05:00.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0 maxlatency=64 mingnt=32
resources: iomemory:40000000-40000lff irq:11
```

where in the world do i go from here to get this thing working? card is D-Link DWL-650

i have linux-restricted-modules-2.6.20-15-generic installed already and have a couple different network setup managers ready to assist.  i just need the dang hardware to work!  the light's on the card aren't even on

---

### Post by molsen on 2007-06-04
argghghh i downloaded that windows wireless drivers utility and imported the .inf file from the DWL-650 drivers package and that didn't work.  it doesn't show up as installed but when i try it again it says "Driver **driver** is already installed"

i thought this was supposed to be a plug-n-play device on this OS?  what am i missing?  what am i doing wrong?

---

### Post by molsen on 2007-06-04
k i tried ndiswrapper with the RTL8180 chipset driver

```
sudo ndiswrapper -i /home/matt/RTL8180.INF
```
k, but...
```
sudo ndiswrapper -l 
```
returns
```
dwl650: invalid driver!
net8180: invalid driver!
```

so wtf?  someone PLEASE help

---

### Post by molsen on 2007-06-06
anyone?  other people seem to be able to get their DWL-650's to work, but i've tried the same things and cannot get mine to

---

### Post by tturrisi on 2007-06-06
open a root terminal
cd to /usr/src

```

apt-get --purge remove ndiswrapper
apt-get install kernel-headers-`uname -r`
apt-get install build-essential
wget http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz
wget http://patches.aircrack-ng.org/rtl8180-0.21v2.patch
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180
```
this will also enable the card to work w/ aircrack-ng!

---

### Post by molsen on 2007-06-07
i only got this far:

```
matt@matt-laptop:/usr/src$ sudo apt-get install kernel-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-headers-2.6.20-16-generic

```

?????

same thing with the 2.6.20-15 kernel

---

### Post by tturrisi on 2007-06-07
oops, do:

```
apt-get install build-essential linux-headers-`uname -r` module-assistant
wget http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz
wget http://patches.aircrack-ng.org/rtl8180-0.21v2.patch
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180

```

---

### Post by molsen on 2007-06-07
nevermind, i tried ndiswrapper again and i got it.  i never read anywhere that instead of just the .inf file, you need the .sys file too for the driver to install.

it works now

---

### Post by netstat on 2007-06-09
apt-get --purge remove ndiswrapper
apt-get install kernel-headers-`uname -r`
apt-get install build-essential
wget [http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz)
wget [http://patches.aircrack-ng.org/rtl8180-0.21v2.patch](http://patches.aircrack-ng.org/rtl8180-0.21v2.patch)
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180

ndiswrapper didn't work for me, it constantly reported "invalid driver". This worked at once for me! Thanks! 

I also had problem with a PCMCIA Trendnet (broadcom chipset) wifi card. I found this solution on the forums which solved it! 


" sudo aptitude install bcm43xx-fwcutter
  fwcutter asks if you would like it to extract the firmware as part of the setup. Say yes.   

  After this type: 
  sudo modprobe bcm43xx
  Unplug you Wired connection, wait 30-60 seconds and then enjoy wireless using network      manager by the clock. "

I lost the link to where the post originally was but whoever wrote it well done it worked very well too! :D

---


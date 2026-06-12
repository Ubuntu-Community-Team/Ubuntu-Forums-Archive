---
title: "Broadcom BCM4306"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by ibrahim4 on 2013-10-05
I have a BCM4306 Wiereless card driver issue and I have been trying all day wipe the old drivers and set up the right ones and things are still not working. 
 
her is what I get when I type in **lspci -nnk | grep -iA2 net**
0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f8]
    Kernel driver in use: b43-pci-bridge

now I think the right driver for me is in the right driver for me are in the two packages calle** b43fwcutter** and** firmware-b43legacy-instaler. **

What I do not know is 
#1 how to get the right kernel deiver from b43-pci-bridge to change to b43fwcutter. 
#2 If this is what I need to do to fix the problum.
#3 Maybe wipe the diver somehow and start over? 
#4 If I have been wasting my time and just need to go get a wierless card. 

Anyway I would relay like some help with this.

Also when I run sudo apt-get install linux-firmware-nonfree 

I get the following errors 

The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 98 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/


 I am bran new to all this stuff and doing my best to get through it but struggling. 
I went to another page and tried some of there suggestions and this is the stuff I got back

[FONT=monospace]_**cat /etc/lsb-release; uname -a**_[/FONT]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

Linux ibrahim-Pavilion-zd8000-PD726AV-ABA 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux

[FONT=monospace]_**lspci -nnk | grep -iA2 net**_[/FONT]
0b:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Kernel driver in use: 8139too
--
0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f8]
    Kernel driver in use: b43-pci-bridge
[FONT=monospace]
_**lsusb**_[/FONT]
Bus 005 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

**rfkill list all**
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**lsmodsudo su**
lsmodsudo: command not found

**/etc/modprobe.d/blacklist.conf**
bash: /etc/modprobe.d/blacklist.conf: Permission denied
 exit^C

I don't know if I am even on the right track hear and I would like some help if anyone has some ideas.
thanks

---

### Post by Kevin McCready on 2013-10-06
Here is cut and paste from my database when I had same problem. I'm not really all that technical but learnt to use the terminal and follow a linux recipe. So I have little idea of what these instructions really mean.
Good luck.

to try to get wireless card working
STA driver must be removed. In a terminal run
Code:
sudo apt-get remove bcmwl-kernel source
put your driver on desktop
sudo mkdir /lib/firmware/<your modem>
sudo cp Desktop/b43/* /lib/firmware/<your modem>
sudo rmmod -f <your modem>
sudo rmmod -f ssb
sudo modprobe <your modem>
don't reboot until wireless working
I found I also needed to delete the bcmwl-kernel-source package and now it works great! Can't thank you enough!

---

### Post by varunendra on 2013-10-06
First of all, Welcome to the forums Ibrahim !

Let's answer your questions first -

Your card -
```
0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (**rev [COLOR="#FF0000"]03[/COLOR]**)
```
..is supported by the native b43 driver which is already present in the system. However, it needs a suitable proprietary firmware to work.

> **ibrahim4 said:**
> now I think the right driver for me is in the right driver for me are in the two packages calle** b43fwcutter** and** firmware-b43legacy-instaler. **
Just so you know, those packages are not drivers. Those are only helper packages that download and install correct **firmware** for the **b43** driver. Now the b43legacy firmware is meant for [COLOR="#FF0000"]revision 2[/COLOR] of this card, while yours is **[COLOR="#FF0000"]rev 3[/COLOR]**. So the legacy firmware won't work with it.

> What I do not know is 
#1 how to get the right kernel deiver from b43-pci-bridge to change to b43fwcutter. 
#2 If this is what I need to do to fix the problum.
#3 Maybe wipe the diver somehow and start over? 
#4 If I have been wasting my time and just need to go get a wierless card.
#1 Like I said, you already have the correct driver available and loaded, only firmware is needed.

#2 You need to install either "firmware-b43-installer" (along with b43fwcutter) or "linux-firmware-nonfree" package, latter of which you tried, but with a minor mistake..

#3 Not needed.

#4 Should not be needed. This card works nicely, as much as I have seen here.

> E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
This error indicates there was probably another package manager open at the time of execution. If you have Ubuntu Software Center, or Synaptic opened, please close it first. Let only the terminal open. Then, while being connected to internet, please do -
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv b43
sudo modprobe -v b43
```
If only the terminal is open, and still you get the above error, something else is wrong, post back and we'll fix it.

---

### Post by ibrahim4 on 2013-10-07
Hey Thanks so much My WiFi works just fine with the Broadcom now. Thanks!

---

### Post by Bucky Ball on 2013-10-07
varunendra to the rescue again. ;)

Good news and please mark thread as solved from Thread Tools to help others. Enjoy!

---

### Post by varunendra on 2013-10-07
/me lovez the sound of 'Solved' :P

---

### Post by Kevin McCready on 2013-10-08
impressive Varun!

---

### Post by varunendra on 2013-10-08
> **Kevin McCready said:**
> impressive Varun!
Thanks! It comes naturally after a certain level of madness :P

---


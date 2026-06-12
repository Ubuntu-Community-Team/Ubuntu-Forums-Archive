---
title: "Sitecome WL-012 and Hardy"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by ruggig on 2008-05-19
Hello everybody, I need help configuring my usb wireless adapter.
First of all, I'm a newbie and I guess I could have done some mistakes following [that guide]("http://ubuntuforums.org/showthread.php?t=121393") I've found, so I'll explain here what happened step by step.

I plugged in the USB and the green led is off.
I opened synaptic, marked for installation linux-wlan-ng (0.28) and applied.
After the linux-wlan-ng was installed, I rebooted the PC.

Led status: off.

So I asked myself even if ubuntu was knowing about the plugged adapter and I asked to show me the list of plugged usb:

```
lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 003 Device 002: ID 046d:c30a Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
**Bus 002 Device 007: ID 09aa:3642 Intersil Corp. Prism 2.x 802.11b Adapter**
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Yes it is loaded. But still led is off.

Next step:
> (2) The prism drivers are already included in the 2.6.12 kernel and you won't have to build a new kernel. Check with lsmod and you should see the prism2_usb module (The card must be plugged in).

This is the complete list:
> 
**prism2_usb             75908  0 **
**p80211                 33160  1 prism2_usb**
usbcore               146028  5 **prism2_usb**,usbhid,ehci_hcd,uhci_hcd

Yes it is, or at least, I guess so...

Next step...
> 3) After installing the linux-wlan-ng package you find /etc/modutils/linux-wlan-ng which defines the aliases that identify the wlan0 interface with the prism driver. For the Sitecom WL-012, uncomment

alias wlan0 prism2_usb

The device needs to be reset when the driver is loaded. Enter a line

options prism2_usb prism2_doreset=1

before the alias command above. The linux-wlan-ng package is not yet fully adapted to the 2.6 kernel, but to the 2.4 kernel. The 2.4 kernel uses /etc/modutils, while the 2.6 kernel wants the /etc/modprobe.d directory. To make Ubuntu find the alias, do

cp /etc/modutils/linux-wlan-ng /etc/modprobe.d/linux-wlan-ng.modprobe

Ok, Hardy is using >2.6 so because /etc/modutils/ was empty I did

> sudo nano /etc/modprobe.d/linux-wlan-ng

The alias wlan0 prism2_usb was already uncommented so I simply added to the end of file: options prism2_usb prism2_doreset=1
And saved.

Then I tried to do *cp /etc/modutils/linux-wlan-ng /etc/modprobe.d/linux-wlan-ng.modprobe* but I couldn't (linux-wlan-ng doesn't exists in /etc/modutils.. remember the folder was empty?)

Ok so I skipped this part and tried to follow the next step..

> Now go to /etc/network/interface and configure the wlan0 interface. Enter

auto wlan0
iface wlan0 inet dhcp
pre-up /etc/init.d/wlan start
post-down /etc/init.d/wlan stop

There's no folder named interface in /etc/network/ so what do I need to do now?

Thanks, I hope at least one of you can waste his time to help me :D
I apologise with you if I made any mistakes in this post... Any help is appreciated! :)

---

### Post by chili555 on 2008-05-19
interface**s**, /etc/network/interfaces is the file you want. Also, remember you are *adding* to wlan0. Please leave lo and eth0 alone. You can safely comment out any other interfaces, such as eth1, ath0, wifi99, etc. Comment out means make it look like:```
#auto eth2
#iface eth2 inet dhcp
```Items that are commented out are disregarded. The purpose of commenting out is two-fold: first, while booting, you won't waste time trying to connect eth1 (sorry, doesn't exist), ath0 (sorry, doesn't exist), wifi0 (sorry, doesn't exist), etc. Second, if you comment out a line in any file, you can go back later and see what you changed in case you need to undo the change.

---


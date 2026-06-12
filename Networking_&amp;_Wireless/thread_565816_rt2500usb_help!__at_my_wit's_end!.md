---
title: "rt2500usb help!  at my wit's end!"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by molsen on 2007-10-02
Zonet DEW2500P usb wireless network adapter
Ubuntu 7.04

i've searched and searched and searched and have tried various methods for getting this to work, but i am still unable to get my adapter to connect to any wireless networks, protected or not.

i don't know what else to try.  the driver installed fine with ndis-wrapper and the device is detected and turned on, it just won't connect to any networks.

where do i go from here?

---

### Post by Lambert on 2007-10-02
> **molsen said:**
> Zonet DEW2500P usb wireless network adapter
Ubuntu 7.04

i've searched and searched and searched and have tried various methods for getting this to work, but i am still unable to get my adapter to connect to any wireless networks, protected or not.

i don't know what else to try.  the driver installed fine with ndis-wrapper and the device is detected and turned on, it just won't connect to any networks.

where do i go from here?

When you say the driver installed fine with ndiswrapper, did you blacklist the native driver? It's possible there are two loaded drivers for the device and causing a conflict.

if you open up a terminal window, what is the output of this

```

lsmod

```

If you see a line labeled rt2500 and a line labeled ndiswrapper then you need to unload one of these modules and try to connect then.

to remove a module, in terminal run this command

```

sudo modprobe -r ndiswrapper

```

---

### Post by molsen on 2007-10-02
there's a line labeled ndiswrapper and one labeled rt2570, but not rt2500

i ran the command, but am still unable to connect

i checked the installed drivers again with sudo ndiswrapper -l and got
```
matt@matt-desktop:~$ sudo ndiswrapper -l
rt2500usb : driver installed
        device (148F:2570) present (alternate driver: rt2570)

```

what else can i check?

---

### Post by kevdog on 2007-10-02
blacklist the rt2570 driver

echo "blacklist rt2570" | sudo tee -a /etc/modules
sudo modprobe -r rt2570

Reload the ndiswrapper driver
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

Restart the networking bus (among other things)
sudo /etc/init.d/dbus restart

Any signal at this point?

---

### Post by molsen on 2007-10-02
```
matt@matt-desktop:~$ echo "blacklist rt2570" | sudo tee -a /etc/modules
Password:
blacklist rt2570
matt@matt-desktop:~$ sudo modprobe -r rt2570
FATAL: Module rt2570 is in use.
matt@matt-desktop:~$ sudo modprobe -r ndiswrapper
matt@matt-desktop:~$ sudo modprobe ndiswrapper
matt@matt-desktop:~$ sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 

```

i have signals of all the wireless networks within range, but it still won't connect.  none of the little green circles light up either.  it just attempts to connect for a while then reverts to the wired connection.  i know the card works and the network is up...so what gives?

---

### Post by kevdog on 2007-10-02
Dont run the wired and wireless connections at the same time -- you will have a problem.

---

### Post by molsen on 2007-10-02
even if i completely disable the wired connection, i can't seem to connect to the wireless networks.  it shows the step-looking bars but i get no active internet connection.

also, when i right-click and goto "connection information" it shows the driver being used is the rt2570.  i thought i needed to use the rt2500, which i installed with ndis-wrapper?

---

### Post by kevdog on 2007-10-02
Can you post the following:

modinfo rt2570
lsmod | grep 2570

Did you blacklist the 2570 driver and then reboot??

You tried to unload the module previously, but from what you posted it stated the driver was in use.

Again I think a reboot with the appropriate blacklist statement should work, however if not you can do the  following:

sudo ifconfig <interface_name like wlan0 or eth1> down
sudo modprobe -r rt2570
sudo modprobe -r ndiswrapper
sudo modprobe ndiswraper
sudo ifconfig <interface_name> up

Then repost
lshw -C network

---

### Post by Lambert on 2007-10-02
removed text, kevdog's post has it write, mine was duplicate

---

### Post by molsen on 2007-10-03
```
matt@matt-desktop:~$ modinfo rt2570
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko
license:        GPL
author:         http://rt2x00.sourceforge.net
description:    Ralink RT2570 usb 802.11g WLAN driver 1.0.0 - BETA2 2006/06/18
srcversion:     B24EA88A25D2DD1B4B04C16
alias:          usb:v0EB0p9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p008Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14F8p2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0066d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)

```

```
matt@matt-desktop:~$ lsmod | grep 2570
rt2570                186432  1 
usbcore               134280  10 ndiswrapper,rt2570,snd_usb_audio,snd_usb_lib,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd

```

i went through the sudo commands you listed, but when i got to "sudo ifconfig rausb1 up", it returned "rausb1: ERROR while getting interface flags: No such device"

and here's...```
matt@matt-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: rausb0
       serial: 00:06:f4:0e:15:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Ralink,05/27/2004, 1.00.01.0000 multicast=yes wireless=IEEE 802.11g

```

but the good news is now it is WORKING!!!  are the changes made tonight permanent?  thanks so much!!!!!

---

### Post by kevdog on 2007-10-03
If you have the rt2570 module blacklisted in the /etc/modprobe.d/blacklist file the changes should be permanent. 

I noticed that your interface was assigned rausb0 and not rausb1, thats why the up statement with rausb1 did not work.

---

### Post by molsen on 2007-10-03
yea, it WAS rausb1, but i switched usb ports for diagnostic reasons.  it's back in rausb1 and i made sure rt2570 is permanantly blacklisted, but the wireless isn't working again now

-EDIT- alright, i think i have i sorted out now.  

now to figure out how to get it to automatically connect to my preferred network on boot-up.  seeeeaaarrrchchhh

---

### Post by kevdog on 2007-10-03
You also have to make sure the ndiswrapper module is automatically loaded on boot with it listed in /etc/modules.

If it isnt then you need to do:
echo ndiswrapper | sudo tee -a /etc/modules

Im not sure if network manager can connect automatically to a preferred network.  I know wicd can (its a network manager alternative).

---


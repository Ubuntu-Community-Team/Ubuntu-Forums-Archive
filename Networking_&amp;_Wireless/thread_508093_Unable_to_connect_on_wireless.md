---
title: "Unable to connect on wireless"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by vendingmachine on 2007-07-23
I'm running a Linksys WUSB54GC on my desktop computer, the wireless network is detected, but I am unable to connect.  It has a 10-digit WEP key on it, which I put in exactly as on Windows, but I am still unable to connect.  Please excuse me if I left out any relevant information.

---

### Post by p110011 on 2007-07-23
If you're using 7.04 Feisty Fawn I don't think it will work, I have one of those and never found anyone else able to get one going either.

I had it going using 6.10 but had to manually compile the driver.

I'm using a D-link pci card that works flawlessly.

---

### Post by kevdog on 2007-07-23
You are going to have to do some homework for me.  I believe the Linksys WUSB54GC contains an rt2500 chipset.  Couple ways of checking

Post output of following command:
lshw -C network (probably wont work)

Find the version of the USB dongle you are using, I believe there are version 1 through 4.  Then you are going to have to google around

The command: lsusb
might help with the google search, but it wont give you the answer.

---

### Post by vendingmachine on 2007-07-25
Output of lshw -C network:

       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:70:38:47:c1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Output of lsusb:

       Bus 001 Device 002: ID 13b1:0020 Linksys 

Will keep looking for the other info.

---

### Post by p110011 on 2007-07-25
The WUSB54G is labeled ver. 1 through 4 shown on the dongle itself. [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2751723093B16](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2751723093B16)
If you have WUSB54GC, this is the one that I can't find help with and I now use a pci unit. [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1134691790190&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9019023093B17](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1134691790190&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9019023093B17)

---

### Post by kevdog on 2007-07-25
For the uSB device, I think it uses the rt73 chipset from what I could find on google.  You will need to install serial monkey drivers.  This is a general guide, however you need to be aware that you are installing the rt73 drivers

Installation Instructions:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

Serial Monkey site:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

---

### Post by vendingmachine on 2007-07-25
To p110011: yes, I am using the compact WUSB54GC.

To kevdog: I followed the tutorial you linked to, but after blacklisting the old modules and loading the new module, when I performed the command

sudo ifconfig wlan0 up

, it said it was unable to find the device.  I typed sudo ifconfig, and only my motherboard's ethernet ports were listed in the readout.

---

### Post by kevdog on 2007-07-25
I can see that your device is not associated with any driver, thats why it is saying device not found.  Lets just check to see if the module is loaded

sudo modprobe -l rt73
modinfo rt73

Can you post your /etc/modprobe.d/blacklist file?

---

### Post by vendingmachine on 2007-07-25
sudo modprobe -l rt73:

/lib/modules/2.6.20-15-generic/extra/rt73.ko

modinfo rt73:

/lib/modules/2.6.20-15-generic/extra/rt73.ko
license:        GPL
description:    Ralink RT73 802.11abg WLAN Driver 1.0.3.6 CVS 2007072511
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     72CF115161B212940D46C85
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           firmName:Permit to load a different firmware: (default: rt73.bin)  (charp)

/etc/modprobe.d/blacklist:




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

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

---

### Post by kevdog on 2007-07-25
Ok everything looks good there, lets verify the module is associated with your card:
lshw -C network

and the module is actually loaded
lsmod | grep rt73

You for now turned off all WEP/WPA/MAC filtering correct?

---

### Post by vendingmachine on 2007-07-25
lshw -C network

  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN


lsmod | grep rt73
rt73usb                33536  0 
rt2x00lib              11904  1 rt73usb
mac80211              175364  2 rt73usb,rt2x00lib
crc_itu_t               3072  1 rt73usb
rt73                  213888  0 
usbcore               134280  9 ndiswrapper,rt73usb,rt73,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

I do not have physical access to the router at the moment to turn off the encryption.  However, when I saw the logical name from the lshw -C network command as "wlan1", I realized when I tried activating the device before that I used "wlan0", as that was the name before I installed the new driver.  So I attempted the process again using the correct name:

sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:1a:70:38:47:c1
Sending on   LPF/wlan1/00:1a:70:38:47:c1
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.100 -- renewal in 32765 seconds.

---

### Post by kevdog on 2007-07-25
Until their is a driver associated with your interface, configuring the interface is not going to work.  A lot of strange results came up with your last statment of lsmod:

rt2x00lib 11904 1 rt73usb
mac80211 175364 2 rt73usb,rt2x00lib
crc_itu_t 3072 1 rt73usb
rt73 213888 0
usbcore 134280 9 ndiswrapper,rt73usb,rt73,usbhid,usb_storage,libusu al,ehci_hcd,ohci_hcd

I didnt thing rt2x00lib, rt73usb would come up.  I think this may be part of the problem.  Have you physically unloaded this modules from the kernel like:

sudo modprobe -r rt73usb
sudo modprobe -r rt2x00lib

Do the above and then reboot, and then relist lsmod | grep rt.  I want to confirm no other conflicting modules are loading.

---

### Post by vendingmachine on 2007-07-25
I was able to get a successful connection, I'm typing this response from the wireless network.   Even though I have rt73usb and rt2x00 blacklisted, they were loading on startup anyway, even after I removed them and rebooted.  So I removed them this last time, went ahead and did the sudo dhclient, and it took me two tries, but it connected.

---

### Post by kevdog on 2007-07-25
Keep me posted if you have problems in the future.  I dont understand if you blacklist and rmmod them, how they can show up with lsmod.  That's just plain goofy.  I guess you could go one extra step, and physically find the ****.ko files and rename them.

---

### Post by vendingmachine on 2007-07-26
This isn't a problem, just continued quirkiness.. I followed the next part in the tutorial to have the device automatically set itself for each boot, and when I rebooted, everything connected and came up fine... but now the rt73usb and rt2x00lib modules are still there, and not conflicting apparently.

---

### Post by Albaraha on 2007-07-31
Any listed steps to follow would be grateful.
I'm struggling to get my **_Linksys Wireless-G USB Adpater WUSB54GC_** to work.

---


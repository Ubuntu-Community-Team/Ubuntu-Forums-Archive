---
title: "Broadcom 4306 wireless card dissappeared after hardy kernel upgrade"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by mxgods on 2008-06-16
Ran through all the bcm43xx-fwcutter steps and had wireless working in kernel 2.6.24-16.  I did an upgrade to 2.6.24-18 and now my wireless card does not show up at all.  when i do an lspci it shows up, but thats it.  if i go back to my previous kernel, it works fine, just not in this kernel.  My card is a broadcom bcm4306 (rev 3)

---

### Post by Ayuthia on 2008-06-16
> **mxgods said:**
> Ran through all the bcm43xx-fwcutter steps and had wireless working in kernel 2.6.24-16.  I did an upgrade to 2.6.24-18 and now my wireless card does not show up at all.  when i do an lspci it shows up, but thats it.  if i go back to my previous kernel, it works fine, just not in this kernel.  My card is a broadcom bcm4306 (rev 3)
Can you post your lshw -C network in 2.6.24-18?  Also, what happens when you do the following:
```
sudo modprobe -r b43 ssb
sudo depmod -ae 
sudo modprobe b43
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwlist scan
```
Does any wireless sites show up?  I have had similar problems with 2.6.24-18 with my 4311 card (works now with 2.6.24-19), but I am going to update my laptop with the 4306 card tonight and see what happens.

---

### Post by mxgods on 2008-06-16
here is what happened after i ran all those commands, my wireless cad is now visible but no wireless networks show up.

rich@rich-laptop:~$ sudo modprobe -r b43 ssb
[sudo] password for rich: 
rich@rich-laptop:~$ sudo depmod -ae
rich@rich-laptop:~$ sudo modprobe b43
rich@rich-laptop:~$ sudo ifconfig wlan0 up
rich@rich-laptop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:5b:61:55
Sending on   LPF/wlan0/00:90:4b:5b:61:55
Sending on   Socket/fallback
rich@rich-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

rich@rich-laptop:~$ 
rich@rich-laptop:~$ 

rich@rich-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:04:4f:bc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.30.10.108 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:5b:61:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
rich@rich-laptop:~$

---

### Post by Ayuthia on 2008-06-16
That all looks fine except for the part about not seeing any wireless.  I will go ahead and try to get mine updated.  It will take me a little over three hours because I am on dialup.  I'll let you know what happens.

---

### Post by mxgods on 2008-06-17
Just for an update, I did an upgrade to the 2.6.24-19 kernel last night and then uninstalled and reinstalled the fwcutter driver and still nothing.  I also reran all the steps you gave me before and still the same thing, but after i reboot my wireless card doesnt show up again.  It only shows up if i run the steps you gave me.

---

### Post by dmizer on 2008-06-17
> **mxgods said:**
> Just for an update, I did an upgrade to the 2.6.24-19 kernel last night and then uninstalled and reinstalled the fwcutter driver and still nothing.  I also reran all the steps you gave me before and still the same thing, but after i reboot my wireless card doesnt show up again.  It only shows up if i run the steps you gave me.
edit the file /etc/rc.local so it looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r b43 ssb
depmod -ae 
modprobe b43
ifconfig wlan0 up
exit 0
```

---

### Post by mxgods on 2008-06-17
Ok, i did that and now my wireless card shows up at boot, but it still sees no wireless networks.  Is that driver that it is using the b43xx-fwcutter driver?

---

### Post by dmizer on 2008-06-17
okay ... according to this thread:
[http://ubuntuforums.org/showthread.php?t=773994](http://ubuntuforums.org/showthread.php?t=773994)
this howto works:
[http://ubuntuforums.org/showthread.php?t=767372](http://ubuntuforums.org/showthread.php?t=767372)

---

### Post by mxgods on 2008-06-17
That didnt work, i dont know if it is still using the fwcutter driver, i had it working using that and i have allready ran the install for fwcutter manytimes and it doesnt change anything.  How do i know im using the fwcutter driver?

---

### Post by Ayuthia on 2008-06-17
> **mxgods said:**
> That didnt work, i dont know if it is still using the fwcutter driver, i had it working using that and i have allready ran the install for fwcutter manytimes and it doesnt change anything.  How do i know im using the fwcutter driver?
I just updated my Dell laptop (the one with the 4306 card) and it had no problems.

If you want to see if you are using the fwcutter driver, check:
```
lshw -C network
```
Look for the driver in there.  It should say b43-pci-bridge or something like that.  The card should not be UNCLAIMED or DISABLED.

You will also need to check and see what modules are loaded:
```
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
```
It should only have b43 and ssb out there.

To reload the modules to get it back to the b43 state:
```
sudo modprobe -r b43 ssb
sudo depmod -ae 
sudo modprobe b43
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
sudo iwlist scan
```

---

### Post by mxgods on 2008-06-17
My driver name was just the standard driver then, i will reinstall it again tonight, i forgot to bring the cd with me to work today.

---

### Post by mivo on 2008-06-17
Start here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)   Note the recommended repository at [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) - that should automate everything.

---

### Post by mxgods on 2008-06-17
I did all that and it still didnt work, but like i said i dont have the cd and the b43-fwcutter is on the cd and it is currently not on my laptop.  So i will try that and hopefully that will fix things.

---

### Post by mivo on 2008-06-17
The Cafuego repository has the firmware, so no need for the fwcutter. (If you tried this method already, sorry, missed it!)

---

### Post by mxgods on 2008-06-17
yeah i installed the firmware adn still nothing is showing up...its just funny that kernel 16 still works, just nothing else after that.

---

### Post by mxgods on 2008-06-17
Ok, here is a good one.  The laptop im using is a Compaq R3000.  There is a hardware turn on and off button on the front corner of this laptop.  It doesnt work in both linux and windows.  Somehow in the newer kernels, this got shut off.  I had to boot up in windows (which i rarely do) and it wasnt working in there either.  I reinstalled the wireless driver that came with this laptop.  Once i did that, it started working in windows (hence, the hardware switch was turned on).  I rebooted into linux and then everything worked great.  One note i do have with the b43 driver problem, there is someone that wrote this program, they call it toolbox 0.0.1 and that is a gui app that does all the driver work for you (including adding the hardware boot and the blacklisting).  If you need me to i can attach the tar of it.  It is in the forums somewhere just cant remember where i found it.

---


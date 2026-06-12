---
title: "blacklisting bcm43xx help"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by action_owl on 2008-08-22
Dear most humble linux gurus,
I am having quite the time trying to figure out how to get my WiFi working in Ubuntu. I have read  a lot of other forums that pertained to my Dell 1370 card and none of them have worked so figured I would try to tackle this battle one step at a time.

First Problem:
blacklisting bcm43xx:
I typed:
“sudo modprobe -r bcm43xx”
in terminal and nothing happens...it just takes me to a new line.
So I restart, then in terminal I type:
“lsmod | grep bcm”
once again just goes to a newline
then I type:
 “modprobe -l | grep bcm43 ”
and get the following:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

so is bcm43xx blacklisted?

i am using Ubuntu 8.04.1
thanks!

---

### Post by spd106 on 2008-08-23
The modprobe -l command just lists all of the available kernel modules, not just those that are currently loaded.

If the driver is listed in the /etc/modprobe.d/blacklist file then it won't be loaded automatically, you would have to load it manually. As you are running 8.04.1 bcm43xx should be blacklisted due to being replaced by b43 and b43-legacy. So if you are trying to use ndiswrapper then you will need to blacklist these too.

lsmod will tell you which modules are currently loaded and you see which driver is being used by your wifi interface by running the following command.
```
$ sudo lshw -class network
```

In my case I am using b43 and I have the following line in the output.
```
configuration: driver=b43-pci-bridge latency=32 module=ssb
```

---

### Post by Flag on 2008-08-23
Understand your problem, you're not the first to struggle with it.
What worked for me is use ndiswrapper plus madwifi / MS drivers, ndiswrapper either handymatic or through ndisgtk.


Luck

---

### Post by action_owl on 2008-08-23
Super Thanks spd106, its making more sense to me now, But I might still have an issue.

I ran:
sudo lshw -class network:
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a4:f2:ad:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I blacklisted the b43 and b43legacy by typing in the blacklist file:
blacklist b43
blacklist b43-legacy

I also tried:
blacklist b43
blacklist b43legacy

I restarted every time I changed it

I rebooted and ran sudo lshw -class network:
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ef:f0:d2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=192.168.0.1 latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

the good news is that the network descriptions makes more sense than before the files were added to the blacklist but it still shows:
 
configuration: driver=b43-pci-bridge latency=64 module=ssb

my blacklist file now looks like this:

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

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# conlicts with wifi stuffs
blacklist b43
blacklist b43legacy


should I go ahead with installing the new Wireless driver with NDISWRAPPER or do I need to do more to blacklist the other drivers? what about module=ssb?

---

### Post by spd106 on 2008-08-25
You should be ok to go on and install ndiswrapper now.

I wouldn't blacklist ssb if I were you, because your wired nic needs it.

---

### Post by namopereht on 2008-08-25
I seem to remember there was a problem that the Broadcom 43xx cards are being improperly handled by the module ssb, and would not let go of the card to ndiswrapper. I am running a bcm4318 on Kubuntu 8.04 and kept having the same problems. I uninstalled ndiswrapper and just used the restricted drivers and all works perfect. Only problem is the hardware light no longer just shows on/off/searching by its flashes, but off while hardware off, on while searching, and flashing like an activity light while connected. I don't know how this would be done in gnome, but in KDE I just enabled the driver in "hardware drivers" in the programs menu. 

namopereht

---


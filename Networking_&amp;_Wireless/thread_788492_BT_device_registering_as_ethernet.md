---
title: "BT device registering as ethernet"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by BallsOfSteel on 2008-05-09
Hey,

I'm having a problem with a bluetooth dongle that is registering as an ethernet device.  It's some Belkin BT adapter that I paid $40 for a while back.  This has worked under other OS's, but with a little hacking.  Under Fedora 8, I had to add 'pegasus' to the blacklist file under /etc/modprobe.d/blacklist.  After that, the dongle worked perfectly.  

Under Hardy Heron, the device doesn't work.  At first when I plugged it in, the light would go on, but no BT logo would pop up on the top panel in the notification area.  I tried scanning with hcitool, but nothing would happen and it would say that no device was present.   I tried adding 'pegasus' to the blacklist file, rebooting, but STILL nothing.  

When I try to run 'lsusb' it seems like it would freeze.  It would just sit there and do nothing.  I tried connecting it through a USB hub and I tried connecting it to a port directly on the motherboard.  With nothing else left to try, I hooked it up to my Mac keyboard that has two ports on there.  When I ran 'lsusb' it showed up as a 100mbps ethernet device.  Then, when I connected it to the computer itself again, it showed up as the same.  

Anyone have any ideas on what I can do?  Is there a known issue between Belkin BT adapters and Hardy Heron?  I remember using this device with Edgy Eft, and Fedora 8.  Not sure why it's not working here.  I've included copies of lsusb and my blacklist file...

lsusb: ```
elwood@elwood-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 011: ID 054c:0268 Sony Corp. 
Bus 002 Device 010: ID 050d:0121 Belkin Components F5D5050 100Mbps Ethernet
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 009: ID 0a5c:2120 Broadcom Corp. 
Bus 001 Device 008: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 007: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 005: ID 046e:556e Behavior Tech. Computer Corp. 
Bus 001 Device 004: ID 05ac:0204 Apple Computer, Inc. 
Bus 001 Device 003: ID 05ac:1002 Apple Computer, Inc. Apple Extended Keyboard Hub [Mitsumi]

```The Sony is my PS3 controller and the Broadcom is ANOTHER BT adapter that I've tried, but to no avail.

Blacklist:  ```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
blacklist pegasus

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

```

Thanks in advance,

Brandon

---

### Post by BallsOfSteel on 2008-05-10
I switched from 64-bit Ubuntu to 32-bit and my BT device worked perfectly after adding pegasus to the blacklist.

---


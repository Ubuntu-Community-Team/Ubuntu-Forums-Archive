---
title: "USB Internet Help"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by Drian42 on 2007-10-06
Hi,
I have ubuntu Gutsy Gibbon installed with XP on my desktop computer. This computer does not have an etherenet port so i connect to the internet using a USB Cable.  This works fine in XP but not in ubuntu... my modem is a D-Link DSL-302g. How do i connect to the internet using USB???
i have found some articles about this in the ubuntu documentation but it asks wether my modem is speedtouch, Connexant AccessRunner etc. How do i know???
Please Help! without the internet ubuntu is useless.
Thanks.

---

### Post by Lambert on 2007-10-07
With the device plugged in, open a terminal, type in the following command, and post output here.

```

sudo lshw -C bus

```

You will see all hardware that makes up the usb line. If you can pick the section just on the modem, post just that.

---

### Post by Drian42 on 2007-10-07
Thanks for your help. 
I couldn't find anything that i was sure was my modem so
Here is what appeared in the Terminal after i entered the code:

```
adrian@DESKTOP:~$ sudo lshw -C bus
  *-core                  
       description: Motherboard
       product: 85ERV
       vendor: SOLTEK
       physical id: 0
       version: 0
       serial: 00000000
       slot: PCI2
  *-firewire
       description: FireWire (IEEE 1394)
       product: IEEE 1394 Host Controller
       vendor: VIA Technologies, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 46
       width: 32 bits
       clock: 33MHz
       capabilities: pm ohci bus_master cap_list
       configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
  *-usb:0
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=32 module=uhci_hcd
  *-usb:1
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=32 module=uhci_hcd
  *-usb:2
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.2
       bus info: pci@0000:00:10.2
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=32 module=uhci_hcd
  *-usb:3
       description: USB Controller
       product: USB 2.0
       vendor: VIA Technologies, Inc.
       physical id: 10.3
       bus info: pci@0000:00:10.3
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: pm ehci bus_master cap_list
       configuration: driver=ehci_hcd latency=32 module=ehci_hcd
  *-ide:0
       description: IDE Channel 0
       physical id: 0
       bus info: ide@0
       logical name: ide0
       clock: 33MHz
  *-ide:1
       description: IDE Channel 1
       physical id: 1
       bus info: ide@1
       logical name: ide1
       clock: 33MHz

```
If it helps at all when i was installing ubuntu it came up with an error 'Could not find network hardware' or something like that.

---

### Post by Lambert on 2007-10-07
I'm not real familiar with adsl so i will have to provide a link and defer hoping someone else with more knowledge here can help you. Read through this link.

[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by Drian42 on 2007-10-07
Thanks again,
I have tried this and as i mentioned in my first post (i think) this is where i get stuck. It askd what driver i have > 
The first step towards getting a USB ADSL modem working is to identify exactly what type of modem you have. Depending on your modem type, you should follow the guide specific to the driver your modem needs.

To identify your modem, you should start by noting the make and model, which is usually printed on the front. Occasionaly you may have to look for a label to discover the exact model. You should then consult the list of USB ADSL modems to see which driver your modem requires, and if it can be made to work with Ubuntu. 
Ok now where is this 'list of USB ADSL modems'??? i can't find it anywhere! and without this i don't know what to do. I found somewhere that i had to find out what chipset or something my modem had and eventualy found that it has the Viking chipset or something... 
I don't realy understand any of this.
Please Help!

---

### Post by Drian42 on 2007-10-19
I just uppgraded to Ubuntu Gutsy Gibbon but the problem is still there- 
I can't connect to the internet! please help, ubuntu is useless without it!

---

### Post by StevenHarper on 2007-10-21
The USB Adsl Modem manager is now fixed for Gutsy 7.10

get it here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

read About it here

[http://www.squeezedonkey.com/wiki/linux](http://www.squeezedonkey.com/wiki/linux)

thanks

Steve

---

### Post by Drian42 on 2007-10-23
So should this fix my problem? the site sais that only 'SpeedTouch' modems are supported... is my modem one of these??
I'll install it on my Desktop and see if it works....

Thanks

---

### Post by Drian42 on 2007-11-08
Ok i tried that but my internet is STILL not working.
Can someone please help me???

---


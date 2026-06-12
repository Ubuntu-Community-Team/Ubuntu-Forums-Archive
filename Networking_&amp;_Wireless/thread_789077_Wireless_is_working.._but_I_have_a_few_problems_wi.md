---
title: "Wireless is working.. but I have a few problems with it.."
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-05-10
[b]EDIT:

Go here for RTL8187B wireless issues

[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

[/b]
______________________________________________


I have manually configured my wireless card but following this [here]("www.ubuntuforums.org/showthread.php?t=684495").]

My wireless card is rtl8187b with the stupid ID number, 8197 :@
But I can get it to work when modified the Windows98 driver.
(before anyone asks, my wireless switch is on :P)

I have got this in my /etc/rc.local:
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

ifconfig wlan1 down
dhclient -r wlan1
iwconfig wlan1 essid "linksys"
iwconfig wlan1 key open
iwconfig wlan1 key MY HEX KEY
iwconfig wlan1 key open
iwconfig wlan1 mode Managed
ifconfig wlan1 up
dhclient wlan1

exit 0
```

On start up, it connects to my wireless but does not connect to the internet. 
I can connect to my internet when I login by, in terminal:
```
sudo iwconfig wlan1 key MY HEX KEY (I need to wait a second or 2 before I put in the next line otherwise it will not connect to my wireless)
sudo iwconfig wlan1 key open
sudo dhclient wlan1

```
and it connects fine :) 

How do I get my wireless to connect up on start up? 

I was thinking of putting a delay of a second or 2 between these 2:
```
iwconfig wlan1 key MY HEX KEY
[[[[[Delay here]]]]
iwconfig wlan1 key open
```
Then, in theory wireless will connect to the router and the internet.
I do not know how to create a delay. Would it even be possible?


and another thing, 

Firefox likes to start in offline mode.. Why?
It only started when I stopped using nm-applet.
To come out of offline mode I need to go - File - Offline mode. 
Its just annoying to do it every time I open Firefox.

Finally, 

Before I used my internal wireless card, I had a usb one. That was wlan0 and my internal is wlan1. 
How do I get my internal one to wlan0?

O and my output of dmesg is this:

```
From the start of ndiswrapper:
[   35.334059] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   35.537919] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   35.765425] usb 7-6: reset high speed USB device using ehci_hcd and address 4
[   35.934237] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,02/08/2007,5.1063.0208.2007) loaded
[   36.365332] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04713/0x204000
[   36.400082] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   40.655050] wlan0: ethernet device 00:16:44:7f:24:22 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8197.F.conf
[   40.655080] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   40.655117] usbcore: registered new interface driver ndiswrapper
[   40.673089] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   40.673173] udev: renamed network interface wlan0 to wlan1
[   40.865642] lp: driver loaded but no devices found
[   41.524083] EXT3 FS on sda1, internal journal
[   43.390644] No dock devices found.
[   48.489911] ppdev: user-space parallel port driver
[   48.644080] audit(1210425753.947:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5488 profile="/usr/sbin/cupsd" namespace="default"
[   49.460558] [drm] Initialized drm 1.1.0 20060810
[   49.494081] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   49.494099] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.494215] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   49.583682] NET: Registered protocol family 17
[   49.719687] ndiswrapper (iw_set_wep:961): key 1 is not set
[   60.262974] NET: Registered protocol family 10
[   60.263565] lo: Disabled Privacy Extensions
[   68.439654] CPU0 attaching NULL sched-domain.
[   68.439662] CPU1 attaching NULL sched-domain.
[   68.469418] CPU0 attaching sched-domain:
[   68.469425]  domain 0: span 03
[   68.469427]   groups: 01 02
[   68.469431] CPU1 attaching sched-domain:
[   68.469433]  domain 0: span 03
[   68.469435]   groups: 02 01
[   71.084921] wlan1: no IPv6 routers present

```


Hope anyone can help me..



Thanks!
Tom

---

### Post by Tom--d on 2008-05-10
Anyone?

---

### Post by Ayuthia on 2008-05-10
> **Tom--d said:**
> I have manually configured my wireless card but following this [here]("www.ubuntuforums.org/showthread.php?t=684495").]

My wireless card is rtl8187b with the stupid ID number, 8197 :@
But I can get it to work when modified the Windows98 driver.
(before anyone asks, my wireless switch is on :P)

I have got this in my /etc/rc.local:
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

ifconfig wlan1 down
dhclient -r wlan1
iwconfig wlan1 essid "linksys"
iwconfig wlan1 key open
iwconfig wlan1 key MY HEX KEY
iwconfig wlan1 key open
iwconfig wlan1 mode Managed
ifconfig wlan1 up
dhclient wlan1

exit 0
```

On start up, it connects to my wireless but does not connect to the internet. 
I can connect to my internet when I login by, in terminal:
```
sudo iwconfig wlan1 key MY HEX KEY (I need to wait a second or 2 before I put in the next line otherwise it will not connect to my wireless)
sudo iwconfig wlan1 key open
sudo dhclient wlan1

```
and it connects fine :) 


I think that the problem might be with the order of turning on ifconfig.  I think you need to have that up before you do your iwconfig.  So maybe move ifconfig wlan1 up after dhclient -r wlan1.

> (before anyone asks, my wireless switch is on :P)
By the way is your wireless switch on???  Saw your message so I just had to ask.  :)

---

### Post by cevans on 2008-05-10
I agree with Ayuthia that the most likely problem here is with the order of commands, not any delay (dhclient can cope with delays anyway). There isn't really any need to have ifconfig wlan1 down or dhclient -r, though the latter *may* make the process a bit faster in certain cases, depending on the server. Many wireless drivers do require, however, that the interface be up before being configured, so ifconfig wlan1 up is very important, and should be before anything else.

Also, many of the commands you are using seem very redundant. Why not just use "iwconfig wlan1 enc open HEX KEY" instead of all the key and open commands? I'm note sure why you need to set Managed (it should probably be set automatically), but if you do, that should probably go right after bringing the interface up.

---

### Post by Tom--d on 2008-05-10
Thank you both for replying :) 

Right, taking in what you have said. This is what I have come up with:

```
ifconfig wlan1 up
dhclient -r wlan1
iwconfig wlan1 mode Managed
iwconfig wlan1 essid "linksys"
iwconfig wlan1 key MY_HEX_KEY open
dhclient wlan1
```

Would I need to edit any of that?

***Just rebooted and it worked :D:D:D:D***

Thank you both :)


But.. firefox likes to start in offline mode.. do you know why?

---

### Post by geezerone on 2008-09-15
> **Tom--d said:**
> ... firefox likes to start in offline mode.. do you know why?

Is it working now as typing about:config in a FF tab and then searching for toolkit.networkmanager.disable and set this is set to true should work.


A description of toolkit.networkmanager.disable is [here]("http://kb.mozillazine.org/Toolkit.networkmanager.disable").


HTH

---


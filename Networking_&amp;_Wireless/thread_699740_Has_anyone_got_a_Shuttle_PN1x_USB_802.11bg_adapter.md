---
title: "Has anyone got a Shuttle PN1x USB 802.11b/g adapter running with ndiswrapper?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by HyRax on 2008-02-17
Hi all,

I'm a recent convert to Ubuntu and have installed it on my PN11/15/18 (whatever it is)-equipped Shuttle XPC. Everything works bar the wireless.

Has anyone else got this working? So far I have followed the instructions given in _[this thread](http://ubuntuforums.org/showthread.php?t=31926)_ and also a handful of ndiswrapper-related hits in Google and have got to the point where the hardware IS recognised and the driver appears to be loaded, but I cannot see it under ifconfig or iwconfig.

Here's what I did. First up, I did an lsusb to identify the hardware. It comes up as "AirVast".

```

$ lsusb
Bus 003 Device 005: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
[color="red"]Bus 003 Device 004: ID 124a:4023 AirVast [/color]
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 003: ID 1310:0001 Roper Class 1 Bluetooth Dongle
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
$
```

Then I searched the ndiswrapper Sourceforge page for the ID 124a:4023 and found this (_[page reference](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)_):

```

   1.  Card: Iogear GWU513

    *   Chipset: Prism GT
    *   usbid: 124a:4023 (also 124a:4025)
    *   Driver: http://www.iogear.com/support/driver/GWU513_1203A.zip
    *   Other: Works fine with ndiswrapper-0.12rc1. Same usbid as Shuttle PN15 aka. Airvast WM168g. Bugs: ndiswrapper 1.0_rc2 &#8594; Doesn’t work with kernel 2.6.10 and USB 2.0 (awlgtnic: probe of 3-3:1.0 failed with error -22), ndiswrapper 1.3 cvs works with 2.6.13.
```

I downloaded the GWU513_1203A.zip Windows drivers and successfully installed them via the ndiswrapper GUI front end and can list it as follows:

```

$ ndiswrapper -l
awlgtnic : driver installed
        device (124A:4023) present (alternate driver: p54usb)

```

Then made sure the module was loaded:
```

$ sudo ndiswrapper -m
module configuration already contains alias directive

$ sudo modprobe ndiswrapper

```

A quick lsmod shows:

```

$ lsmod | grep ndiswrapper
ndiswrapper           185240  0 
usbcore               138632  8 ndiswrapper,hci_usb,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
$ 

```

So ndiswrapper *is* running, however when I check dmesg, I get the following:

```

$ dmesg | grep prism
[   36.032354] prism54usb: eeprom read failed!
[   36.032375] prism54usb: probe of 3-5:1.0 failed with error -22
[   36.032402] usbcore: registered new interface driver prism54usb
```

The iwconfig and ifconfig commands do not show up wlan0 and any attempt to scan wlan0 simply comes up with:

```

$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

The error shown in dmesg is (nearly) the exact same one shown on the Sourceforge page. Does this mean that this adapter is *not* usable under Ubuntu at all? I'm using 7.10 Gutsy with 2.6.22 kernel.

I also tried blacklisting the p54usb driver, but to no avail.

Alternately, is anyone aware of any native Linux drivers? I came across the _[Prism54 Project](http://prism54.org)_ site, but I'm not making heads or tails of it at the moment - it appears the driver is incomplete and/or experimental?

I probably should mention that it shouldn't be a hardware issue - the recently destroyed Windows setup worked perfectly with it. :p About the only thing I haven't yet explored is if I need to do any firmware updates of the unit, given that eeprom error from dmesg, so I'm going to check that out next, but in the meantime, any help would be greatly appreciated.

---

### Post by dogacres on 2008-05-09
HyRax,
I'm having the same problem trying to get my PN15 wireless working after having left windows behind for Ubuntu 8.04.  I've been foraging far and wide but have not yet found any native drivers, but have confirmed with your post's help that my chipset is AirVast rather than Zydas. 

Have you been able to get your PN15 running under Hardy Heron?

Best regards,

---

### Post by HyRax on 2008-05-18
Hi - sorry for the late reply.

Unfortunately my PN15 continues to like dormant with Hardy. No joy in any department, via Gutsy upgrade or new Hardy install.

---


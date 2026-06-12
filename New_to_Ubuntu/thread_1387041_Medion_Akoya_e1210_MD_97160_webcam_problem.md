---
title: "Medion Akoya e1210 MD 97160 webcam problem"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by USB_NL on 2010-01-21
hello

i have installed a dual boot on this netbook from a buddy of mine because his windows crashed

the webcam dosn't work with karmic koala

i probably can use a driver cd for windowsXP

in karmic koala all seems to work accept for the webcam

how do i fix this?

i have read something about ndiswrapper will that work?

---

### Post by Zorael on 2010-01-21
That's a rebranded MSI Wind, isn't it? From [Wikipedia](http://en.wikipedia.org/wiki/Medion_Akoya_Mini);
> **Wikipedia]The Medion Akoya Mini (E1210) is an OEM netbook version of MSI Wind manufactured by Medion AG, Germany, designed to be sold in continental Europe.

The Medion Akoya Mini is preloaded with the Microsoft Windows XP Home operating system and is customised according to the country where it is sold.

Major hardware **differences** in comparison with MSI Wind are:
[list][*]**1.3 megapixel camera**
[*]No Bluetooth device (German, Danish and Australian model includes mini Bluetooth dongle)
[*]No RAM module soldered onboard
[*]Wireless 802.11 n[/list][/quote]

The MSI Winds suffer in Karmic, as is noted in [the release notes](http://www.ubuntu.com/getubuntu/releasenotes/910). The camera driver has a bug that causes the USB system to crash if enabled, so it has to be disabled if you want to use other USB devices. Also, when raising or lowering brightness (on most bios versions) it starts to oscillate inbetween brightness settings. Both are known bugs, and the USB crash is fixed in an updated kernel in the repository for proposed updates.

So according to the Wikipedia page your Medion netbook has a different webcam and *may* not suffer from the same issue. If it's not working, it may be the same bug, or it may be something completely else.

From said release notes (and note the links to the bug reports) said:**
> **[SIZE=3]bison webcam in MSI Wind netbook causes USB errors if not disabled[/SIZE]**

An error in the uvcvideo driver used for the bison webcam in certain MSI Wind and related netbooks causes USB support to fail, resulting in an inability to use USB devices or suspend/resume the netbook. As a workaround, users can disable the camera before boot using the Fn+F6 hotkey. ([435352](https://bugs.launchpad.net/bugs/435352))

**[size=3]Brightness flickering on MSI Wind netbooks with KMS[/size]**

A bug in the kernel-mode-setting (KMS) brightness handling on certain MSI Wind netbooks, including the U90, U100, and U120, results in a bad flickering effect whenever the brightness is changed on the desktop, as the brightness is repeatedly raised and then lowered. Users affected by this issue can use the same workaround as described in the previous note to disable KMS. ([415023](https://bugs.launchpad.net/bugs/415023))

However, [the Ubuntu wiki page on netbook support](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Medion Akoya E1210) lists the E1210 as working "very well". It doesn't say if that's in Jaunty or in Karmic though, nor does it mention the webcam.
[quote="Ubuntu wiki on netbooks"]**[SIZE=3]Medion Akoya E1210[/SIZE]**
Works very well. Sound, wireless, ports, suspend, hibernate and hardware function buttons all reported to work correctly.[/quote]

To answer your questions, your Windows driver for the webcam will definitely not work. There is too much of a difference between the two operating systems. The exception where Windows drivers might work is (as you said) when using them through ndiswrapper - but that's for wireless cards only. There is no such wrapper for webcam drivers.

So if your webcam issue is the same as people with MSI Winds are experiencing, you should be able to solve them by enabling the **karmic-proposed** repository and upgrading to the **2.6.31.18** kernel. [This wiki page on repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates Tab) should help you get it enabled. Then you just need to upgrade packages and reboot. Hopefully that will do the trick.

---

### Post by USB_NL on 2010-01-21
:D thanks upgrading to the **2.6.31.18** kernel solved the problem and the webcam worked wen i tested it in Cheese

---

### Post by kendoori on 2010-03-08
Where did you get 2.6.31.18? I can't seem to find it? and is this solution still working for you?

---


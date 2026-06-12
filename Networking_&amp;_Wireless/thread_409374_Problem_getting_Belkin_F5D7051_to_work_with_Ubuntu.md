---
title: "Problem getting Belkin F5D7051 to work with Ubuntu 7.04 Beta"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by asdlinux on 2007-04-14
Hi

I'm trying to get a Belkin F5D7051 to work with Ubuntu 7.04. I'm using ndiswrapper and i have installed the driver successfully. My problem is that it detects the hardware but it loads an alternate driver. i get this output from ndiswrapper:

root@magnus-laptop:/home/magnus# ndiswrapper -l
bcmrndis : driver installed
        device (050D:7051) present (alternate driver: rt2570)

rt2570 driver is wrong and probably blocking ndisdwrapper from loading the driver. How can i stop Ubuntu to load the alternate driver?

Thanks 
Magnus

---

### Post by AmyRose on 2007-05-01
Try this: [http://ubuntuforums.org/showpost.php?p=2570962&postcount=3](http://ubuntuforums.org/showpost.php?p=2570962&postcount=3)

Doing that and rebooting made my wifi card work.

Oh, and don't use ndiswrapper for Ralink cards. It's not necessary since Ubuntu comes with a GPLed driver. Unfortunately, the default one in Feisty is terribly broken, but my directions will force it to fall back on the working driver.

---

### Post by janemiddlemiss on 2007-08-13
> **AmyRose said:**
> Try this: [http://ubuntuforums.org/showpost.php?p=2570962&postcount=3](http://ubuntuforums.org/showpost.php?p=2570962&postcount=3)

Doing that and rebooting made my wifi card work.

Oh, and don't use ndiswrapper for Ralink cards. It's not necessary since Ubuntu comes with a GPLed driver. Unfortunately, the default one in Feisty is terribly broken, but my directions will force it to fall back on the working driver.

the belkin f5d7051 is a wireless usb adapter not a card.

User: AmyRose's blacklisting drivers didn't work for me.

hey, did anyone successfully get the belkin wireless  G+ usb adapter working in ubuntu 7.04 Feisty Fawn?

i googled it and have tried numerous suggestions from others but no luck

---

### Post by janemiddlemiss on 2007-08-14
i've got the f5d7051 belkin usb working under ubuntu 7.04 feisty fawn at long last.[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

Reinstall ubuntu 7.04. 
(maybe you don't have to but after changing so many things i thought i'd play safe.  If you have and need to keep windows installed on a dual boot then i recommend using the free 'boot it NG')

Follow this tutorial to get drivers installed:
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)
(Use the LATEST NDISWRAPPER program from their own website.  Also be careful to substitute belkin driver filenames in place of the stated ones).

Flashing lights on adapter = success.
I get the same message about alternate driver rt2571 like in the first post above but can still log on regardless
However my problem is that i have to 1) type sudo modprobe ndiswrapper on reboot and 2) keep the wireless usb adapter unplugged during startup, until after i've typed this command otherwise it crashes right after log in (!!??)

---

### Post by ugm6hr on 2007-08-14
> **janemiddlemiss said:**
> However my problem is that i have to 1) type sudo modprobe ndiswrapper on reboot and 2) keep the wireless usb adapter unplugged during startup, until after i've typed this command otherwise it crashes right after log in (!!??)

For problem 1 - this might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#autostart](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#autostart)

Whether it helps problem 2 - try it and see....

---

### Post by janemiddlemiss on 2007-08-14
thanks. that autoloads ndiswrapper on boot up.

As for ubuntu from crashing after login whenever the usb adapter is in:

fixed it by typing 'sudo gedit /etc/modprobe.d/blacklist' then adding the lines:

blacklist bcm43xx 
blacklist rt2570

I'd feel happy about all this if it hadn't taken me the best part of 3 days!

f_ucking painstaking is configuring Ubuntu

---

### Post by nikef on 2007-08-14
> **janemiddlemiss said:**
> the belkin f5d7051 is a wireless usb adapter not a card.

User: AmyRose's blacklisting drivers didn't work for me.

hey, did anyone successfully get the belkin wireless  G+ usb adapter working in ubuntu 7.04 Feisty Fawn?

i googled it and have tried numerous suggestions from others but no luck

i use the belkin wireless g adapter model number F5D7050

I plugged it in and away i went,although at first i was using a different model that did not work

---

### Post by nickmcg on 2007-08-15
> **janemiddlemiss said:**
> thanks. that autoloads ndiswrapper on boot up.

As for ubuntu from crashing after login whenever the usb adapter is in:

fixed it by typing 'sudo gedit /etc/modprobe.d/blacklist' then adding the lines:

blacklist bcm43xx 
blacklist rt2570

I'd feel happy about all this if it hadn't taken me the best part of 3 days!

f_ucking painstaking is configuring Ubuntu

I think you must have been unlucky - the rt2570 module worked for me flawlessly, and was a great improvement on ndiswrapper.

Nick

---

### Post by Dynamicadam on 2007-09-04
I have done everything that was said, and ndiswrapper gave a success message.  All the drivers and stuff are in the ndiswrapper/bcmrndis folder.

The adapter shows up in the Hardware info as USBRAW (is this normal)

The adapter is not flashing.

HELP!

---

### Post by nickmcg on 2007-09-04
> **Dynamicadam said:**
> I have done everything that was said, and ndiswrapper gave a success message.  All the drivers and stuff are in the ndiswrapper/bcmrndis folder.

The adapter shows up in the Hardware info as USBRAW (is this normal)

The adapter is not flashing.

HELP!

What does iwconfig report (and ifconfig)?

Although the modules have been installed, the wireless is not configured - go to System->Administration->Networks to configure the card

Nick

---

### Post by Dynamicadam on 2007-09-06
Hi,
 
iwconfig show no wireless extensions on lo and eth0
 
The network panel only has options for a modem and a wired connection.

---

### Post by nickmcg on 2007-09-06
It looks like something is not loading correctly.
Check dmesg for any ndiswrapper error messages```
dmesg | grep ndiswrapper
```

Nick

---

### Post by Paris Heng on 2007-09-06
Hey,

I am using F5D7050.

I am using **AMD64**, i heard there are another way of installing Ndiswrapper. Are you ways of installation is for x86 architect?

Thank you.

---

### Post by Dynamicadam on 2007-09-06
I am getting two messages:
ndiswrapper version 1.47 loaded (smp=yes)
usbcore: registered new interface wrapper ndiswrapper

---

### Post by nickmcg on 2007-09-07
> **Dynamicadam said:**
> I am getting two messages:
ndiswrapper version 1.47 loaded (smp=yes)
usbcore: registered new interface wrapper ndiswrapper

You should have a message between those two lines, saying something like```
ndiswrapper: driver bcmwl5 (Broadcom [blah, blah]) loaded
```

Did you get any messages when you did the ```
sudo ndiswrapper -i [windows inf file]
```step?

Nick

PS I did try using a Belkin f5d7010 (pcmcia adaptor), but I had so many problems with it (Ubuntu and windoze), that I gave up and bought a dLink usb card instead.
Ideally, I'd prefer to use an adaptor with a native driver, but trying to find one is nigh  on impossible (they don't tell you what chipset you're getting)

---

### Post by Dynamicadam on 2007-09-07
First time I got an invalid driver message, but I did what the tutorial said, and I got a success message the second time.

---

### Post by nickmcg on 2007-09-08
It looks to me that ndiswrapper is not loading the windows driver.
It might be worth removing then reinstalling the driver to see what happens

Nick

---

### Post by Dynamicadam on 2007-09-08
I re-installed the drivers and then used the following commands with the adapter plugged in to see if it was working or not.
```
dmesg | grep ndiswrapper
```
```
ndiswrapper -l
```
 
The results are below.  It says the device is present, but it is not appearing in the network manager, it isn't flashing and Firefox won't connect.

[[IMG]http://sapvow.bay.livefilestore.com/y1p0qfWNMEbazFnYimj038omCPxPM2RePbgYdWBgtg6LMWZsu02zrlojylV5AIp4LpccZ8i9b9ekXIhQPxWmxxjOg/Screenshot.png[/IMG]](http://sapvow.bay.livefilestore.com/y1p0qfWNMEbazFnYimj038omEz6qMy4_hPwNFzmVG3EieVW_hFLyRBiSdAqzVe1rMW4bJS0eKKAkj6Y1ErE8n9MbA/Screenshot.png)

See what I mean?

Thanks for helping BTW!

---

### Post by nickmcg on 2007-09-08
Ok, you're using the same chipset as I am```
lsusb
Bus 002 Device 002: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
```

You can uninstall ndiswrapper (if you want). Go to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) and download the legacy driver for rt2570 and follow the instructions in the archive to build and install it (there might even be a ready built version in the repository, but it's out of date)

If you want to use WEP, then that's all there is to it (the device should show up as rausb0)
If you want to use WPA, you'll need to configure it with iwpriv or (which is what I have done) grab rutilt (there's a link to that on serial monkey)

Just to add a further complication, there's also the newer rt2x00 driver, but I haven't been able to get that to work reliably, although if you can, it means that you can use network manager or wicd to configure everything (THE device shows up as wlan0, but I can't get a valid dhcp lease).

Pleasure to help - I've been down this route myself, and others helped me!

Cheers

Nick

---

### Post by kditty on 2007-09-12
i got this card working with this tutorial: [http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)

with  	Zydas 1211B  chipset

---


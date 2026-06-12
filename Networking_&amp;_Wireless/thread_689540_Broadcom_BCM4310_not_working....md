---
title: "Broadcom BCM4310 not working..."
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Haglaz on 2008-02-06
I've followed a good number of guides found on this forum, Ubuntu docs and elsewhere. When I try to use ndiswrapper, it takes the driver and recognises the device, but I'm getting no wireless interface and nothing is appearing in wicd or network-admin. I've also tried using fwcutter, but I may be doing something wrong or leaving a step out.

When I run lshw -C network, this is what it tells me about my wireless device:

```

  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

I'd also like to note that Vista reports this device as BCM4315, not 4310.

I can retrace my steps to provide better detail of what I've been trying, but the problem is there are no error messages of any kind. Ndiswrapper and fwcutter seem to be working fine at first, but I still get nothing from wicd or anything. Am I missing a step here?

---

### Post by jan quark on 2008-02-06
I have the same issues as you have

firstly I have the broadcom 4311 wireless card (rev 01)

secondly ndiswrapper never managed to activate the wlan card for me / haave a dell 1501)

thirdly fwcutter works and does not work. very at random, sometimes the speed is very good, sometimes I have lags which last for an eternity

I somehow managed to activate the card doing this easy steps but as I said the broadcom cards are the hell on earth right now...

[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

---

### Post by Haglaz on 2008-02-06
All I get in Restricted Drivers is Nvidia graphics driver. I've got bcm43xx-fwcutter installed, but it also never prompted me to download firmware when I installed it. :confused:

---

### Post by baixinhu on 2008-02-06
> **Haglaz said:**
> All I get in Restricted Drivers is Nvidia graphics driver. I've got bcm43xx-fwcutter installed, but it also never prompted me to download firmware when I installed it. :confused:

if you have gusty, restricted drivers will give you nothing but trouble...
install the drivers with ndiswrapper, preferentially on a fresh install, but i'll post an link to help you ( it kindda work for my bcm4318 but it was still flaky, it wasn't fresh install)

---

### Post by baixinhu on 2008-02-06
here, fallow this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

---

### Post by Papa-san on 2008-03-16
Did it work for you? 
I have three Dell 1525's to get working, and nothing I have tried works. I don't want to follow that How-to just yet, as I have a clean install, and I don't want to muck it up and have to do it yet again...

---


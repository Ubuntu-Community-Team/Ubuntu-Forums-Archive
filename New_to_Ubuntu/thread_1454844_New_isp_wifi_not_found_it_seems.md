---
title: "New isp wifi not found it seems"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by nnjond on 2010-04-15
Hi,

I've changed my isp to TALKTALK and now my laptop doesnt even sense the wifi signal; although the wlan light on the transmitter is pretty solid. Could it be that my driver isnt recognised by TT? Or do I just make some drop down decisions?

Thanks

nnjond@nnjond-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

nnjond@nnjond-laptop:~$

---

### Post by Paqman on 2010-04-15
Changing your ISP won't affect your wfifi connection from the PC to the router, but it will affect the router's connection to the internet. Have you updated the router with your new account name and password?

You haven't accidentally turned your wifi off or something?

---

### Post by aeiah on 2010-04-15
i assume you got a new modem/router when you changed to talktalk. look at the documentation and see if the wifi ssid is hidden by default, what the default ssid is, and what the default encryption is. i think talk talk uses WPA by default which is great for security but if you were previously using WEP then you may never have realised that your wifi drivers have trouble with WPA.

you could try going into the talk talk router's control panel and switching your wifi encryption off or to WEP and seeing if that helps, and making sure the ssid is being broadcast and isnt hidden.

obviously this isnt a lasting solution and you shouldnt keep your wireless encryption off or even on WEP (WEP can be hacked in about 3 minutes - and it DOES happen), but it may make the problem clearer.

---

### Post by nnjond on 2010-04-15
Thanks for your interest.

The new router has connected my Desktop pc via a cable, and I have the Wireless Network Name and wireless password on the box, but not sure about my way around my laptop network connections app.

---

### Post by coffeecat on 2010-04-15
> **nnjond said:**
> but not sure about my way around my laptop network connections app.

First things first. I cannot see a wireless device listed in your lspci output. Some questions:

Does your laptop have an inbuilt wireless card, or do you use a usb device?

If an inbuilt card, is there is wireless switch on the laptop? Make sure it is switched on.

Do you have Windows on that laptop? Can Windows connect wirelessly?

If you use a usb wireless device, post the output of...

```
lsusb
```

---

### Post by nnjond on 2010-04-15
My laptop has an internal card and it is switched on My only os's are 9.10 and beta 10.04. 9.10 worked fine untill i changed isp. Lynx detects my new isp but works a bit slow

---

### Post by Paqman on 2010-04-15
Are you still having problems nnjond?

Erratic speeds are to be expected for a the first few days on a new connection while your ISP sorts out what your line can handle.

---


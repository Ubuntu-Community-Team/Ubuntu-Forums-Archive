---
title: "Absolute beginner needs help with wireless..."
date: 2009-02-14
forum: New to Ubuntu
---

### Post by linkman1337 on 2009-02-14
Hmm hi guys. I started using ubuntu today (8.10 I believe) on my new laptop and my wireless doesn't seem to be being picked up... it worked without a problem on Vista (although the Windows Wireless Service didn't start with the computer, I had to load it up manually -- maybe part of the problem?) anyway, I'm using a toshiba laptop, from what I gather from the terminal the wireless card is Athernos, although I can't remember the model of it. Anyway, can anyone please walk me through setting it up?

---

### Post by kestrel1 on 2009-02-14
Post the result of```
lspci
```
You need to type this in a terminal

---

### Post by linkman1337 on 2009-02-14
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
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
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
**03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**

```

I'm assuming the bit I bolded is what your after, but I posted it all just in case..

---

### Post by sylvainrb on 2009-02-14
Did you update ubuntu right after you installed it so you could have the necessary drivers for your wireless?

When I first installed ubuntu, I had my laptop plugged in for the internet and right after the install, the system picked up about 250 updates including the drivers for my wireless.

---

### Post by linkman1337 on 2009-02-14
Yeah, it's updated.

---

### Post by sylvainrb on 2009-02-14
Oh ok. I suppose you did that as well then but just in case: did you install the drivers in system -> hardware drivers? I had one for the wireless card and another one called software modem.

If not I can't help you anymore. I'm still a beginner at it too! Sorry!

---

### Post by avtolle on 2009-02-14
Take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) and see if that gets it working.

---

### Post by Slowspeed on 2009-02-14
I might be back tracking but did you enter in the security information for the access point? Or are you not seeing anything at all?

---

### Post by cerealtx on 2009-02-14
```
iwconfig
```
post results please

---

### Post by linkman1337 on 2009-02-14
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


```

---

### Post by benerivo on 2009-02-14
I think you'll need to add a package to enable that particular wireless card. Try installing...```
sudo apt-get install linux-backports-modules-intrepid-generic
```and rebooting. You might then have an extra option in the restricted drivers section (from the main menu).
Have a look at this post ([http://ubuntuforums.org/showthread.php?t=967654](http://ubuntuforums.org/showthread.php?t=967654)) for some more detailed info.

---

### Post by linkman1337 on 2009-02-15
I'm not sure which of your tips in particular did it, but it works now. Thanks! :)

---


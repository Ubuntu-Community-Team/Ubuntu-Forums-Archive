---
title: "Card Reader not functioning properly"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by guerilla on 2009-04-30
hello everybody,

ive just installed ubuntu 9.04, ive tried previous versions but i could never get the wireless card to work. now though its fully functional so ive ditched windows for the mean time.

i have a problem with my card reader though, its not recognising cards when i put them in, also when i turn the computer off the light on the card reader remains on (as does the light on my usb stick)

any suggestions on how i can get this working?

thanks

---

### Post by guerilla on 2009-05-01
any help with this?

---

### Post by coffeeaddict22 on 2009-05-01
Hi,
Welcome to Ubuntu.
You can get a bit more info via the terminal (Applications/Accessories/Terminal).
Once there, type in ```
lspci
```; that'll tell you what type of card you're using hopefully.  If it doesn't show up, it hasn't been recognised by the system, though.  Post what you get back if you need more help.

---

### Post by caldoverde on 2009-05-01
Hi, excuse me to intrude, don't mean to be rude, but I have the same problem and the lspci command shows:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I'm using a Compaq cq-60 210ep


Thanks in advance!

---

### Post by coffeeaddict22 on 2009-05-01
Have you found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490") bug report?  It looks like if it's an XD card reader only, you need to talk to Olympus.  They own the standard, and aren't putting out a Linux driver.  
If it's not XD, then I'm not sure.  There's no record of your card reader in lspci; is it a USB device or built in?  If it's USB, try ```
lsusb
``` and post back the output of that.

---

### Post by guerilla on 2009-05-01
Bus 001 Device 003: ID 07b8:e004 D-Link Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

this is the resuls of lsusb as i think the card reader is a usb device. hope you can help

---

### Post by coffeeaddict22 on 2009-05-02
Put your card in (what type is it?), wait a few secs, then type in ```
dmesg
```
That should tell you if there's anything being recognised by the system, and whether it's PCI or USB, as well as what the problem might be.  Post your results back.

---

### Post by guerilla on 2009-05-02
its actually started reading the card now. however it still remains on when the pc is powered off as do the usb ports on the front of the computer

---

### Post by unutbu on 2009-05-02
Where is the power coming from? if the computer is unplugged... :confused:

Some machines (like Dells) have lights that remain on even when the computer is shutdown. However, if you plug the machine into a powerstrip, you can use the switch on the powerstrip to cut all power to the machine after you shutdown. That should eliminate any lights, obviously.

---

### Post by guerilla on 2009-05-02
its not unplugged just shut down, the lights never used to remain on and still dont when i shut down from xp.

---

### Post by caldoverde on 2009-05-03
After trying to read a card for the first time and not being able to do it, rebooted the laptop and actually i'm able to read my Olympus XD card.

---

### Post by coffeeaddict22 on 2009-05-03
Good enough.  Enjoy the ride!

---


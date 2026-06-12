---
title: "Wlan vs. Usb/Bluetooth"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by Mayfairy on 2006-10-22
Hi! 

I'm having some problems with my laptop (Fujitsu Siemens Amilo L7310GW) running Ubuntu Dapper 6.06.

My problem is that when I boot up my machine it works good except USB-devices. I have had the following problems:
- Usb-bluetooth dongle doesn't show up
- Usb-mouse moves REALLY slowly
- Usb-line to my cell phone doesn't work

I searched around and found out that I should modify my grub boot arguments by adding the line "acpi=off noapic". I did that and got fatal bios error or something along with recommendation to add "pnpbios=off" to my boot arguments. I did that and Ubuntu started nicely. 
Connected my cell phone to my computer and it mounted automatically. Then I tried Bluetooth connection to my phone and it worked fine. 

Then I noticed my Wlan card wasn't detected. Ifconfig, Iwconfig and Networking didn't show any signs of it. 

In the end I made two grub start options; one with "acpi=off noapic pnpbios=off" so I can use Usb devices and one without those arguments so I can use my Wlan.

Apparently I need Acpi to turn on my Wlan card but at the same time it blocks my Usb.

I also have Windows XP on my machine and the mouse works nicely as well as Usb line to my phone. Bluetooth and Wlan do seem to have some problems working at the same time, but I believe it's just some temporary error. 

I have yet to try if the mouse works with my "acpi=off" settings. 

I'd really appreciate it if you could help me with this problem. I'm trying to infect my friends with Ubuntu/Linux fever since they're all Windows users but it's quite hard to convince them when I myself have this kind of problem.

---

### Post by Mayfairy on 2006-10-22
EDIT:

Tried to boot up with acpi=off argument and got Bluetooth, Usb -> cell phone link and Usb-mouse all work good at the same time. 
Mouse was detected right when I plugged it in instead of having to plug it in when booting up which I had to do before and even then it was lagging too bad to be used properly.

---

### Post by Mayfairy on 2006-10-22
EDIT:
Usb-Bluetooth works with Wlan occasionally. Mouse and Usb-cord to cell phone never work with Wlan.

---

### Post by Mayfairy on 2006-10-24
*Desperate bump* ..If anyone should know anything.

---


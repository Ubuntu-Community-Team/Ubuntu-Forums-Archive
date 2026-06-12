---
title: "eagle-usb problem"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by mihalisla on 2006-08-28
Hello ,I 'm having this problem and I'm new to ubuntu:
(I 'm using ubuntu 6.06 dapper amd64 bit)
I installed from the dvd the eagle-usb drivers and when i wrote eaglectrl -w (after isp,passwd settings) it gave me this..

Sending options to device /proc/bus/usb/002/002
Unknown option on line 27
Unknown option on line 28
Unknown option on line 29
Unknown option on line 30
Unknown option on line 31
Unknown option on line 32
Unable to send options to driver: Unknown error 512
Failed to send options to device /proc/bus/usb/002/002
What i have to do about it?
I'm reffering to sagem fast 800 usb modem

Thank you for reading this message[-o<

---

### Post by aces21 on 2006-08-29
The Eagle-usb driver doesn't work with Dapper. You should use ueagle-atm instead. I have written a howto for getting this working [here]("http://www.ubuntuforums.org/showthread.php?t=201127").

Give it a go and let us know if you get stuck.

---

### Post by mihalisla on 2006-08-30
Thank you very much for your reply I'll try it out and i'll post the results to forum again.I 'm searching for 1 week to do sth for this but nothing.Thanks once again.
Greetings

---

### Post by mihalisla on 2006-08-30
The damned sagem just gave one more error throuyuor guide ,check this out if anybody knows about it: 
root@mike-desktop:/home/mike# sudo modprobe ueagle-atm
FATAL: Error inserting ueagle_atm (/lib/modules/2.6.15-26-amd64-generic/extra/ueagle-atm.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Then i did:
root@mike-desktop:/home/mike# dmesg|grep ueagle
[  387.088267] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  387.088349] ueagle_atm: Unknown symbol usbatm_usb_probe
[  388.691551] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  388.691559] ueagle_atm: Unknown symbol usbatm_usb_probe
[  388.723829] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  388.723909] ueagle_atm: Unknown symbol usbatm_usb_probe
[  388.754867] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  388.754970] ueagle_atm: Unknown symbol usbatm_usb_probe
[  559.149147] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  559.149232] ueagle_atm: Unknown symbol usbatm_usb_probe
[  715.304687] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  715.304782] ueagle_atm: Unknown symbol usbatm_usb_probe



thank you for reading this message

NOTE : above it's the log of 2 commands](*,) ]

---

### Post by mihalisla on 2006-08-31
> **mihalisla said:**
> The damned sagem just gave one more error throuyuor guide ,check this out if anybody knows about it: 
root@mike-desktop:/home/mike# sudo modprobe ueagle-atm
FATAL: Error inserting ueagle_atm (/lib/modules/2.6.15-26-amd64-generic/extra/ueagle-atm.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Then i did:
root@mike-desktop:/home/mike# dmesg|grep ueagle
[  387.088267] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  387.088349] ueagle_atm: Unknown symbol usbatm_usb_probe
[  388.691551] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  388.691559] ueagle_atm: Unknown symbol usbatm_usb_probe
[  388.723829] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  388.723909] ueagle_atm: Unknown symbol usbatm_usb_probe
[  388.754867] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  388.754970] ueagle_atm: Unknown symbol usbatm_usb_probe
[  559.149147] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  559.149232] ueagle_atm: Unknown symbol usbatm_usb_probe
[  715.304687] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[  715.304782] ueagle_atm: Unknown symbol usbatm_usb_probe



thank you for reading this message

NOTE : above it's the log of 2 commands](*,) ]

anybody?

---

### Post by mihalisla on 2006-09-01
Any suggestions guys???

---

### Post by mihalisla on 2006-09-04
All I found was that i need  ueagle-atm and data but how can i configure them with the error above?

---

### Post by ajs54 on 2006-09-20
[FONT="Arial"]Hi.

I had the same problem, and it was difficult to solve. I hope it's not too late, and that this solution will work also for you.  There's an hint in [this forum on Eagle site]("http://forum.eagle-usb.org/viewtopic.php?t=4251&sid=b7e819ad29e3bf0179a7c5838be475a4"), but it is in French (well, that's OK for me).

The point is (in my case) that new kernels do contain a module usbatm which is slightly different from the one used by ueagle-atm.  To solve this problem, just change the [FONT="Courier New"]modules.dep[/FONT] (in [FONT="Courier New"]/lib/modules/...[/FONT], where ... is your kernel number): replace the [FONT="Courier New"].../kernel/drivers/usb/atm/usbatm.ko[/FONT] dependency for [FONT="Courier New"].../extra/ueagle-atm.ko[/FONT] by the correct one ([FONT="Courier New"].../extra/usbatm.ko[/FONT]).  You may need to reboot, but it should work (for ueagle-atm).

The bad news is that this file may be updated automatically, and may need to be changed once in a while.  To prevent this, I will try and change the "bad" modules' names (those in [FONT="Courier New"]kernel/drivers/usb/atm[/FONT], [FONT="Courier New"]usbatm.ko[/FONT] and [FONT="Courier New"]xusbatm.ko[/FONT]), adding a [FONT="Courier New"]k_[/FONT] prefix.  I hope it won't cause other problems (but it should not, I think).

I hope this will help...[/FONT]

---


---
title: "USB Kernal Mod ch341 removal"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by lobo_blanco on 2008-12-31
Ubuntu 8.10
Sony VAIO VGN-FS920 laptop

I have an HP DeskJet 1000C printer that I would love to have working under Ubuntu 8.10. I'm not sure if it's even possible since it's not supported by HPLIB but I've been trying various attempts at getting it work.

The problem is that the printer has a Centronics 36 pin parallel interface so I am using a USB to IEEE 1284 adapter cable. (no parallel port on the laptop)
Currently lsusb sees this cable as a  "WinChipHead USB->RS 232 adapter with Prolifec PL 2303 chipset". (cable is actually USB to IEEE 1284)

I'm not sure why, but I tried the CH341 Single Port Serial Driver which involved "sudo modprobe ch341".
This is for a serial interface, not parallel. I need the USB port to recognize the parallel interface of the printer.
I'm trying the CUPS package currently.

Now, when I plug the cable into the USB port it is seen as:
"WinChipHead USB->RS 232 adapter with Prolifec PL 2303 chipset"
     /dev/ttyUSB0 according to the Device Manager.

_Bottom Line:_
I've ended up with a Serial vs needed Parallel problem.
I'd like to remove the ch341 Kernal mod completely.
I tried "sudo rmmod ch341" and "sudo rmmod usbserial" which works until I reboot then it is listed again when using lsmod.

How can I get rid of ch341 and it's association with this cable?

Any and all help with this is greatly appreciated.

Thanks,

Dave

---

### Post by Tim Sharitt on 2008-12-31
add ch341 to /etc/modprobe.d/blacklist

---

### Post by lobo_blanco on 2008-12-31
Thanks Tim! ... it's appreciated!!

lsmod no longer lists ch341 or usbserial.
Just what the Dr. ordered ...

I'm back to square one with the printer but that's another can of worms and square one is exactly where I needed to be on that.


Thank You,

Dave

---

### Post by Tim Sharitt on 2008-12-31
You may want to look at [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1000C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1000C). It recomendends a driver and says it works perfectly.

---

### Post by lobo_blanco on 2008-12-31
I'll take a look, it may be the driver that I am using now.
I think the problem I'm having is with figuring out what the proper "Device URI:" should be. Maybe the link explains that.
For some reason the HP 1000C is a tough nut to crack, not sure why it's not supported with HPLIB, maybe it's just too old.

It's a great printer that prints 11x17 so I'm determined to get it to work one way or the other.

Many Thanks
Have a great New Year!

Dave

---


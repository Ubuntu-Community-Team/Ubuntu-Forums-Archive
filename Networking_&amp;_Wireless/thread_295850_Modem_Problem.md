---
title: "Modem Problem"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Sierra_Dave on 2006-11-08
Modem Stopped working after I installed new video card and had to diable a serial port.  I am running Ubuntu - Dapper on Compaq Deskpro 600 mhz.  I see the modem [ Modem Blaster ISA controller based] on system :

16550A - Compatible
info. capa list serial
info. category strlist serial
info.parent /org/freedesktop/HAL/dun.../pnp0501
/dev/tty S3
hotplug int 2(0x2)
sub tty
Serial Port int 3

In my Bios the video card is at IRQ 11 and the Intel USB controller is at IRQ 3.  I tried switching USB to 9 irq, but no luck.  I should also not the ISA slot is next to PCI slots and on a separate daughter board, thus it using the PCI bridge.  On boot-up, I cant see [cuz it goes to fast] fully that the PCI module is having an error.

I tried to autodetect and nadda.  I also tried manually switching w/o luck.

Is there a way to check IRQ conflicts and/or resolve this.

THanks !!
Dave

---


---
title: "Help installing L/Xubuntu from SliTaz"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Q'ochalo on 2010-10-30
Cross post from 'Installs'

Kind of a weird question. Please feel free to send me elsewhere if I need to. I am an absolute linux newb but have been playing with Ubuntu (on Dell 8400) and Slitaz (old laptop).

IBM A20m running at 500+MHz, 512 RAM and 8 GB free on the HD.

I have both the Lubuntu and Xubuntu iso files.

This BIOS will not boot from USB and CDROM is broken. I would like to figure out a way to install or mount Ubuntu to the empty partition so I can see if this machine can handle it reasonably. I love Slitaz, but I'd like my girls to be able to begin to use it, and Slitaz is a little 'rough' for 4 year olds!

Thanks

---

### Post by J V on 2010-10-30
Without extra hardware the only way I could see would be to somehow manipulate grub to boot from usb, or to flash the bios with a later version capable of handling usb boot... Niether is simple :)

---

### Post by snowpine on 2010-10-30
You can use [Unetbootin]("http://unetbootin.sourceforge.net") or, if you have another computer with a working CD drive, you can swap the hard drive over, do the install, and then swap the hard drive back. :)

---

### Post by Q'ochalo on 2010-11-16
Thanks a bunch.  Still haven't got UnetBootin to work right, but it's a step in the right direction...

---

### Post by jatan78 on 2011-06-09
I just installed Xubuntu 11.04 on A20m using PLoP to boot thumbdrive. I built the thumb drive using the built-in tool "Startup Disk Creator" on another pc running Ubuntu 11.04.

---


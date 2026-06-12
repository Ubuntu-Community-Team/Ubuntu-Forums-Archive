---
title: "Problem during setup"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Dr.Fayed on 2009-12-19
Hello
I downloaded the ISO file from ubuntu.com, burnt it correctly on a CD 700 MB and at the last 40seconds of its setup from windows (I use windows 7), the setup stops giving an error message "permission denied"


I tried to set it up from boot,
After choosing "Install Ubuntu" or even "Try Ubuntu", my laptop stops working, and no key works, I waited for it about 15 minutes but, useless

I remember that Windows gave the ISO burner program a block. However, I burnt it correctly


My Laptop is Toshiba Satellite L500-1GK

Thanks in advance

---

### Post by ryandavis33 on 2009-12-19
what i would is reformat your disc(i dont rember how to do it from the c prom) after you format the disc install ubuntu:)

---

### Post by jerrrys on 2009-12-19
did you do a checksum and a check cd?  what was your burnspeed?

---

### Post by joes7 on 2009-12-19
Reformat your machine completely, and try again. Alternately, try by re-burning the disk, or use a different ISO.

---

### Post by USB_NL on 2009-12-19
> **joes7 said:**
> Reformat your machine completely, and try again. Alternately, try by re-burning the disk, or use a different ISO.

Reformat?  No he would loose his windows7.




Another thing he could do is make a live-cd-iso run on a usb-stick or sd-card you need 2gig minimal to install it there 8gig is max im not sure but you can find the rest of the gigs in the cdrom-folder. Use this website for install-kit to make a flashdrive bootable.
[www.pendrivelinux.com](www.pendrivelinux.com)

Here is the howto page of 9.10
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

You can use the cdrom-folder on the usb-stick to share files with windows on the usbstick.

---

### Post by bodhi.zazen on 2009-12-19
> **Dr.Fayed said:**
> Hello
I downloaded the ISO file from ubuntu.com, burnt it correctly on a CD 700 MB and at the last 40seconds of its setup from windows (I use windows 7), the setup stops giving an error message "permission denied"


I tried to set it up from boot,
After choosing "Install Ubuntu" or even "Try Ubuntu", my laptop stops working, and no key works, I waited for it about 15 minutes but, useless

I remember that Windows gave the ISO burner program a block. However, I burnt it correctly


My Laptop is Toshiba Satellite L500-1GK

Thanks in advance

I am not following you, are you having a problem while installing (wubi) ? booting the CD ? or burning the iso ?

---

### Post by USB_NL on 2009-12-19
You must burn the ISO as an image-file and not just as a data copy.

Or did you get in the menu on the boot-cd?

---

### Post by bpan123 on 2009-12-20
I just had this exact same problem installing xubuntu 9.10 to a known good CF.

Installer stopped with the error "Permission Denied" to some apparently "read-only" file.  When complete, desktop good, everything functional, but when I rebooted, there was no MBR (Master Boot Record).

The message suggested that the HD might be over-heated or something... 

Very odd...

I'm about to re-burn the iso and try reformat / re-install...

---

### Post by bpan123 on 2009-12-20
I can't seem to find any info here about missing MBR, so as stated above, I'm going to reformat / reinstall, and DOCUMENT if the error reoccurs...
:rolleyes:

---

### Post by bpan123 on 2009-12-20
Just got the same error again...

new cd, used a different cd reader too...

> 
[Errno 30] Read-only file system '/target/boot/vmlinuz-2.6.31-14-generic'
This is often due to a fault hard disk.  It may help to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.


Any suggestions?

---

### Post by Dr.Fayed on 2009-12-20
Thnx guyz
I think that setting up Ubuntu from a USB Flash memory is, nearly, the answer of all :)

---


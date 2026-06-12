---
title: "Boot from USB support"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Trzone on 2009-01-04
I have an HP pavilion 521n that does not appear to have any usb booting support....
The usb drive works on my sister's new laptop.
So, is there a bootloader cd or something to that effect that would allow me to boot from usb?

---

### Post by Cypher on 2009-01-04
If I'm not mistaken, you'll need BIOS support to be able to boot from the USB disk.

Now you could use a combination USB/LiveCD to get a persistent configuration. So you'd use the CD to boot Ubuntu but all of your configuration would be stored on the USB drive.

This [HOWTO]("http://http://ubuntuforums.org/showthread.php?t=9893") describes the method above..

---

### Post by _sebastian_ on 2009-01-04
there are boot CDs which will enable you to boot from USB if I am not mistaken.

e.g. 
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

---

### Post by Trzone on 2009-01-04
Will i have to use a different cd image for each release?

---

### Post by _sebastian_ on 2009-01-04
sorry I am not sure but I would assume that the CD only provides the boot loader which then goes over to the USB... (very non-technical :-D ) So it could be that you can use the same CD for different releases...

---

### Post by Trzone on 2009-01-05
I managed to get a cd that would boot it
However i am having issues with booting it from GRUB

[http://ubuntuforums.org/showthread.php?p=6501451](http://ubuntuforums.org/showthread.php?p=6501451)

Here is the other post that i did heh

---

### Post by _sebastian_ on 2009-01-05
here [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB) is another good read for booting from USB and ways to do it.

I found it when I was looking for 'use grub to start from USB'

---


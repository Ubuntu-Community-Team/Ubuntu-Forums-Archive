---
title: "How to save setting on usb?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by ds dude on 2009-01-23
I have ubuntu linux on my usb, I saw a file casper and I'm wondering how to save my settings?

---

### Post by snova on 2009-01-23
As far as I know, a Live USB saves your settings automatically, the same as it would were it a full installation.

Is it not?

---

### Post by ds dude on 2009-01-23
No, it's doesn't save automatically, what am I doing wrong?

---

### Post by rMatey on 2009-01-23
I think you need to check these for the **Persistence** feature, so that it writes the changes to your USB drive.

[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

  That should make all of the difference in the world as it makes changes to your thumbdrive.

):P

---

### Post by theozzlives on 2009-01-23
Insert the USB drive, boot from the 8.10 live CD and go to Applications > Accessories > Terminal, then type:
```
wget pendrivelinux.com/downloads/u810/u810.sh
```
then:
```
chmod +x u810.sh && sh u810.sh
```
follow the prompts, set your CMOS to boot from USB.

---

### Post by ds dude on 2009-01-24
How do I set my CMOS?

---

### Post by ds dude on 2009-01-24
Does anyone know how to set the cmos?  I'm confused about it.

---

### Post by snova on 2009-01-24
He means to set the BIOS to boot from the USB drive. How this is done depends on the particular BIOS, but when you reboot, look for prompts to press a key to get into a menu on the first screen to show up. There should be a way to change the boot order.

---


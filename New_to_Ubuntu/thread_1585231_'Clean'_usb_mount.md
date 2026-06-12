---
title: "'Clean' usb mount"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by ozbolt on 2010-09-30
Hello

I know there are ways to put ubuntu easily on USB stick and boot it. Well, what I want is the same thing only that it does not populate my / directory of USB drive with many folders and thus drive unusable for what it is intended for - copying stuff from one computer to another.

So, is there a way to have ubuntu folder and a boot file in root directory and nothing else?

Ozbolt

---

### Post by mcduck on 2010-09-30
Are you talking about actual install to USB drive, or running a live environment from USB?

For live environment, you can install Grub2 to the drive and use that to boot .iso files. Everything related to Grub2 and the disk images will sit inside /boot directory on the drive, so it's pretty much as clean as a bootable drive possibly can be.

---


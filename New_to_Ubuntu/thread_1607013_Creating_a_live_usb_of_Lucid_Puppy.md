---
title: "Creating a live usb of Lucid Puppy"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by Robert Buckmaster on 2010-10-27
Hi.

I want to create a live USB for Lucid Puppy (5.1) in Ubuntu, but I can't figure out how.

Acoording to the homepage of UNetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) the program can't create a live USB of Lucid Puppy - it only supports version 4.0. Is there a way to make the live USB from command line instead?

What should I do?

Regards

---

### Post by beew on 2010-10-27
Try this
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by C.S.Cameron on 2010-10-27
This page shows how to install Puppy.

[http://puppylinux.org/main/How%20NOT%20to%20install%20Puppy.htm](http://puppylinux.org/main/How%20NOT%20to%20install%20Puppy.htm)

I have also used MultiBootUSB:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by halj32 on 2010-10-27
UNetbootin works fine, just point it to the ISO then the flash drive & let it get on with it everything works

---

### Post by oldfred on 2010-10-27
I created a flash drive with puppy using grub2. Like C.S.Cameron's link to MultiBootUSB but I did it manually. The advantage of grub2 is if your flash drive is larger you can have many ISO on one drive.

[http://ubuntuforums.org/showthread.php?t=1600093&highlight=puppy](http://ubuntuforums.org/showthread.php?t=1600093&highlight=puppy)

---

### Post by Geoff918 on 2010-10-27
Great guides:

[http://www.pendrivelinux.com/puppy-linux-on-usb/](http://www.pendrivelinux.com/puppy-linux-on-usb/)

[http://www.pendrivelinux.com/put-lucid-puppy-on-usb-flash-drive-from-windows/](http://www.pendrivelinux.com/put-lucid-puppy-on-usb-flash-drive-from-windows/)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Robert Buckmaster on 2010-10-28
I realised the problem was with my computer, not Netbootin or the USB stick. After I made a change to the BIOS the problem was fixed.

---


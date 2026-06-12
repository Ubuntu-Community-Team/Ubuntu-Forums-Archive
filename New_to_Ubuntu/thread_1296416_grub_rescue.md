---
title: "grub rescue"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by gaddo on 2009-10-20
Could anybody help with a netbook i have just trashed?
The problem is after playing with disk manager thing i now get Grub Error
"unknown filesystem"  Grub Rescue.
I have read that you can stuff to fix this problem but it requires live cd but being a netbook no cd drive i have an exernal cd drive and have set to boot first but it wont load? any ideas would be great its only a week old!

Gaddo

---

### Post by martrn on 2009-10-20
What netbook do you have ?

Do you have acsess to a pendrive or usb sockets ?

What options do you have for booting external media from the netbook ?

What do you mean by "won't load' ?????

---

### Post by gaddo on 2009-10-20
Acer Aspire one
and it has usb ports and i have a usb cd drive but i cant the cd to load 
keeps going to grub error? 
also have stick

---

### Post by LewRockwell on 2009-10-20
> **gaddo said:**
> Acer Aspire one
and it has usb ports and i have a usb cd drive but i cant the cd to load 
keeps going to grub error? 
also have stick

double-check that your BIOS is set to boot from USB devices FIRST

you shouldn't be getting that grub error if the optical drive is booting first

.

---

### Post by LewRockwell on 2009-10-20
? ? ? ?

> **gaddo said:**
> **i have an external cd drive**

? ? ? ?

> **martrn said:**
> do you have access to usb sockets?

What options do you have for booting external media from the netbook?

? ? ? ?

.

---

### Post by gaddo on 2009-10-20
usb cd drive has just come to life? didnt do anything! so have put booted from live cd
Will search for how to fix Grub error "unknown file system.
Thanks for your quick respone

---

### Post by martrn on 2009-10-20
> **gaddo said:**
> Acer Aspire one
and it has usb ports and i have a usb cd drive but i cant the cd to load 
keeps going to grub error? 
also have stick

Acer Aspire one has USB2.0 and as you have a stick I would suggest you download the ubuntu netbook remix and put it onto a usb stick.
See [https://help.ubuntu.com/community/GettingUbuntu]("https://help.ubuntu.com/community/GettingUbuntu") for getting the ubuntu netbook remix on a stick.

I would say that you could have a bad cd image or their is something wrong with the usb connector and/or usb cd drive.  USb sticks are generally designed to be booted from so should be a better way of booting the ubuntu netbook remix installation cd.

Ensure you download, the IMG file for USB sticks and take care to transfer the IMG (image file) properly in preperating for your new ubuntu netbook remix.  See:- [https://help.ubuntu.com/community/Installation/FromImgFiles]("https://help.ubuntu.com/community/Installation/FromImgFiles")

Over-write any master-boot records (grub) and file systems ect, when prompted.  Check the MD% sums of you IMG files when downloading your image files so that you have a valid proper copy.

---


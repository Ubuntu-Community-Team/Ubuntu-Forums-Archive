---
title: "Uinstall ubuntu that's installed on a USB stick"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by ultimatebuster on 2009-07-01
So I installed ubuntu onto a USB drive on a computer I don't use at all out of curiosity.

Do I need to uninstall it somehow to get rid of GRUB? or do I just need to format the drive. Is GRUP installed on the USB drive or the local hard drive?

Thanks

---

### Post by cariboo on 2009-07-01
Grub is installed on your usb device. Just reformat it, and grub should disappear.

---

### Post by skyjacker on 2009-07-04
> **cariboo907 said:**
> Grub is installed on your usb device. Just reformat it, and grub should disappear.
I too installed my 9.04 on a usb drive, and grub is on there also. I got to thinking that if something happened to the hard drive, I would also lose the ability to get into xp ( I dual boot). Is my thinking correct? How can I change grub to my pc, and still dual boot? I only use xp once a month for a newsletter, so I have to keep it around for a while.

---

### Post by sdlynx on 2009-07-04
Once you format your USB Stick GRUB should be gone.  If it isn't, you can go to the Windows Recovery Console (available through the installation disc) and type ```
fixboot
fixmbr
```that should set you back to only Windows booting.

---

### Post by theozzlives on 2009-07-04
> **skyjacker said:**
> I too installed my 9.04 on a usb drive, and grub is on there also. I got to thinking that if something happened to the hard drive, I would also lose the ability to get into xp ( I dual boot). Is my thinking correct? How can I change grub to my pc, and still dual boot? I only use xp once a month for a newsletter, so I have to keep it around for a while.

If something happened to your Hard Drive, restore the backups that you should be doing regularly.

---


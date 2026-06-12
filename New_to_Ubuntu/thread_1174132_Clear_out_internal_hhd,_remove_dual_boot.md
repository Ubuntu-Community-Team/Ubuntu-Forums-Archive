---
title: "Clear out internal hhd, remove dual boot"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by ChemShock on 2009-05-30
Ok, what I want to do is wipe everything off my drive including both OS. I think I royally screwed things up and since I got some time thing weekend, I was going to reinstall everything on a clean harddrive then see if I can't recreate my problem. If I can or can't fix my problem, then I want to do a fresh reinstall of Win XP and Jaunty. Any suggestions?

---

### Post by s.fox on 2009-05-30
Hi,

You could try using the LiveCD. Format the existing partition when you come to install it.  I am not so sure about the windows partition though.

-Ash R

---

### Post by anchorschmidt on 2009-05-30
Install Jaunty for the whole System. This will remove everything and then you will have a clean install of Jaunty. Then shrink the Jaunty volume using GParted and then install windows on the unallocated space. Format the free space as an NTFS drive beforehand though.

---

### Post by nandemonai on 2009-05-30
Usually easier to install Windows first as it'll wipe out grub.

---

### Post by blueridgedog on 2009-05-30
Unless you want to change partition sizes, just re-install windows onto the existing windows partition, electing to format, then re-install Ubuntu on to the existing partition structure, also electing to format.  I prefer windows first.

---

### Post by niteshifter on 2009-05-30
Hi,

Really wipe the disk, of everything? Boot from a Live CD and in Terminal use this:
```
sudo dd if=/dev/zero of=/dev/sda bs=512
```

Change /dev/sda if needed. The sudo may or may not be needed, depends on the Live CD used. Be patient, a 100's of GB hard drive will take a while.

As to reinstalling. Partition first, then install windows, then Linux. Installing Linux first, then Windows means no Linux on next boot - you'll then have to repair the GRUB install to access Linux.

---

### Post by ChemShock on 2009-06-01
I had a long weekend, but I ended up wiping it twice. Once through the Windows installer disk and another through gparted. Anyways, keep a look out for my upcoming wiki about migrating from wubi to a full dual boot because wubi has left me little suprises when I migrated.

Anyways, Windows XP was first. It says minimum is 10 GB. The reality is it takes 15 after all the updates. I minimized XP to be my gaming emulator and the rest is Ubuntu!

---


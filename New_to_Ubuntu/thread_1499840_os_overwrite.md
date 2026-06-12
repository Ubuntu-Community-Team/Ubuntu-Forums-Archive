---
title: "os overwrite"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-06-02
if I have 9,10 in  and load 9.04 over, total overwrite,no dual.
will it do a good job of wiping disc clean..???  or not??
I mean for security purposes, get rid of ALL data..

---

### Post by halitech on 2010-06-02
the only way to make sure that data is never recovered is to take the drive out and destroy it. There are programs out there that will over write the drive with zeros that you can use that is supposed to make it impossible to recover data but if you will be keeping the machine and using it then loading 9.04 and using the entire drive will be enough.

---

### Post by 3948ctyj on 2010-06-02
I have tried burning the Killdisk and others to USB and it doesnt work. I am trying to wipe a EEE pc, no cd drive.
 Is there a simple app that burns to USB easy that wipes????

---

### Post by doas777 on 2010-06-02
> **3948ctyj said:**
> I have tried burning the Killdisk and others to USB and it doesnt work. I am trying to wipe a EEE pc, no cd drive.
 Is there a simple app that burns to USB easy that wipes????

maybe DBAN? are you worried about wiping the whole disk (including freespace) or just the data currently there? if you just worried about current data, boot off any ubuntu live usb, install wipe, and use it to kill the data.

---

### Post by beast-usa on 2010-06-02
Not sure of your budget. What I did to get around all netbooks, notebooks with no drives. I bought a USB DVD burner $49.00
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5774140&CatId=483]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5774140&CatId=483") it works on everything, no AC plug needed.

Then you can download disk utilities from seagate, WD and write 0's to the drive.

I think seagate also has a USB boot utility.
But it's really easy just using the external DVD/r/rw

---

### Post by darkdragn on 2010-06-02
The really easy way is just to make any jump drive live bootable, with any linux os, and find out what your hdd reads as. I mean /dev/sda, /dev/sdb, /dev/hda, etc. And from the command line, after the jump drive is booted, do 'dd if=/dev/zero of=/dev/sdb' (or whatever the nave of the hdd you're trying to wipe is.)

Oh, any, if you want, unetbootin can get any live cd on to a jump drive... If something's medded up with the jump drive, such as one of the old os on it used syslinux, and you now want to use grub, you might have to zero it out, and reformat it before putting the os on it. (the same dd if=/dev/zero trick as up there... mainly because syslinux's mbr doesn't like being overwritten/altered, lmao)

---


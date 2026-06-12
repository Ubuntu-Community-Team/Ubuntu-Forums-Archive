---
title: "Installing Live 8.10 on a WD Passport"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by NK-Magi on 2009-02-09
I just got a 400GB WD Passport Elite the other day and I was looking into making it into a data storage and bootable Live CD to help in fixing broken PC's that cannot boot (commonly Windows machines).  Is there any way to go and create a Live version of Ubuntu on it in FAT32 and have persistent storage of about 50 to 100 gigs? I've tried the USB Startup Disk utility in 8.10 but for some reason it doesn't notice the USB Hard drive if its mounted or unmounted.

---

### Post by Gresley on 2009-03-23
I'm interested in the exact same question, having just acquired a 320gb my passport drive and loaded it with lots of data. I'm using this to carry personal stuff around for use on my company laptop when away on business. I'm getting some success using all the regular linux apps in windows via portable apps. I carry around a ubuntu live distro on a USB stick, and can boot to this instead of windows, but it would be really useful to be able to boot ubuntu from the external drive rather than take up 2 usb ports.

As above, I cant see how to create the live distro on the my passport as "create a USB startup" doesnt recognise the external drive.

I also want to make the live distro on the my passport as a copy of the distro on the usb stick, and not one from a live cd, so that I can avoid hour and hours of customisation. Any ideas gratefully received.

---

### Post by t0p on 2009-03-23
Concerning installation to a USB drive: I've made a couple of live Linux USB sticks, by using [UNetbootin]("http://unetbootin.sourceforge.net/").  Worked fine with Hardy and Intrepid. It's a great tool.

---

### Post by Gresley on 2009-03-25
Thanks for the tip, really like this as a method of setting up a live USB.

One problem though, despite now having a Ubuntu live distro on the my passport drive, and the boot sequence correct in bios, the laptop for some reason ignores the WD drive and boots into windows directly from the internal drive.

Is anyone aware of any issues concerning making the WD external drive a bootable device?

---

### Post by Gresley on 2009-11-03
For the record, I did eventually get this to work, but with a full install to a fat 32 partition on the WD drive.

I did need to fiddle around a little, in particular the IBM T60 I'm using needed a change in bios to do a full rather than quick boot sequence. The quick boot will recognise a usb stick but not a full usb hard drive for some reason.

I also fiddled around with Grub, which needs to be set up to recognise ubuntu is sitting on hd 0,4. When installing, the external drive appears as the second drive, but when booting from this drive it becomes the first drive and grub gets confused.

---

### Post by Gresley on 2009-11-03
Sorry, finger trouble, I should have said a full install to an ext3 partition, the data on the drive remains in a fat32 partition so that it can be read from a windows machine.

---


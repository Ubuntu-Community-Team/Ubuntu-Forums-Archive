---
title: "HELP my ubuntu died!!!!!!!!"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by myrnamynkoff on 2011-01-31
I need help please!!!! I´m 2 days away from my final exams, all my papers are on my computer and last night i turned it on after some updates and neither the mouse nor the keyboard were working! sooooo i took it to my mom´s technician and i don´t know what he did but i just got it back and now i can't even reach to the password initial screen. all i get is[B] 

(initramfs)

[/B]i already downloaded ubuntu netbook edition again, because the one i had was still the former edition, and i put it on a usb drive, and i changed the booting to the usb drive, but still all i get is:

(initramfs) [                 6.468412]  usb-storage: device scan complete
[   6.469066] scsi 2:0:0:0: Direct-Access Kingston DT 101 G2         1.00 PQ
: 0 ANSI: 2
[   6.470464] sd 2:0:0:0:   Attached scsi generic sg1 type 0
[   6.471237] sd 2:0:0:0:  [sdb] 7823296 512-bytes logical blocks: (4.ooGb/3.72GiB)
[   6.471975] sd 2:0:0:0:  [sdb] Write Protect is Off
[   6.472072] sd 2:0:0:0:  [sdb] Mode Sense: 03 00 00 00
[   6.472160] sd 2:0:0:0:  [sdb]Assuming drive cache: write through
[   6.474982] sd 2:0:0:0:  [sdb]Assuming drive cache: write through
[   6.475069] sdb: sdb1
[   6.477846] sd 2:0:0:0:  [sdb]Assuming drive cache: write through
[   6.477932] sd 2:0:0:0:  [sdb]Attached SCSI removable disk 


and that´s it. **help?** please? i´m completely lost and i´m afraid i might´ve lost all the information i had inside my computer :(

thanks in advance :)

---

### Post by kittkatt on 2011-01-31
If you just need your data, boot up using a Live CD or Live USB image of Ubuntu (easy to google) and transfer off the files you need to a USB stick.  Then just do your work in a computer lab for the next couple of days.

EDIT: just reread your post... are you using a usb hard drive?  or a usb stick?  Did you use Unetbootin to transfer the cd image onto your USB stick?

---

### Post by myrnamynkoff on 2011-01-31
Yes, what I was trying to do was to use a Live USB image of Ubuntu in order to resque all my files, the problem is it won´t let me go that far.

I followed the instructions here: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download) in order to make the startup disk. I used a USB stick, and I set it up with the program that the website mentions: Universal USB Installer..... 

Any idea of why I can´t even use a live image of ubuntu?  :/

---

### Post by Rubi1200 on 2011-01-31
Did you change the settings in BIOS to allow booting from the USB first?

As the computer starts, you will see the POST screen (the one which has the name of the manufacturer), press F2, F12, Esc, Del or whichever key works with your particular model.

There should be a screen in there called Boot or something similar. Check to make sure you can boot from the USB and set it as first boot device.

---

### Post by myrnamynkoff on 2011-01-31
ok. so i finally got to run the Live USB image of Ubuntu, but now comes  problem number 2: I can´t find any sign at all of my data, not even the  disk, or the disk partitions..

So I opened a terminal, and tried sudo fdisk -l, i get to see the disks  partitions there. tried unmounting them (sudo umount -a), but the result  was 'device is busy', tried sudo mount -l and this is what i got:
[B]
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs  (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat  (ro,noatime,fmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)  [PENDRIVE]
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)[/B]


i'm now stuck there..... any idea of what else could i try in order to get to my files?

thanks :)

---

### Post by myrnamynkoff on 2011-01-31
(also, just wanted to add that if i try to access ls /media, it´s like the disk is empty, it gives me back the ubuntu@ubuntu line, so it seems like is not mounted, but at the same time it doesn´t let me do anything, like unmounting it or mounting it all)

---

### Post by Rubi1200 on 2011-02-01
From the LiveCD, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by myrnamynkoff on 2011-02-01
thank you Rubi1200!! :)

I think i got it, i don´t know how i did though... but i was following your instructions and suddenly i saw a folder and i could access my disk, so i saved all my data. Now i´m going to look here on the forum for instructions on how to format the whole disk and reinstall ubuntu again, yey! my little computer will be as good as new soon! :D

thanks again for your help my friend :)

---

### Post by Rubi1200 on 2011-02-01
You are more than welcome :-)

Glad you managed to save your data and get things going again.

If you need more help with anything, just ask.

---


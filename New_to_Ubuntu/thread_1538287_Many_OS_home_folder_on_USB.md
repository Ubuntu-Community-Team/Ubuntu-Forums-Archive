---
title: "Many OS home folder on USB??"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-24
Hello.  I have a few questions acutally.  One of them is, you know those tiny USB receivers that sometimes come with mice, where you can't even tell it's there, other than the USB port isn't avaliable anymore?  Do they have those in Flash Drives?  I would like to obtain a 16GB one, if there are some.  Also, is it possible to set up Linux where my home folder is on the USB drive, and the other distros don't have a home folder?  I would like to have one home folder, on the flash drive, and keep it plugged in all the time, and have a few different distros running....  My thought is, if needed, I could pull out the flash drive, and plug it into another computer and exchange files.  But I need to know if it's possible to host my single home folder (for many Linux OSs) on a single flash drive, and if I can in turn, (while my laptop is off) plug it into Windows computers to exchange files?  If so, could somebody outline how I should go about doing this?  Thanks!!

---

### Post by ankspo71 on 2010-07-24
Hi,
Yes, there are _[usb flash drives (link)]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=522&Tpk=usb flash drives")_. It's even possible to install an entire linux system on one of those. [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) The closest I have come to using a flash drive is an SD card though, so I can't say I am speaking from experience. ;)

I finally understood the question about the single home folder to be shared among multiple linux'es (not multiple home folders being shared like I thought you asked), so you can ignore what I originally said. The problem here would be getting each system to mount that USB home directory...

---

### Post by ankspo71 on 2010-07-24
Here are 2 links that might help you with a home partition on a usb flash drive.

HOWTO: Persistent home on USB key
[http://ubuntuforums.org/showthread.php?t=9893](http://ubuntuforums.org/showthread.php?t=9893)
(this shows that it is possible to use a usb drive as a home partition.)

set /home to usb device?
[http://ubuntuforums.org/showthread.php?t=529573](http://ubuntuforums.org/showthread.php?t=529573)

---

### Post by sgosnell on 2010-07-24
The closest I know of to a hidden flash drive is an SD card.  I keep one in my slot almost all the time.  I use an SD card for installing different Linux distros, often the latest Ubuntu alpha or beta, for trial without affecting my internal drive.  If you don't have an SD slot, the next closest that I know of is a microSD card with a small card reader, plugged into the USB port.  That's probably not as small as you want, but that's about all that is available.  You can easily mount any drive or partition as /home through fstab.

---

### Post by k3lt01 on 2010-07-25
I personally wouldn't have multiple OSs use the same /home folder. Each OS can have its own settings that may not be compatible with other OSs and cause conflicts. Even with different versions of Ubuntu (current and development/testing) I run separate /home partitions.

---

### Post by C.S.Cameron on 2010-07-25
Ubuntu, Mint, Xubuntu, Kuubuntu, etc will all use a home-rw partition for persistence when booting from a Live USB.
However when these are all installed as bootable iso's on the same flash drive, (see MultiBootUSB), you end up with a mess using a single home-rw.

---

### Post by CaptainMark on 2010-07-25
these a good if you want a small usb drive [http://www.play.com/PC/PCs/4-/13953903/Verbatim-Store-n-Go-Micro-8GB-USB-Flash-Drive/Product.html#](http://www.play.com/PC/PCs/4-/13953903/Verbatim-Store-n-Go-Micro-8GB-USB-Flash-Drive/Product.html#)

---

### Post by oldfred on 2010-07-25
/home has to be linux formated, ext3, ext4 or other but not FAT or NTFS for windows. Windows will not read it.

You should not share /home as the settings may not be compatible with other systems (unless you use different user names defeating the ideal of same data).

Why not just create a /shared partition and save all your data to that. I have both NTFS and EXT3 shared and data partitions that I mount in several installs (not on USB though). Not sure if USB missing what happens to any automounts in fstab.

---


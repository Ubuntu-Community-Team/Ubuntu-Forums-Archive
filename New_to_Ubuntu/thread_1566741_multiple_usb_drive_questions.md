---
title: "multiple usb drive questions"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-09-02
i have a 4 gb external usb drive that i need to format, for some reason ubuntu cant do that so i downloaded the program "Gnome format" but nothing happens when i click on the icon. how can i format my external usb drive?  i was also wondering if it is possible to download the universal usb installer program from [www.pendrivelinux.com](www.pendrivelinux.com) the program is made for windows i know, i think i can transfer it to windows because i use a duel boot computer. the problem is downloading the program.  i was also wondering if it is possible to have a partition on that 4 gb usb because i cannot use it for storage if it has ubuntu live install on it. if anyone knows about this type of thing it would be great.

---

### Post by Smart Viking on 2010-09-02
> **ornothaloapq said:**
> i have a 4 gb external usb drive that i need to format, for some reason ubuntu cant do that
Try to use gparted(also, you need to unmount the drive to format it)
```
sudo apt-get install gparted
```> **ornothaloapq said:**
> 
i was also wondering if it is possible to download the universal usb installer program from [www.pendrivelinux.com]("http://www.pendrivelinux.com") the program is made for windows i know, i think i can transfer it to windows because i use a duel boot computer. the problem is downloading the program.
I don't really see what you mean. Anyways, if you want to create a bootable usb i suggest you use unetbootin, it have both a linux and windows version, to install it in ubuntu run this command:
```
sudo apt-get install unetbootin
```> **ornothaloapq said:**
> i was also wondering if it is possible to have a partition on that 4 gb usb because i cannot use it for storage if it has ubuntu live install on it. if anyone knows about this type of thing it would be great.
Yes it is possible, you would create the partition the same way you would create any other partition(althrough i don't think it would be a problem to store files on the same partition?). :)

---

### Post by C.S.Cameron on 2010-09-02
gparted +1

If you use the Start Up Disk Creator that comes on the Live CD you can make an USB install that saves changes.

Both UNetbootin and usb-creator use FAT32 filesystem, so you can use the root partition for storage.
When booted from the disk you have to look in cdrom to find things that were copied from a Windows computer.

---

### Post by ornothaloapq on 2010-09-02
i cant unmount the usb drive i get this error message    "Could not unmount /dev/sdc1" "Text ended before matching quote was found for ". (The text was 'sh -c 'umount -v "/media/JOEL'S_USB"'')"

---

### Post by oldfred on 2010-09-03
When you labeled your flash drive did you actually put the quote in the label. I think that is confusing the system. Try and see if disk utility will let you relabel it. It may not have to be unmounted to change label name.

The unetbootin installer is quick & easy but as you have noticed the flash drive is mostly dedicated to your one install. If you only have a 1 or 2GB flash that is ok, but with 4GB or more it can be a waste.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by Smart Viking on 2010-09-03
> **ornothaloapq said:**
> i cant unmount the usb drive i get this error message    "Could not unmount /dev/sdc1" "Text ended before matching quote was found for ". (The text was 'sh -c 'umount -v "/media/JOEL'S_USB"'')"
Don't use special characters in your usb's name, rename it.

If you rename it to lets say "usb", then the commend to unmount the drive would most likely be:
```
sudo umount /media/usb
```
:)

---


---
title: "HELP! Formatted 1TB USB drive with Gnome Format and now I can't do anything with it!"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by oldrocker99 on 2009-10-16
I just bought a Seagate 1TB external drive and intended to format it to ext2 so I could copy over my /home directory, which has some files which are >4GB. My first mistake was using Gnome Format instead of fdisk, I suppose, but, upon finishing, the drive couldn't be mounted and is now invisible. 

I tried "fdisk /sde1" and got

mount: can't find /dev/sde1 in /etc/fstab or /etc/mtab

and, sure enough, nothing there.

If I try Gnome Format again, I get 

/dev/sde: unrecognized disk label

In other words, I am stuck. Anyone who can help, let me know!

:guitar:

---

### Post by nkingcade on 2009-10-16
I think I had this problem a while back. Unplug the drive and plug it back in the machine. The machine should recognize that something new exists. Then, go to the properties for the device and make sure you have permission to configure it. (READ And WRITE) Try that and I'll look through my threads to see if I can find the answer I was given. 

Neal

---

### Post by nkingcade on 2009-10-16
Found it. Please go to this location and load this utility. It will allow you to partition and format the drive. Let me know if this works for you. Whoops. 

Here is the link: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Neal

---

### Post by kwacka on 2009-10-16
as it's a harddrive, is gparted any use?

---

### Post by oldrocker99 on 2009-10-16
Thanks for the swift replies. I'm downloading GPartEd as I type and am then crossing my fingers.

The community comes through AGAIN!):P


:guitar:

---

### Post by nkingcade on 2009-10-16
gparted is the utility for partitioning and formatting harddrives both internal and external. Once it discovers the device it will display it. You then select it and right mouse to format. Try that.

Neal

---

### Post by oldrocker99 on 2009-10-16
OK, I booted with the gparted live disk and successfully created a partition, then formatted it as ext2. It shows up when I rebooted. I gksudoed Nautilus to change to permissions to me and my group. I'm able to drop-and-drag a folder to copy it, but am unable to CTRL-C and CTRL-V to copy it, nor am I able to create a new folder. 

I mean, so far so good, but a few niggles remain.

:guitar:

---

### Post by redbook4574 on 2009-10-16
> **oldrocker99 said:**
> OK, I booted with the gparted live disk and successfully created a partition, then formatted it as ext2. It shows up when I rebooted. I gksudoed Nautilus to change to permissions to me and my group. I'm able to drop-and-drag a folder to copy it, but am unable to CTRL-C and CTRL-V to copy it, nor am I able to create a new folder. 

I mean, so far so good, but a few niggles remain.

:guitar:

I always find it better to format externals as fat32 or ntfs this gives the added advantage of being compatible with other systems (dare I say it, windows). I have always had trouble with ext2 externals.

---

### Post by oldrocker99 on 2009-10-16
> **redbook4574 said:**
> I always find it better to format externals as fat32 or ntfs this gives the added advantage of being compatible with other systems (dare I say it, windows). I have always had trouble with ext2 externals.

Hmmm... I had nothing but trouble in my XP days when I tried to format an external HD in NTFS. Again, the reason I used ext2 is that I have files in my /home directory which are => 4GB, which FAT32 won't handle.

Also, I won't go back to Windows at gunpoint since I went to Ubuntu.

:guitar:

---

### Post by redbook4574 on 2009-10-16
I have 2 x 1tb externals both ntfs, they both work fine, formatted via gparted. they should support 4gb files no problem. failing that try ext3.

---

### Post by oldrocker99 on 2009-10-16
> **redbook4574 said:**
> I have 2 x 1tb externals both ntfs, they both work fine, formatted via gparted. they should support 4gb files no problem. failing that try ext3.

I had, in fact, thought my sda (system) disk was ext2, when in fact it is ext3. I can always reformat. Thanks.

:guitar:

---


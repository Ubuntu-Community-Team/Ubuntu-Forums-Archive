---
title: "Installing Windows 7"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by bhargava.ankush26 on 2011-08-31
Hello, 

I am a noob at Linux.. I had a college project and thought of using the Linux environment to develop my project.. So, I formatted my hard disk and installed Ubuntu 10.04 on it (ASUS K52F Laptop).. Recently, I received an industrial project that I need to work on.. And that projects needs me to use various Microsoft-Windows Software (Tried Wine but it did not work).. I have a Windows 7 DVD but when I insert it and try restarting my system, it does not boot.. Ubuntu Starts automatically.. I tried the same with my pen-drive but the result is the same.. I checked the boot order that was like CD/DVD first preference, Flash Drives Second Preference and Hard-disk Third Preference... So nothing wrong with the Boot order.. Can anyone please help me.. Both the projects are very important and urgent for me.. So I need both the Operating Systems.. Ubuntu as well as Windows 7.. 

NOTE: I tried using Virtual Box also.. But even that did not work well.. :(

---

### Post by uRock on 2011-08-31
Your BIOS should show which key to use to interrupt the boot process and allow you to manually select which device to boot from.

---

### Post by Jesus_Valdez on 2011-08-31
What went wrong with Virtual Box? 

anyway, there's an old HOWTO in the forum: &#8220;How to&#8221; Dual boot Ubuntu and Windows 7 (Ubuntu installed first) 

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Don't know how up to date is, but I think is a good start.

---

### Post by Mark Phelps on 2011-08-31
One thing you should know BEFORE you attempt to install Win7 (presuming you are able to get your laptop to boot from DVD) is that Win7 will NOT be able to understand the existing Linux filesystem, thus the only option it will probably give you is to erase the entire drive -- which, from what you said, is NOT what you want to do.

So, before that, you should boot using an Ubuntu CD and use the Partition Editor to shrink the Linux partitions to make room for Win7.

---

### Post by elliotn on 2011-08-31
if you sure win7 was installed correctly you should update grub and grub will list your win7 when u boot

---

### Post by elliotn on 2011-08-31
> **elliotn said:**
> if you sure win7 was installed correctly you should update grub and grub will list your win7 when u boot

oops didn't read the whole post

---

### Post by pierreyy on 2011-08-31
try to access the bios menu, and from there tell ur computer to boot from the cd... anw to boot from the cd its usually either f2, f12, or del. It should show on your booting screen with an asus logo or smthn... anw let us know.

---

### Post by Mark Phelps on 2011-09-01
If you positively can't read ANY optical media in your drive, you could use unetbootin to create a bootable Ubuntu USB stick -- and boot from that.  Once in Ubuntu, open a terminal and enter the sudo command I mentioned earlier. That will list off the partitions on your drive.

---

### Post by indyeah on 2011-09-01
Windows 7 will not install on HD previously containing ubuntu untill  u clear your HD of linux code.As someone mentioned earlier better to erase your HD and then try installing windows 7.

But before you do all that make sure to backup your data.

---

### Post by Mark Phelps on 2011-09-02
> **indyeah said:**
> ....As someone mentioned earlier better to erase your HD and then try installing windows 7.

That's NOT what I said! I said to SHRINK the existing Linux filesystem partitions to create an unallocated space for Ubuntu.  I never said to ERASE the drive.

If the Win7 installer can't understand the Linux filesystem partitions, it SHOULD be able to see the unallocated space -- and install there.

---


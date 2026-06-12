---
title: "Remove Windows XP from dual boot."
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Anthony A on 2011-07-06
I would like to remove Windows XP from my machine that I dual boot with Ubuntu 11.04. Do I just use Gparted to delete the Windows partition? What is the proper procedure? Thanks

---

### Post by lincoln32 on 2011-07-06
yes delete partition and update grub if needed simple:)

---

### Post by beew on 2011-07-06
> **lincoln32 said:**
> yes delete partition and update grub if needed simple:)

It is not that simple. What do you do with the unallocated space after Windows is deleted? I am not sure about how safe it is to move Ubuntu's root partition to the left if XP was installed first (usually the case for many dual boots) Now it may be just waiting for gparted to do its job but I think OP should get some reassurance from someone who has actually tried that. I have expanded  or shrink Ubuntu's /home partition on the right side many times but I am always a bit uneasy about moving the root partition to the left as I vaguely remember reading somewhere that this may render the installation unbootable. So instead of taking a chance when I got rid of Windows in my dual boot I simply installed Mint LMDE in in the unallocated space instead of expanding the Ubuntu partition.

---

### Post by dFlyer on 2011-07-06
Why not backup what you want to keep and just do a clean install configuring partitions the way you want them.

---

### Post by maizuddin35 on 2011-07-06
> **Anthony A said:**
> I would like to remove Windows XP from my machine that I dual boot with Ubuntu 11.04. Do I just use Gparted to delete the Windows partition? What is the proper procedure? Thanks

I think , the only way is to format the partition where the windows xp is situated. am I right?hmmm

---

### Post by beew on 2011-07-06
> **maizuddin35 said:**
> I think , the only way is to format the partition where the windows xp is situated. am I right?hmmm

No, you can just delete it with gparted and leave the unallocated space unformatted. But I  think OP would want to put something in the vacated space instead of just leaving it unallocated.

---

### Post by maizuddin35 on 2011-07-06
> **beew said:**
> No, you can just delete it with gparted and leave the unallocated space unformatted. But I would think OP would want to put something in the vacated space instead of just leaving it unallocated.

there, your problem should then solve now ;)

---

### Post by lincoln32 on 2011-07-06
I do it quite often after deleting the partition with windows you can expand the /home or / partition as you like and since grub 2, it will normally not need to be updated as it checks for all kernals on hard drive sometimes it takes a while to update so I usually just update grub manually

---

### Post by beew on 2011-07-06
> **lincoln32 said:**
> I do it quite often after deleting the partition with windows you can expand the /home or / partition as you like and since grub 2, it will normally not need to be updated as it checks for all kernals on hard drive sometimes it takes a while to update so I usually just update grub manually

I tried that once (moving a Ubuntu 10.10 / partition to the left ) and afterwords the hard drive was unbootable. Get lots of IO errors. Could be just a coincidence, but I am cautious to tell people to do that given my experience. :)

---

### Post by maizuddin35 on 2011-07-06
I never try this kind of method before. is it advisable to do this?

---

### Post by Brushstroke on 2011-07-06
You can resize/expand the space of your Ubuntu root or home partition with GParted to take advantage of the space remaining from deleting Windows. But be advised that it takes awhile and you will need to use the GParted Live CD rather than the GParted application that comes installed with Ubuntu. As long as there are no errors on the drive, you should be fine with resizing the partition and there shouldn't be any problems with booting. It's how I added a bit more swap space to my setup and it worked fine. :)

---

### Post by beew on 2011-07-06
> **Brushstroke said:**
>  you will need to use the GParted Live CD rather than the GParted application that comes installed with Ubuntu.

Why is that? I would think you can just boot from a Ubuntu live usb and use Gparted installed there.

---

### Post by Brushstroke on 2011-07-06
> **beew said:**
> Why is that? I would think you can just boot from a Ubuntu live usb and use Gparted installed there.
Yeah, that works too. :P

---

### Post by wildmanne39 on 2011-07-07
Hi, here is a guide for resizing partitions by a person who is very good at this sort of thing, and depending where the free space is located you may have to reinstall grub, that will be determined by this guide also. Yes you have to use the livecd or liveusb stick to resize your partitions but you can not be booted into ubuntu to do it.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Anthony A on 2011-07-07
From reading the responses it looks like just deleting the XP partition is no problem and I can do this from Ubuntu with Gparted. The tricky part is if I want to expand the Ubuntu partition to use up the free space created by deleting the XP partition. Well I think I will install Linux Mint alongside Ubuntu so I won't need to expand the Ubuntu partition. 

Will this work:

1) Use Gparted to delete XP partition.

2) Do nothing with the free space.

3) Install Mint and let the installer install Mint along side Ubuntu using the free space from the deleted XP partition.


Is it even necessary to delete the XP partition with Gparted before installing Mint? Couldn't I just use the Mint installer to remove XP and install Mint beside Ubuntu?

---

### Post by lincoln32 on 2011-07-07
yes but I recommend delete the partition first so it will be easy to find while installing mint or what ever you choose;)

---

### Post by beew on 2011-07-07
> **Anthony A said:**
> From reading the responses it looks like just deleting the XP partition is no problem and I can do this from Ubuntu with Gparted. The tricky part is if I want to expand the Ubuntu partition to use up the free space created by deleting the XP partition. Well I think I will install Linux Mint alongside Ubuntu so I won't need to expand the Ubuntu partition. 

Will this work:

1) Use Gparted to delete XP partition.

2) Do nothing with the free space.

3) Install Mint and let the installer install Mint along side Ubuntu using the free space from the deleted XP partition.


Is it even necessary to delete the XP partition with Gparted before installing Mint? Couldn't I just use the Mint installer to remove XP and install Mint beside Ubuntu?

3) is tricky. Instead of installing along side choose the manual partition option when installing Mint because you want to specify where the bootloader is installed.

In your dual boot situation you want only one OS to control grub. Since Ubuntu is already installed it should retain the control. When you install Mint you should choose either not to install a bootloader or, if the option is not availiable, install it in the partition where Mint is instead of the drive (i.e if Mint is in sda4, then install the bootloader in sda4 instead of sda)  Another advantage of choosing manually partition is that you can create a separate /home partition if desired.

After installing Mint you should boot into Ubuntu and run in the terminal

```
sudo update-grub
``` 

It will detect Mint and add it to the boot menu.

---

### Post by beew on 2011-07-07
Oh btw if you have decided to dual boot two Linux I would suggest something different instead of Mint because Mint is basically just Ubuntu + codecs. Mint LMDE may be more interesting but not too radically different (it is a rolling release based on Debian instead of Ubuntu), or Fedora 15 if you are more adventurous and want to try out  gnome shell (and it is non debian)

If you want to try Fedora definitely remember not to install the bootloader. The steps are basically similar.

---

### Post by sleepy3103 on 2011-07-07
I'm not an expert, but is probably defrag your Windows partition from within Windows. Then if it isn't already, is shrink the Windows partition down to half of your total hd space using the Windows partitioning software. Then soak up the extra space with your ubuntu /home partition using a live cd. Then install mint over the Windows partition, reformatting it in the process. 
  Also if your Windows has a recovery partion you may be able to use that as your / partition for mint and the main one for /home. Never tried it but it sounds logical, depending on sizes.

---


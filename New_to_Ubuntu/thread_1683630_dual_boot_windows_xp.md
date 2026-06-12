---
title: "dual boot windows xp"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by BrandenPosts on 2011-02-07
Heyy, i have ubuntu 10.10 and I just wanted some help on how to dual boot windows xp to my computer, and please explain to me in the noobiest way plz :)

---

### Post by jonnny_j22 on 2011-02-07
This is going to depend a bit on how your hard drive is partitioned. 

Run gparted (you may have to install it depending on your version of ubuntu - sudo apt-get install gparted)

look at the partition map - how many partitions are there? There will be a minimum of 2 - one swap and one root. there may be others such as /boot and /home.

Finally how many primary partitions are in use? this will be described in the list beneth the partition table. This is important because windows must have a primary partition and a hard drive can only have four. Linux however can put all of its partitions inside an 'extended' partition, which takes up only one primary slot.

---

### Post by Darkness Des on 2011-02-07
The Ubuntu team was kind enough to make it intensely simple to dual boot: Simply install it and when it asks how to set up the drive, select "Install next to other operating systems" and it will partition for you. You can even tell it how much space to use.

---

### Post by presence1960 on 2011-02-07
> **BrandenPosts said:**
> Heyy, i have ubuntu 10.10 and I just wanted some help on how to dual boot windows xp to my computer, and please explain to me in the noobiest way plz :)

Do you have ubuntu installed & want to add XP or do you have XP installed and want to add ubuntu?

---

### Post by BrandenPosts on 2011-02-07
I have ubuntu installed and want to install xp.

and for some reason it wont let me download gparted

---

### Post by presence1960 on 2011-02-08
> **BrandenPosts said:**
> I have ubuntu installed and want to install xp.

and for some reason it wont let me download gparted

You want to boot the ubuntu Live CD/USB. Choose try ubuntu. When the desktop loads open gparted (System > Administration > Gparted Partition Editor). Use gparted to shrink your Ubuntu partition. This will create space to install XP. You can leave that space as unallocated space or create a primary NTFS partition with gparted. When done reboot with the XP install CD. Install XP to the unallocated space or NTFS partition-whichever you did. When XP is installed reboot to make sure XP boots properly.

Now you will need to reset the MBR to use GRUB 2. This is because windows will have reset it to use the windows boot loader. You will not be able to boot ubuntu until you reset the MBR to use GRUB 2. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") for instructions to do so. If you are not sure what to do post back please. I can give you precise commands to run to reset the MBR after you do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---


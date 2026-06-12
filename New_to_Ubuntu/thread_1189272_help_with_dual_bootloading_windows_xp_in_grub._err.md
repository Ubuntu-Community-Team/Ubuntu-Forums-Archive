---
title: "help with dual boot/loading windows xp in grub. error 13."
date: 2009-06-16
forum: New to Ubuntu
---

### Post by jarongg on 2009-06-16
so i have been using  this tutorial ([http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)) to set up a dual boot  of linux and windows xp on my msi wind. i just got the grub reinstalled and edited the menu.lst file  to have windows xp be an option. now the problem i am having is i am getting an "error 13: invalid or unsupported executable format" when i try to boot into windows. 

i used this command 

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

to make windows xp available, but perhaps something is missing from that. does anybody have any ideas of how i could fix this?

---

### Post by jarongg on 2009-06-16
after googling around a bit i am seeing that other people have a map code for their grub that wasn't a part of the tutorial i was using. but i don't know if linux is on hd0 or hd1 or what.

---

### Post by jarongg on 2009-06-16
bump.

---

### Post by unutbu on 2009-06-16
Please run boot_info_script ([http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)) and post the RESULTS.txt file here.

---

### Post by Don1500 on 2009-06-16
Try to set the widows loader like this.

title Windows XP
root (hd0,0)                <<<<<<<<<<<< Here is the change
makeactive
chainloader +1

Ususally if you have windows installed on the same hard drive as Ubuntu, windows is in hd0,0, and hd0,1 is a partition formatted for linux (ext3). So when you look in hd0,1 for windows it is looking for a DOS file system and you would get error 13

---

### Post by jarongg on 2009-06-16
> **unutbu said:**
> Please run boot_info_script ([http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)) and post the RESULTS.txt file here.

here it is.

---

### Post by jarongg on 2009-06-16
> **Don1500 said:**
> Try to set the widows loader like this.

title Windows XP
root (hd0,0)                <<<<<<<<<<<< Here is the change
makeactive
chainloader +1

Ususally if you have windows installed on the same hard drive as Ubuntu, windows is in hd0,0, and hd0,1 is a partition formatted for linux (ext3). So when you look in hd0,1 for windows it is looking for a DOS file system and you would get error 13

does the fact that i had linux installed first change anything? also, if i were to make the changes, is there any chance it will change how it boots into linux so if it doesn't work, i won't be able to get into linux?

---

### Post by jarongg on 2009-06-16
> **Don1500 said:**
> Try to set the widows loader like this.

title Windows XP
root (hd0,0)                <<<<<<<<<<<< Here is the change
makeactive
chainloader +1

Ususally if you have windows installed on the same hard drive as Ubuntu, windows is in hd0,0, and hd0,1 is a partition formatted for linux (ext3). So when you look in hd0,1 for windows it is looking for a DOS file system and you would get error 13

actually i just went for it and changed it and it works perfectly. both os' boot up. thanks so much for your help. :D

---

### Post by Don1500 on 2009-06-16
> **jarongg said:**
> actually i just went for it and changed it and it works perfectly. both os' boot up. thanks so much for your help. :D

I was just typing that you should try it since it would not interfere with your linux boot.

---


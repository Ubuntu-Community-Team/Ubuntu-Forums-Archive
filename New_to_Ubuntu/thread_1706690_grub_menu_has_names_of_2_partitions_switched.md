---
title: "grub menu has names of 2 partitions switched"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by grayceworks on 2011-03-14
I installed kubuntu into its own partitions on my laptop drive which already had a windows recovery partition and a windows partition. Everything runs correctly except that the grub menu has mislabelled the 2 windows partitions. 

It has my main windows partition labeled as the recovery partition, and my recovery partition is labelled as the main windows partition. 

From what I can tell, it's getting this info from probing the available OS info? How can I fix this? When I checked the 30_os_prober file, it just has code to get the "LONGNAME" automatically, instead of a way for me to specify the names. 

I also looked at getting "Grub Customizer" but when I try to install it, it says it requires a bunch of other files, and then it says it is impossible to install those other files. 

Sooooo... If anyone can point out how I can update my menu the right way, since I know I'm not supposed to edit the grub.cfg file directly. (can I though, if I make a backup of it?) 

Thanks!

---

### Post by Hippytaff on 2011-03-14
If you update the grub.cfg file when you do ```
update-grub
``` all your changes will be overwritten. [You can instead update the files in grub.cfg.d]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries") which will take effect by doing ```
sudo update-grub
```

---

### Post by Mark Phelps on 2011-03-14
In addition, any time you do a routine Ubuntu update that replaces the kernel version, GRUB.CFG then gets overwritten -- again.  So, making a backup is not really a good idea.

---

### Post by oldfred on 2011-03-14
drs305 long ago posted a way, but for most he recommends the grub customizer.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

drs305 wrote a Grub 2 Tweaks guide but it's pretty geeky stuff. If you are interested in editing the Grub2 scripts to rename a title, see Section 7 of the "Tweaks" link 
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Copy entries to 40_custom from grub.cfg and edit.
Vista names reversed in grub2 menu
[http://ubuntuforums.org/showthread.php?t=1692562](http://ubuntuforums.org/showthread.php?t=1692562)

---


---
title: "Home folder out of space (hd has 60 gb left)??"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by slixz85 on 2010-12-24
hi just bootin up the computer today and tryed downloading couple iso's and my home folder says less than 1mb is left of free space but my filesystem shows 60 gb left. just wondering how i can fix this so i can put more into my home folder. thanks

---

### Post by Verbeck on 2010-12-24
is your /home on a separate partition?
also, post the output of* df -h* from a terminal

edit: try emptying the trash as well

---

### Post by slixz85 on 2010-12-24
yes it is on a seperate partition i have zorin, linux mint and ubuntu

been installin os's like crazy to try them all out. must have done somethin with the /home. is there anyway at all to have all the linux os's share the same home directory?

---

### Post by slixz85 on 2010-12-24
just needing them to share for instance. i use one os for gaming only so nothing else can slow it down, then i use one for normal downloading stuff to the home folder music isos videos etc
and the last one is used alot also but kind of like another space in case i wanna try out more os's.

---

### Post by 3rdalbum on 2010-12-24
For trying out multiple operating systems, why not use something like Virtualbox?

---

### Post by Girya on 2010-12-24
you need to edit your /etc/fstab file(s) to mount your home partition. backup your current fstab files before you start editing that way you can restore them from a live cd if you mess something up. 

this is what mine looks like with seperate partitions for /music, /video, /pictures and /home. ((tabs don't show up in the code block)



> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=927eaacf-64d4-46fc-ad02-afe0bf1052f6 /               ext4    errors=remount-ro 0       1
UUID=024ad244-2b23-4d9a-abaf-2662586d2250	 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=1c3ed51c-899b-404b-9e57-d635a68ac9b5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#music mount
UUID=34c2d906-0716-43ab-883b-872079424ca1	/music		ext4	defaults0	2

#video mount
UUID=fb4f56c4-dbf2-485b-8bb6-656c049f17dd		/video		ext4	defaults	0	2

#pictures mount 
UUID=7f68a464-443b-43fa-ab0a-9202f3d158f1		 /pictures	ext4	defaults	0	2


to find the UUID type: ```
blkid
```

just as something to think about; moving to LVM2 for hd management will solve most of your issues about space. you still have to have /boot on a regular partition. I still haven't figured out why Ubuntu doesn't set it up as default.

---

### Post by slixz85 on 2010-12-24
> **Girya said:**
> you need to edit your /etc/fstab file(s) to mount your home partition. backup your current fstab files before you start editing that way you can restore them from a live cd if you mess something up. 

this is what mine looks like with seperate partitions for /music, /video, /pictures and /home. ((tabs don't show up in the code block)





to find the UUID type: ```
blkid
```

just as something to think about; moving to LVM2 for hd management will solve most of your issues about space. you still have to have /boot on a regular partition. I still haven't figured out why Ubuntu doesn't set it up as default.




3rdalbum could you explain virtual box and girya. i am little new so would i be able to copy your post almost and use it when i edit the fstab also. if you could take the time to explain more thoroughly... thanks for input so far (<---and will i need to edit the fstab on every partition then (most likely)???

---

### Post by slixz85 on 2010-12-24
just looked it up actually still trying to understand virtualbox all the way but check this out. [http://www.virtualbox.org/attachment/wiki/Screenshots/FreeBSD_win.png](http://www.virtualbox.org/attachment/wiki/Screenshots/FreeBSD_win.png) looks just like normal linux in way installing xp inside the os. can i do this with ubuntu as well instead of having to burn iso's using unetbootin??

---

### Post by Girya on 2010-12-24
**no, don't copy my fstab file, that would be bad**. I'll spend a little time and try to explain. in nest post, just give me a bit. in the meantime look at your fstab file. and google fstab. 

in a terminal type 

```
cat /etc/fstab 
```

yes edit every fstab file. you could do it from one distro by mounting the other partitions.

---

### Post by slixz85 on 2010-12-24
appreciated. i will try in look myself but no guarantees thanks

---

### Post by mikewhatever on 2010-12-24
> **slixz85 said:**
> hi just bootin up the computer today and tryed downloading couple iso's and my home folder says less than 1mb is left of free space but my filesystem shows 60 gb left. just wondering how i can fix this so i can put more into my home folder. thanks

You should, most likely, delete some files, which will free disk space. Another way is to make the home partition larger, which involves resizing partitions. Please note that editing fstab or mounting partitions as suggested above does not free disk space.

PS: Post the outputs of the following

sudo fdisk -l 

df -h

---

### Post by Girya on 2010-12-24
after thinking about it a little more I would probably leave the home partitions mounted as they are because configuration files might be different between ubuntu, zorin and mint. instead I would create a data partition and mount that in each disto and save/move all your music, videos, pictures etc to that folder. 

so how I would do that? 

backup all the files you don't want to lose to external media, in case something goes wrong. [B]if you can't do this don't continue. 
[/B]
plan, where are you going to get the extra space to create a data partition?

use gparted from a live cd to resize a partition so you can create a new data partition.

create the data partition using gparted.

boot into your mint, zorin and ubuntu os'es and mount the data partition and copy data to that partition.

edit fstab to mount the data partition at boot.  

this would be a complex project that could easily screw up your computer so bad you could lose all your valuable data. If you do choose to undertake this project study up and make sure you understand every aspect of it. good luck

---

### Post by |Eric| on 2010-12-24
my usual strategy is to not keep any personal file in the my documents and /home folders
i use it as a "system" folder basicaly all the programs save their settigns in there and it becomes a real mess 
its much better to have a mount point in the root than mess with all the crap in your home folder. 


just like was said above 
blkid  to list the UUIDs
and then edit the fstab file (or not ) 
you can mount your partitions manualy also 
fdisk -l to list the partitions ( as root or in a sudo)

in ubuntu i make mountpoints in /media keeps all the things clean 

du /home/xyz to get the size of it . 

also note that if you have lots of small files with big inode spacing its possible to be inneficient in therms of space and have no inode left even if your not using all the space


Virtual Box is a Virtual Machine engine and games dont run well in it if they require 3d .  but for anything else it does fine .

---


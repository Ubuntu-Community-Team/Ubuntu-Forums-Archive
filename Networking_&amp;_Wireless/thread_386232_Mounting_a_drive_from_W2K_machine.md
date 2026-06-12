---
title: "Mounting a drive from W2K machine"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by TM4674wlmi on 2007-03-16
Ok so I am very very new to linux. I am trying to mount a drive off my w2k machine to my laptop. I want to mount this drive so i can stream my mp3s from my w2k to laptop (kinda like how you would do it in windows) So i went to the ubuntuguide wiki and found a set of instructions. I followed these instructions:

sudo mkdir /media/sharename
gksudo gedit /root/.smbcredentials

then edited my username and password into the .smbcredentials 
then ran these commands
sudo chmod 700 /root/.smbcredentials
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

here is how my fstab looks:
------------------------------------------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ec5e3d7e-87ea-42ce-b905-e22d364b2416 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=8eae8f48-79a1-4dfa-8113-683fc0593340 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
//svrname/F$/mp3      /media/mp3 smbfs  credentials=/root/.smbcredentials    0    0
-----------------------------------------------------------------------------------------------------------------------------------

So after i edited that file and saved it a window popped up asking me what i wanted to do and i chose to open the folder, plus now there is a HDD icon on my desktop. My problem is tho when i open that icon up it doesnt show any of my mp3s or folders that i should be seeing.
All i see is my root folder on the left side showing me /media/mp3. Im sorry if im confusing anyone im trying to describe it the best I can.  If anyone can help me it would be much appreciated. Oh and Im using KDE not Gnome if that makes a difference

Thanks

---

### Post by TM4674wlmi on 2007-03-17
Ok i solved the problem somewhat... i was looking thru my repositories and i didnt have smbfs installed, so i installed that. I still ran into some problems and couldnt connect. So i tried editing the 
/etc/fstab and changed my entry from
/svrname/F$/mp3 /media/mp3 smbfs credentials=/root/.smbcredentials 0 0 
to 
//svrname/F$       /media/mp3 smbfs  credentials=/root/.smbcredentials    0    0

for some reason i couldnt connect directly to the mp3 folder under the F$ drive so after i left it out it and ran sudo mount -a it mounted and i can stream music straight from my server :) 

I still have to navigate to the mp3 folder.. but at least its somewhat going. Not too bad for a newb :)

If anyone else has any other suggestions please let me know 

thanks

---


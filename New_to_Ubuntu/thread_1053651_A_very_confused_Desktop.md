---
title: "A very confused Desktop"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by gino on 2009-01-28
Hi,
I am running Ubuntu 8.10. For some reason ( I must have done something terribly wrong) my Desktop seems to be in "/home/gino/Music/Bach, Johann Sebastian/Desktop".
I have tried creating a directory in /home/gino called Desktop and erasing the "/home/gino/Music/Bach, Johann Sebastian/Desktop" but it appears again.
How can I solve this without disturbing the whole thing? HELP!
Thanks in advance
Gino

---

### Post by The_Real_Anna on 2009-01-28
I would re-install Unbuntu (IF THIS WAS YOUR FIRST INSTALL!)....

---

### Post by gino on 2009-01-28
Thanks Anna.....
But then I would have to back up everything (I have many megabytes of data in different folders) and reinstall software....is there an easy way?????
Cheers
Gino

---

### Post by utnubuuser on 2009-01-28
In Treminal > sudo dpkg --configure -a

---

### Post by Boomhauer on 2009-01-28
dont reinstall :)
go to a terminal and enter this in ```
cat .config/user-dirs.dirs
``` and then copy and paste what it returns here.

---

### Post by presence1960 on 2009-01-28
I am a noob myself, but you mentioned something that can help you in the future. I learned the benefits of creating a separate /home partition. This makes a reinstall super easy because your /home partition remains untouched and it contains a lot of the settings for a lot of your software too. So once you reinstall or upgrade your data is still there and when you reinstall your software all your settings will be there too. Just set up the partitions using gparted on a live cd, then on the install choose manual when the partition editor comes up. choose the partition to install Ubuntu to, select the file sytem (I use ext3) and set mount point as "/". then select the partition to be used as home, choose the filesystem (I use ext3) and set the mount point as "/home". Set your swap and continue with the install. You will have a separate /home partition when complete. There is a great how to on pychocats website but for the life of me I can't find it right now. But that is how I learned to do it. When I changed to 64 bit from 32 bit Ubuntu it made life real easy since my home partition remained intact and once I installed my programs all my settings were there as they were before. Maybe someone can point you to a tutorial, don't take my "from memory" explanation of how to do it and try it.

---

### Post by gino on 2009-01-28
Thanks Guys

after I moved the desktop again to /usr/gino. AFter this somehow again an empty Desktop folder appear in the strange location. After this I erased the weird Desktop and then I did the suggested command:

sudo dpkg --configure -a 

Then re started the machine and did the second suggestion and got

gino@gino-laptop:~$ cat .config/user-dirs.dirs
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/"
gino@gino-laptop:~$

The problem seems solved now (there is no Desktop directory in the musi/Bach directory). If there is still something weird I will come back...

thank you thank you thank you

---

### Post by presence1960 on 2009-01-28
BTW even a separate /home partition is no excuse to not back up your files. _STUFF HAPPENS_ Always back up the files you can not afford to lose or you will be sorry one day

---


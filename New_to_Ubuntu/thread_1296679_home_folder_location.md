---
title: "home folder location"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by patchido on 2009-10-20
in addition to this post
[http://ubuntuforums.org/showthread.php?t=1296233]("http://ubuntuforums.org/showthread.php?t=1296233")

i wanted also, to move everything regarding programing into a space under the other partition, what do i mean by this, i dont want that my linux partition gets full, i gave it only 5 Gib, because i wanted to make this, is there a way to set my home folder in another place? or atleast make all programs to install into another place?

---

### Post by UndefinedMind on 2009-10-20
When you install a program, using the terminal, you can select where you install it. I do not think you can actually change your /home/ folder.

Another method is to just drag and drop everything you want to move to the other partition to the other partition, delete the old symbolic link, and update it with the new path of the files.

---

### Post by bwang on 2009-10-20
This: [http://firmit.wordpress.com/2008/10/29/change-my-home-folder/](http://firmit.wordpress.com/2008/10/29/change-my-home-folder/) lets you move your home folder to a different folder. I don't know whether it works for a different partition, though.

---

### Post by patchido on 2009-10-20
> **bwang said:**
> This: [http://firmit.wordpress.com/2008/10/29/change-my-home-folder/](http://firmit.wordpress.com/2008/10/29/change-my-home-folder/) lets you move your home folder to a different folder. I don't know whether it works for a different partition, though.

i really didnt understand this but looks liek what i need

---

### Post by bwang on 2009-10-20
In a Terminal:
```
gksudo gedit /etc/passwd
```
Be careful! You need to copy everything (including hidden files) to the new home folder from your current one, or else you will not be able to boot.

---

### Post by dv3500ea on 2009-10-21
Alternatively, you could mount another partition as home, or even as something like /home/devel to contain just your programming files. You would need to back up home before doing this. This would treat your partition as your /home or /home/devel folder and store all files you put in that folder to your partition. To do this, fstab needs to be edited to include the partition. I am developing a tool to automate this (attached) which you can install. To acheive this you would need to know the location of the volume of your partition (/dev/sda*). You could then run ```
permount /dev/sda /home
``` or ```
permount /dev/sda /home/devel
``` (replacing /dev/sda with the location of the volume of your partition. Alternatively, if you have the perl-tk package installed, you can run ```
permount-tk
``` to use a GUI interface. 


DISCLAMER: I am still developing this tool, hence the poor standard of the .deb package. The tool *does* work but it (especially the GUI interface) could be improved a lot. If it causes any problems or you mount to the wrong place or with the wrong partition etc, run ```
permount --revert
```. You should back up the contents of /home before trying to mount partitions to home.

---

### Post by patchido on 2009-10-24
> **bwang said:**
> In a Terminal:
```
gksudo gedit /etc/passwd
```
Be careful! You need to copy everything (including hidden files) to the new home folder from your current one, or else you will not be able to boot.

i did this, had everything copied, but when i try to boot it woint log in, it says that the home folder needs to have 644 permissions, i believe it was 644 i really dont remeber, so now i cant boot into my account, after this i tried to boot through live cd, and i couldnt for some reason it wont load, and then i tried with windows cd to maybe format the whole cd and start again, but wont work either, i dotn know what happened, also i tried to revert it through a linux partition viewer through windows but it wont open up the partition, its really awkard, i dont have an idea what to do... plz help

---

### Post by patchido on 2009-10-25
plz, help me with this

---


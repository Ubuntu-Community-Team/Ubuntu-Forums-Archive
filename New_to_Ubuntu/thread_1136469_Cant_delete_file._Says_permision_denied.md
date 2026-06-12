---
title: "Cant delete file. Says permision denied"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by manfrom3004 on 2009-04-25
I cant delete a folder with a file in it. I even tried sudo rm -r /media/disk/WINDOWS. (yes Im triying to delet the last remnants of windows) It says permission denied, or something similar.  It says I cant delete the file. Please Help!!

---

### Post by MyR on 2009-04-25
Welcome to Ubuntu!

Partitions cannot just be "deleted" in the traditional sense.  You have to erase the partition with a partition editor (like gparted).  You can then boot to a live cd and resize your ubuntu partition to fill the empty space.  It's a good idea to back up all your data first, just in case.

peace

---

### Post by llamabr on 2009-04-25
If it's a partition, it can't be deleted, but it can be unmounted, or reformatted.

What is the exact error you're getting?  And what's the output of 

```
df
```

---

### Post by manfrom3004 on 2009-04-25
Its not a partition, itsd just a file. I dont know the exact error, because my computer is in Spanish (im trying to learn spanish). and what should I do with dr, dr and then the file or just dr

---

### Post by m_2009 on 2009-04-25
Have you tried to change the file permissions with root access?

It could be that root only has permission to read only...

---

### Post by rcayea on 2009-04-25
Just a thought...

Right click and properties and then go to the permissions tab and see if it will let you change the permissions there.

---

### Post by whoop on 2009-04-25
Are you sure /media/disk/WINDOWS is a file? Looks more like a directory to me.
try sudo rm -rf (be carefull)

---

### Post by Bios Element on 2009-04-25
> **manfrom3004 said:**
> Its not a partition, itsd just a file. I dont know the exact error, because my computer is in Spanish (im trying to learn spanish). and what should I do with dr, dr and then the file or just dr

Erm, if it's in /media it's NOT a file. I'm not sure what your doing wrong here but /media should only have partitions and devices in it. Not actual files but sym-links.

---

### Post by baizon on 2009-04-25
I think its a mounted NTFS drive. Check ```
mount
``` if there is a /media/WINDOWS drive, if yes unmount it and it will be gone :-)

---

### Post by mkrahmeh on 2009-04-25
personally i recommend using the gparted to format a partition, but there is a tweak around using the dd command. anyway, before you do anything, please post back the output of ```
df
```
**you need to be careful if the /media/disk/windows is not a partition, least you may corrupt a disk or something**

in case its not a partition, it might help to post back the output of 
```
ls -l /media/disk | grep -i windows && whoami
```

---

### Post by Spiritous on 2009-04-25
> **m_2009 said:**
> Have you tried to change the file permissions with root access?

It could be that root only has permission to read only...

Sudo before the command makes it a ROOT Command.

---

### Post by AFarris01 on 2009-04-25
guys... hes trying to delete a directory INSIDE a partition (the partition is /media/disk/ and the directory is the /WINDOWS/ dir inside /media/disk/) I highly doubt that hes got a partition mounted as /media/disk/ and another partition mounted inside it as /media/disk/WINDOWS/

Anyway...

to the OP:*the guy that suggested using 'rm -rf' is probably suggesting the best course of action in your case, if you are just trying to delete the old windows system files (which is what it looks like)... just be very careful, because rm -rf deletes EVERYTHING in the target, so you need to make sure oyu're pointing it where you want it to go.  you may also need to give the command root permissions (with sudo) because if i remember correctly, all my NTFS partitions, when mounted, assume root permissions for file access/removal (initially at least)

personally, though, to make sure you dont accidentally delete something important, i would suggest changing to the directory where the troublesome folder is located (i.e. "cd /media/disk/" in the terminal), then run the delete command as "sudo rm -rf ./WINDOWS" ... meaning:
sudo: give root permissions to what i'm about to do
rm: remove something
-rf: recursively remove folders that i'm pointing to
./WINDOWS: the folder in the current directory i'm pointing to (if you ran the cd /media/disk/)

hope that helps!

---

### Post by Spiritous on 2009-04-25
> **AFarris01 said:**
> guys... hes trying to delete a directory INSIDE a partition (the partition is /media/disk/ and the directory is the /WINDOWS/ dir inside /media/disk/) I highly doubt that hes got a partition mounted as /media/disk/ and another partition mounted inside it as /media/disk/WINDOWS/

Anyway...

to the OP:*the guy that suggested using 'rm -rf' is probably suggesting the best course of action in your case, if you are just trying to delete the old windows system files (which is what it looks like)... just be very careful, because rm -rf deletes EVERYTHING in the target, so you need to make sure oyu're pointing it where you want it to go.  you may also need to give the command root permissions (with sudo) because if i remember correctly, all my NTFS partitions, when mounted, assume root permissions for file access/removal (initially at least)

personally, though, to make sure you dont accidentally delete something important, i would suggest changing to the directory where the troublesome folder is located (i.e. "cd /media/disk/" in the terminal), then run the delete command as "sudo rm -rf ./WINDOWS" ... meaning:
sudo: give root permissions to what i'm about to do
rm: remove something
-rf: recursively remove folders that i'm pointing to
./WINDOWS: the folder in the current directory i'm pointing to (if you ran the cd /media/disk/)

hope that helps!

This.

---

### Post by m_2009 on 2009-04-25
> **Spiritous said:**
> Sudo before the command makes it a ROOT Command.
 
Yes I am aware sudo makes it a root command. But you can still set the file permissions on a file so that even root doesnt have access to delete the file without first needing to give the root account read and write access to a file.

---

### Post by manfrom3004 on 2009-04-26
I did try -rf, but i got the same error

---

### Post by manfrom3004 on 2009-04-26
I tried 
ls -l /media/disk | grep -i windows && whoami and I got back:
 drwxrwxrwx 1 root root   28672 2009-04-10 21:18 WINDOWS

---

### Post by mkrahmeh on 2009-04-26
> **manfrom3004 said:**
> I tried 
ls -l /media/disk | grep -i windows && whoami and I got back:
 drwxrwxrwx 1 root root   28672 2009-04-10 21:18 WINDOWS

in this case, the whoami part of the output is not significant, since the directory grants full permissions to all users. 
to the best of my knowledge, permissions of files override permissions assigned to the parent directory..what is the output of 
```
ls -l /media/drive/windows
``` 

to check whether you are part of the sudoers, post the output of
```
groups *your_username*
```

---

### Post by manfrom3004 on 2009-04-26
It says the directory doesnt exist for the first command and 
*my_username* adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin vboxusers
for the second one

---

### Post by mkrahmeh on 2009-04-27
dude..either you have deleted it successfully, which is exactly what you want, or you copied and pasted the command from my post without paying attention to letters' cases, commands in shell are case sensitive, meaning that windows is different than WINDOWS for a directory name :KS

---

### Post by bolucpap on 2009-04-27
There is also the possibility that the windows disk you have mounted has been mounted read only. Could you ```
cat /etc/mtab
``` and post the results here?

---

### Post by Alterax on 2009-04-27
> **m_2009 said:**
> Yes I am aware sudo makes it a root command. But you can still set the file permissions on a file so that even root doesnt have access to delete the file without first needing to give the root account read and write access to a file.

Off topic, but just in case anyone is curious on how to do this, it is done by using sudo chmod +i thefilename.  It's called the 'immutable bit', and once you set a file with this permission, the only way it can be deleted or modified is for root to remove the bit with chmod -i thefilename.

Just a pointless bit of interesting trivia you may never need...back to your regularly scheduled program.

---


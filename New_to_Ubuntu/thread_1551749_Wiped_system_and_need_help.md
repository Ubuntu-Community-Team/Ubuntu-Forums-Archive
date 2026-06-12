---
title: "Wiped system and need help"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by spillage2 on 2010-08-12
OMG Please help.

just tried to so called get my system set up to use my ipod and some dumb *** must think it funny to post instructions to wipe peeps systems. 

its deleted lots of stuff and now i can only log onto it using terminal without any gui.

i have just moved pics over from my sd cards as going on holiday tomorrow and wanted to make sure i have lots of space.

my system has two hard drives. 

could i load up the live ubuntu cd and gain access to these pictures and move them to my spare hard drive.

i know i shouldnt of trusted some idiots instructions but didnt really think that there really is peeps out there doing this to us.

never again will i trust any instructions given out that are not on these ubuntu forums.

---

### Post by jtarin on 2010-08-12
> **spillage2 said:**
> 
never again will i trust any instructions given out the the ubuntu forums.OK...have a great day!

---

### Post by shadow120 on 2010-08-12
removed

---

### Post by spillage2 on 2010-08-12
sorry just edited my post was not putting these forums down at all....i really should preview my posts before putting them live.

have now installed the live cd but dont know how to access the files due to permissions.

---

### Post by shadow120 on 2010-08-12
if you can mount the drive from the live cd open a terminal and use sudo nautilus and go to it and see if the files are still there if they arem great copy them to something and reinstall.  if not then let us know and there are data recovery programs that you can use

---

### Post by spillage2 on 2010-08-12
ok thanks shadow.


i can gain access to the files but they are locked due to the permission's.

could anyone help me with how to change the permissions on these folders.

Thanks.

spill.

edit: I can move the pics to a pen drive so the permission issue is not with the files but with the other hard drive. Its a 600gb drive split into two 300gb partitions. not sure why i cannot send any data to either of them.

---

### Post by tmos22 on 2010-08-12
Just use chmod to alter the permissions for the files

This will help

```
https://help.ubuntu.com/community/FilePermissions
```

---

### Post by sandyd on 2010-08-12
> **spillage2 said:**
> ok thanks shadow.


i can gain access to the files but they are locked due to the permission's.

could anyone help me with how to change the permissions on these folders.

Thanks.

spill.
since your using the livecd, the user is called ubuntu
```
sudo chown -R ubuntu:ubuntu /path/to/file
```should do the trick.

Note that this will allow you to access your files, however there is very, very little chance that you will be able to able to run your system with a GUI. Best chances are to take all your stuff you need and reinstall, since we don't know what has been deleted, and what needs installing. Ill take a look into it, though.

However, since you need your system in a hurry, I guess you just might as well wipe and reinstall after backing up needed files, as the chmodding commands above allow you to access your files, but will make a mess of your system if you do not chown correctly.

---

### Post by jtarin on 2010-08-12
Once in the live CD environment you will need to be root on your other system. You accomplish this by using the command "chroot".
The basics are



```
sudo chroot /mount/point /bin/bash
```

Then:
```
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
```
Then all your work will be in the terminal from here on.


be sure to unmount the proc, sysfs, and devpts when you are done w/ the chroot, then exit the chroot

```
exit
```

---

### Post by spillage2 on 2010-08-12
ok sudo chown ubuntu:ubuntu /path/to/file works but only for the file listed.  so this removes the "padlock" on that folder but all folders within it are still locked.  how do i unlock all folders within a folder without having to do this for each. I have about 30 folders in there.  sorry to be such a neewbie..just getting stressed cause im off the france first thing tomorrow and dont need this right now..

---

### Post by sandyd on 2010-08-12
> **spillage2 said:**
> ok sudo chown ubuntu:ubuntu /path/to/file works but only for the file listed.  so this removes the "padlock" on that folder but all folders within it are still locked.  how do i unlock all folders within a folder without having to do this for each. I have about 30 folders in there.  sorry to be such a neewbie..just getting stressed cause im off the france first thing tomorrow and dont need this right now..
fixed.

---


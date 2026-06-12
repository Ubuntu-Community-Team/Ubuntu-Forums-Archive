---
title: "lost my hard drive on reinstall"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Pipedreams on 2011-06-14
So i erased my windows partition and figured i would have some issues to work out afterwards. I some how disabled my secondary hard drive ( or didn't include it in the installation). I was wondering what went wrong and if someone can explain it?

---

### Post by wildmanne39 on 2011-06-14
> **Pipedreams said:**
> So i erased my windows partition and figured i would have some issues to work out afterwards. I some how disabled my secondary hard drive ( or didn't include it in the installation). I was wondering what went wrong and if someone can explain it?Hi, it sounds like you partitioned incorrectly but need more information to know for sure. Are you having boot problems now? If so post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. You could just open gparted in ubuntu or from livecd and see what partitions you have and what drives.

---

### Post by Rubi1200 on 2011-06-14
+1 to wildmanne39's suggestion to run the boot script.

The diagnostic information it contains can help us assist you with this issue more effectively.

Thanks.

---

### Post by Pipedreams on 2011-06-16
No everything works as it should ( I can even see the unity launcher now) but i just don't have a extra hard drive. I'll check out the info and keep you posted. You guys are awesome.

---

### Post by dcsoldschool53 on 2011-06-16
try this command, ```
sudo fdisk -l
```or, this one```
sudo blkid
```and give us your out put.

---

### Post by dcsoldschool53 on 2011-06-16
Another thing you can try, is open either gparted or disk utility. See if you can see the drive there. What is the drive's format, ntfs, vfat, or ext4 ?

---

### Post by oldfred on 2011-06-16
@dcsoldschool53
The outputs of fdisk & blkid are in the boot script.

      Pipedreams
Best to post contents of results.txt in your post and enclose it in code tags to preserve formating & make it easier to review. You paste file, then hightlight entire text and click on # in edit panel above, or click on # and it will add [ code] paste here [ /code] tags to paste in between.

It shows "The Monster" mounted. Unmount before adding to fstab below:
I generally suggest for Linux not to use spaces. You may want to permanently mount on reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

mkdir TheMonster

gksudo gedit /etc/fstab

Paste only one of these into your fstab - do not include comments:
What this will do is mount the partition with owner = root but with read / write permissions ( umask=007 ) granted to all local login users ( gid=46 ).
```
 /dev/sdb1 /media/TheMonster ntfs defaults,nls=utf8,umask=007,gid=46 0 0
#EDIT: If you prefer to be the owner then you can also go with this:
 /dev/sdb1 /media/TheMonster ntfs defaults,nls=utf8,umask=007,uid=1000 0 0
#Or using UUID which is prefered, this just has defaults:
UUID=3C42935F42931CA8          /media/TheMonster  ntfs-3g      defaults           0  0  

```After any edit of fstab to make sure you made no typos

sudo mount -a

If it just returns it is ok, otherwise fix errors before rebooting.

---

### Post by dcsoldschool53 on 2011-06-17
Type this command in a terminal```
mount
```It will show you everything mounted on your system. Because you are using natty, I really don't know anything about that OS. I do know that if it shows using the mount command, it is mounted. All we have to do is get you to see it.

If it is not showing there; then my question is, how did you format it. Did you use a windows disk, Ubuntu's gpart or Ubuntu's disk utility? What format did you use ntfs, vfat, or ext4 what? 

And yes fstab file is the file to use to automate the process of mounting your drives. I am guessing that you are a newbie or noob to the world of Ubuntu. All we can do is tell you how to do it, or dump enough information (website) on you, so that you can get an understand as to what we are telling you. After saying all of that:

1.) You need to backup the fstab file before making any changes to it. This way you can get back your orgin configurations.

2.) Here are two more web sites for fstab file:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

3.) Psychocats says on his/her website that internal hard drives with ntfs-format are not automatically mounted in natty, but it show you how to mount it. 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

4.) For The Monster drive, if you are using it as part of any command in a terminal, it is used in this way ```
the command /media/The\ Monster
``` for example```
cd /media/The\ Monster
```There is a space between the\ and Monster.

Forgive me for all the typing and for calling you a noob, but I hope this helps you.

---


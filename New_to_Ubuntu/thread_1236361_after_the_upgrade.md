---
title: "after the upgrade"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-08-10
I apologize for spamming you all a bit here. 

I've done the upgrade from hardy to ibex. Everything I've checked so far appears to be working fine except that I can no longer access my c drive by going to applications/wine/browse c>/  

One other concern is the rather big jump in hard disk space used, suddenly its looking like I have about 10 gigs less than before, which seems a bit much. 

Anyone else run into this difficulty?

mystmaiden

---

### Post by diablo75 on 2009-08-10
Your C: drive (the Wine C: drive, to be clear) is located in /(your home folder)/.wine/drive_c

You'll have to reveal hidden folders in your Nautilus file browser to see the files/folders that begin with a .period by pressing CTRL-H.

As for your hard drive usage, it shouldn't have changed by much, certainly not 10 gigs.  What are you using to determine the usage/difference?  In my opinion, the System Monitor (System>Administrative>System Monitor>File System tab) is a quick and easy to read display of *currently mounted* partitions.

---

### Post by 3rdalbum on 2009-08-10
> **mystmaiden said:**
> I apologize for spamming you all a bit here. 

I've done the upgrade from hardy to ibex. Everything I've checked so far appears to be working fine except that I can no longer access my c drive by going to applications/wine/browse c>/  

That's not the... er... recommended method to access your Windows partition :-)  You can access a Windows partition connected to your system, by going to the Places menu and choosing it from the list. You can do it on Intrepid, I did it from an Intrepid live CD literally yesterday :-)

---

### Post by mystmaiden on 2009-08-10
Its not a windows partition, its just my Wine c drive, which was hitherto, always accessible by going to applications/wine/browse c  - I know where it is located otherwise its just easier to use this way as installing a good deal of Poser stuff that does not come from Daz (ie free stuff created by other users) winds up having to be manually installed.  Some of the stuff from daz also winds up having to be moved because it does not always go where it is supposed to via wine program loader.

to answer diablo  - I had a look at the disk usage analyzer to see how much of the drive was in use, system monitor reflects the same amount.

myst

---

### Post by drs305 on 2009-08-10
> **mystmaiden said:**
>  I had a look at the disk usage analyzer to see how much of the drive was in use, system monitor reflects the same amount.

myst

There is a link  (DiskSpace)in my signature line for finding and recovering 'lost' free space. Perhaps some of the commands or tips could help you locate what is using the extra space. An upgrade by itself wouldn't increase your / usage by 10GB.

---

### Post by mystmaiden on 2009-08-11
drs305 - thanks, it had occurred to me earlier that maybe the problem was not the update but the troubles I had backing up. Earlier I found 12 gigs of incomplete backups on my external, I wondered if deleting them had gotten stuck in a trash bin somewhere. I tried plugging it in and going through all the trash emptying steps I knew off, found one and got rid of it. 
Then I did this according to your post:

```
mystmaiden@hal:~$ sudo find / -name '*' -size +1G
[sudo] password for mystmaiden: 
/home/mystmaiden/Desktop/ultimate-edition-2.2-x86.iso
/home/mystmaiden/.VirtualBox/HardDisks/Yehudi2.vdi
/home/mystmaiden/Music/hal1music.zip
find: `/home/mystmaiden/.gvfs': Permission denied
find: `/proc/6572/task/6572/fd/6': No such file or directory
find: `/proc/6572/task/6572/fdinfo/6': No such file or directory
find: `/proc/6572/fd/6': No such file or directory
find: `/proc/6572/fdinfo/6': No such file or directory
/media/FV-U35/2009-07-22_07.40.33.797723.hal.ful/files.tgz
/media/FV-U35_/2009-08-10_01.51.57.840525.hal.ful/files.tgz
/var/backup/2009-08-10_03.06.12.893546.hal.ful/files.tgz

```I don't know that home/mystmaiden/.gvfs is.. but I do see two things. Looks like the two media files listed there did not go to my external as they should  have. I had all kinds of trouble backing up to it today, clonezilla failed several times as did simple backup. It's ntfs so maybe that was the trouble.  Can I safely get rid of the two media/fv-u35, since I have the var backup? I also noticed earlier that in the /var file I have  the file names backup and one named backups. I  tried Home User so that file may have come from it, that had also hung up and after 12 hours when it did not complete backing up I simply closed it - could 'backups' be from it?

thanks
mystmaiden

---

### Post by drs305 on 2009-08-11
The .gvfs folder is a standard file for virtual file systems - you don't need to delete it or try to alter it. Although it can be reported in Disk Usage Analyzer as taking up space, it doesn't actually occupy physical space on your drive.

As to the files in /media, I would first make sure they are on your / drive by closing all apps and unmounting everything possible with "sudo umount -a". That should unmount all partitions that aren't "busy", including any mounted on media. At that point, there really shouldn't be anything substantial in /media and if those two files are still there some action needs to be taken.

I can't tell you what those files are, but they appear to be backup files and are definitely not part of a normal Ubuntu install, which wouldn't use /media to store anything. If you delete them, remember to empty your "root" trash bin since that is where they will end up (unless you use SHFT-DEL).

/var/backup, as you correctly surmized, is also not a standard folder for Ubuntu (/var/backups is). It appears to be another backup file that ended up in the wrong location. I have read about sbackup using /var/backup as a target folder for creating backups in some cases.

You seem to have done a good job analyzing these files. Now go and free up some disk space.  ;-)

---

### Post by qwety on 2009-08-11
You can run (with sudo)to free more space:
```
apt-get clean
apt-get autoclean
```

---

### Post by mystmaiden on 2009-08-11
Thanks for all the help everyone, I'm pleased to report the disk space is now back just where it should be, everything all clean and tidy and I'm 10 gigabytes happier. drs305, your posts were super helpful.

mystmaiden

---


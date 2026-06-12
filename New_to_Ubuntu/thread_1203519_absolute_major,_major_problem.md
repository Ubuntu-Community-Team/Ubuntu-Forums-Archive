---
title: "absolute major, major problem"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Achilles124 on 2009-07-03
I don't know what I did wrong, but suddenly my harddisks are full 100%, thunderbird is deinstalled, tomboy has disappeared. Data disappear. Cannot start firefox etc, etc, etc.
For instance, see the data from the terminal when I type: tomboy.

[DEBUG]: NoteManager created with note path "/home/ecmpeek/.tomboy".

Unhandled Exception: System.IO.IOException: Disk full. Path /home/ecmpeek/.tomboy.log
  at System.IO.FileStream.FlushBuffer () [0x00000] 
  at System.IO.FileStream.Flush () [0x00000] 
  at System.IO.StreamWriter.Flush () [0x00000] 
  at Tomboy.FileLogger.Log (Level lvl, System.String msg, System.Object[] args) [0x00000] 
  at Tomboy.Logger.Log (Level lvl, System.String msg, System.Object[] args) [0x00000] 
  at Tomboy.Logger.Log (System.String msg, System.Object[] args) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

I don't know what happened to my system but it is major.
Can somebody help, please.

---

### Post by cariboo on 2009-07-03
You probably have either a full trashcan, or to many archived packages in /var/cache/apt/archives. To clean out archived packages, open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
``` 

to check trash, in a the same terminal type:

```
cd ~/.local/share/Trash
```

remove the contents of file and info.

You can also do the same thing by going to Places-->Home Folder and pressing Ctrl-h to reveal the hidden files and directories.

---

### Post by halitech on 2009-07-03
whats the result of```
df -h
```
if you can get the terminal open again

---

### Post by Achilles124 on 2009-07-03
How is it possible that there so many files in my trash? I delete them often using the trash icon on my desktop!

---

### Post by Achilles124 on 2009-07-03
Here are the results of df -h

ecmpeek@ecmpeek-desktop:~$ df -h
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda1             142G  136G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  336K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  176K 1007M   1% /dev
tmpfs                1007M   84K 1007M   1% /dev/shm
lrm                  1007M  2,4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1,0M   32K  992K   4% /tmp
/dev/sdf2              81G   30G   51G  38% /media/disk
/dev/sdf3              71G   22G   49G  31% /media/disk-1
/dev/sdf1             148G   38G  111G  26% /media/disk-2

---

### Post by Celauran on 2009-07-03
OK, your root partition is clearly full. Let's dig a little deeper.

```
sudo du -sh /*
```

---

### Post by Achilles124 on 2009-07-03
Okay, here is the result:

ecmpeek@ecmpeek-desktop:~$ sudo du -sh /*
6,1M	/bin
55M	/boot
0	/cdrom
260K	/dev
21M	/etc
du: kan geen toegang krijgen tot `/home/ecmpeek/.gvfs': Toegang geweigerd
82G	/home
4,0K	/initrd
0	/initrd.img
0	/initrd.img.old
443M	/lib
16K	/lost+found
89G	/media
4,0K	/mnt
33M	/opt
du: kan geen toegang krijgen tot `/proc/10370/task/10370/fd/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10370/task/10370/fdinfo/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10370/fd/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10370/fdinfo/3': Bestand of map bestaat niet
0	/proc
67M	/pup_400.sfs
92M	/pup_412.sfs
513M	/pup_save.2fs
48M	/root
7,7M	/sbin
4,0K	/selinux
4,0K	/srv
0	/sys
32K	/tmp
6,3G	/usr
40G	/var
0	/vmlinuz
0	/vmlinuz.old
18M	/zdrv_400.sfs

translation: "du: cannot get access, file or map doesn't exist."

---

### Post by Celauran on 2009-07-03
> **Achilles124 said:**
> translation: "du: cannot get access, file or map doesn't exist."
That's normal. Don't worry about it.

> **Achilles124 said:**
> ```
ecmpeek@ecmpeek-desktop:~$ sudo du -sh /*
6,1M	/bin
55M	/boot
0	/cdrom
260K	/dev
21M	/etc
du: kan geen toegang krijgen tot `/home/ecmpeek/.gvfs': Toegang geweigerd
82G	/home
4,0K	/initrd
0	/initrd.img
0	/initrd.img.old
443M	/lib
16K	/lost+found
89G	/media
4,0K	/mnt
33M	/opt
du: kan geen toegang krijgen tot `/proc/10370/task/10370/fd/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10370/task/10370/fdinfo/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10370/fd/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10370/fdinfo/3': Bestand of map bestaat niet
0	/proc
67M	/pup_400.sfs
92M	/pup_412.sfs
513M	/pup_save.2fs
48M	/root
7,7M	/sbin
4,0K	/selinux
4,0K	/srv
0	/sys
32K	/tmp
6,3G	/usr
40G	/var
0	/vmlinuz
0	/vmlinuz.old
18M	/zdrv_400.sfs
```

/home is 82G and /media is 89G. You know your system better than I; does this look right? If not, keep digging deeper with du (ie. du -sh /home/*).

---

### Post by Achilles124 on 2009-07-03
that explains a lot. 160 Gig is the size of my harddisk...So probably my system is full to the brim and I have to get rid of some data.

I am already busy copying data to my external harddisk. I will delete the obsolete files of my 160 Gig harddisk.

---

### Post by Achilles124 on 2009-07-03
Okay, ty for answering you all. I have removed some files from harddisk. Now I hope that everything works again as it should be. Thanks again.

---

### Post by halitech on 2009-07-03
I'm wondering why your /var folder is 40gig in size

---

### Post by cubeist on 2009-07-03
I think the 40 Gigabytes in your /var directory is very weird.  You should drill down to find out what is in there.

For a graphical method of viewing the size of files, in your accessories menu there is a program called disk usage analyzer.


edit: late on the post,

---

### Post by Celauran on 2009-07-03
> **cubeist said:**
> I think the 40 Gigabytes in your /var directory is very weird.  You should drill down to find out what is in there.

Good catch, both of you. I had totally overlooked that. Big log files could also be indicative of larger problems elsewhere, so this definitely warrants investigating.

---

### Post by drs305 on 2009-07-03
> **Celauran said:**
> Good catch, both of you. I had totally overlooked that. Big log files could also be indicative of larger problems elsewhere, so this definitely warrants investigating.

For troubleshooting, you might take a look at the link in my signature on DiskSpace. It details some of the reasons disks unexpectedly fill up and how to deal with it.

---


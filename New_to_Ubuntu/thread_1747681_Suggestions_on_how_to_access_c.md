---
title: "Suggestions on how to access c:"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Madmeeko on 2011-05-02
I thought I would try using Ubuntu because I was unable to start my laptop, running Windows XP, after getting the message that the windows\system32\config\system file was missing or corrupt.
 
After several attemps to repair I thought I'd try to use Ubuntu to access the files, fix if possible or at least retreive any files I could. Now I am finding that I am unable to access the c: at all.
 
Any suggestions on how to access c: would be greatly appreciated. Thank you

---

### Post by sandyd on 2011-05-02
> **Madmeeko said:**
> I thought I would try using Ubuntu because I was unable to start my laptop, running Windows XP, after getting the message that the windows\system32\config\system file was missing or corrupt.
 
After several attemps to repair I thought I'd try to use Ubuntu to access the files, fix if possible or at least retreive any files I could. Now I am finding that I am unable to access the c: at all.
 
Any suggestions on how to access c: would be greatly appreciated. Thank you
When you start ubuntu from the livecd, C: should show up as XX Disk in "Places".
XX being the name of the disk (normally, the size)

---

### Post by Skaggz on 2011-05-02
Linux doesn't use C: D: etc.  Your C: drive is most likely named dev/sda1

The simplest, graphical, way to access your Windows partition is through Nautilus.  On the places menu, is there one that says "xxx GB Filesystem"?  Where xxx equals the size of the C: partition in gigabytes

---

### Post by K_45 on 2011-05-02
If it isn't automounting in the live cd, run this command to see if the HDD is actually recognized from the live CD:

```
sudo fdsik -l
```

Did the XP problem mention anything about missing an NTDLR bootloader?

---

### Post by Madmeeko on 2011-05-03
Thanks everyone. I think I got it to read what was formerly known as my c: drive. It's called WindowsXP now.
 
New issue is that all of the documents that were on that drive are no where to be found.
 
Is it possible that whatever caused the error code I originally got when Windows would not boot (windows\system32\config\system missing or corrupt) be resposible for the data loss?
 
 
> **K_45 said:**
> If it isn't automounting in the live cd, run this command to see if the HDD is actually recognized from the live CD:
 
```
sudo fdsik -l
```
 
Did the XP problem mention anything about missing an NTDLR bootloader?
 
Thanks for recommending the code but the newb in me has no idea how to run it :)
 
The only other message that I got was that there was an error caused by partmgr.sys

---

### Post by K_45 on 2011-05-03
Well if its recognized, have you looked through the drive for your files?

---

### Post by BertN45 on 2011-05-03
Probably you can find your files in the following directories: Documents and Settings -> <your userid> -> My Documents

---

### Post by jramshu on 2011-05-03
> **Madmeeko said:**
> Thanks for recommending the code but the newb in me has no idea how to run it :)
That is a command you would run in the terminal window.
If you are using Ubuntu 10.10 go to Applications>Accessories>Terminal
I'd have to load 11.04 to guide you exactly.

It will be a dark purple box.
Type in the code, or copy/paste it.
Not sure what the live cd password is though, but I'm sure that won't be hard to get from the forums.

EDIT: Just read that the livecd doesn't ask for the sudo password.

---

### Post by jramshu on 2011-05-03
On 11.04 terminal can be found by clicking the "+" icon at the bottom left, then start typing "terminal" in the search area. It will be a black box that says "terminal." After it opens type the command or copy/paste.

```
sudo fdisk -l
```

You should see something similar to this:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1b4a48f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       28569   229476320    7  HPFS/NTFS
/dev/sda2           37493       38913    11411456    7  HPFS/NTFS
/dev/sda3   *       28569       37239    69637121    f  W95 Ext'd (LBA)
/dev/sda5           28569       28831     2107392   82  Linux swap / Solaris
/dev/sda6           28832       31443    20972544   83  Linux
/dev/sda7           31443       37239    46555136   83  Linux

Partition table entries are not in disk order
```

---

### Post by Madmeeko on 2011-05-10
> **jramshu said:**
> On 11.04 terminal can be found by clicking the "+" icon at the bottom left, then start typing "terminal" in the search area. It will be a black box that says "terminal." After it opens type the command or copy/paste.
 
```
sudo fdisk -l
```
 
You should see something similar to this:
 
[CODE]
 
Thank you! I was able to get everything to list but unfortunately I get 'permission denied' if I try to access the drive.
 
The message I get is:
 
bash: /dev/sda2: Permission denied  :(

---

### Post by rkillcrazy on 2011-05-10
> **Madmeeko said:**
> Thank you! I was able to get everything to list but unfortunately I get 'permission denied' if I try to access the drive.
 
The message I get is:
 
bash: /dev/sda2: Permission denied  :(

Did it give anymore info?  I've seen systems nag about "dirty drives" when I'd try to recover data from a busted Windows install.  I used to run a script to force the mounting of the HDD anyway...  I've never seen that error for anything other than a dirty drive (usually seen when one has to force the Windows system down hard.) and I've used a Live CD to recover a lot of data from broken Windows installations!  Other than that, I can't see NTFS permissions keeping you from getting to your data.  Was that Windows system running any sot of other encryption software?

---

### Post by MDguy on 2011-05-10
Try mounting the drive, open a terminal and run:
```
sudo mount /dev/sda2 /mnt
```
 
Then go to Places->Computer->File System and open the "mnt" folder, and you should be able to see your Windows files.

---

### Post by Madmeeko on 2011-05-11
> **MDguy said:**
> Try mounting the drive, open a terminal and run:
```
sudo mount /dev/sda2 /mnt
```
 
Then go to Places->Computer->File System and open the "mnt" folder, and you should be able to see your Windows files.
 
 
Thanks. I can see all the Windows files only, meaning the ones that would be used to run Windows. All other files including program files, documents, pictures, music, etc are not there.
 
> **rkillcrazy said:**
> Did it give anymore info? I've seen systems nag about "dirty drives" when I'd try to recover data from a busted Windows install. I used to run a script to force the mounting of the HDD anyway... I've never seen that error for anything other than a dirty drive (usually seen when one has to force the Windows system down hard.) and I've used a Live CD to recover a lot of data from broken Windows installations! Other than that, I can't see NTFS permissions keeping you from getting to your data. Was that Windows system running any sot of other encryption software?
 
 
No, it didn't give any other information and there was no other encryption software.
 
 
I am so stumped on this its insane. ](*,) Whatever virus nailed my computer did a damn good job

---

### Post by rkillcrazy on 2011-05-11
> **Madmeeko said:**
> Thanks. I can see all the Windows files only.

Yeah, that's odd...  I've only see that with corrupt HDDs or systems where someone has messed up an install and %WinDir% ended up on some other partition.  Did you have any other partitions on that HDD?

Can you copy/paste the readout from your **terminal** window when you do a **sudo fdisk -l** so we can see what your system sees?

Do you hear any odd sounds (clicking, perhaps?) coming from the area where the HDD sits inside the machine?

---

### Post by Madmeeko on 2011-05-11
> **rkillcrazy said:**
> Yeah, that's odd... I've only see that with corrupt HDDs or systems where someone has messed up an install and %WinDir% ended up on some other partition. Did you have any other partitions on that HDD?
 
Can you copy/paste the readout from your **terminal** window when you do a **sudo fdisk -l** so we can see what your system sees?
 
Do you hear any odd sounds (clicking, perhaps?) coming from the area where the HDD sits inside the machine?
 
 
No odd sounds other than the usual reading disk sounds. Here is the readout from the terminal window
 
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d384d37
Device Boot Start End Blocks Id System
/dev/sda1 * 1 10824 86943748+ 7 HPFS/NTFS
/dev/sda2 10826 12030 9679162+ c W95 FAT32 (LBA)
/dev/sda3 12031 12161 1052257+ d7 Unknown
 
Oh, and I'm running Ubuntu off a live cd. It isn't installed on my comptuer.
 
 
Thank you so much!

---

### Post by rkillcrazy on 2011-05-11
> **Madmeeko said:**
> No odd sounds other than the usual reading disk sounds. Here is the readout from the terminal window
 
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d384d37
Device Boot Start End Blocks Id System
/dev/sda1 * 1 10824 86943748+ 7 HPFS/NTFS
/dev/sda2 10826 12030 9679162+ c W95 FAT32 (LBA)
/dev/sda3 12031 12161 1052257+ d7 Unknown


Ok, again, in a terminal window, run **mount** and copy/paste the output back here.

---

### Post by Madmeeko on 2011-05-11
> **rkillcrazy said:**
> Ok, again, in a terminal window, run **mount** and copy/paste the output back here.
 
 
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /mnt type vfat (rw)
/dev/sda1 on /media/WindowsXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
ubuntu@ubuntu:~$

---

### Post by rkillcrazy on 2011-05-11
> **Madmeeko said:**
> ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /mnt type vfat (rw)
/dev/sda1 on /media/WindowsXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
ubuntu@ubuntu:~$

Anyone is welcome to jump in here....  After all, I'm no expert with Linux.  I've dealt with Windows far longer....

So, again, not being an expert, it looks like **/dev/sda1** might be the Windows partition.  **/dev/sda2** looks like it's mounted incorrectly though - unless that's a thumb drive or something.  I've never seen anything mounted directly to **/mnt** so if anyone knows better than I, please speak up.

Open a terminal window again and list the contents of **/media/WindowsXP** and copy/past back here: ```
ls -l /media/WindowsXP
```

---

### Post by rkillcrazy on 2011-05-11
I'm not sure why I didn't think of this before but you said you were using the Live media...  If that's the case, if you go to **System > Administration**, you should find an app called **GParted**.  I guess if Unity is running, you could just search for it as well.  Anyway, it should open up and look something like the screen-shot I've attached.  **BE CAREFUL; DO NOT MAKE CHANGES HERE.**  This is a powerful tool and you can delete whole partitions full of data with this tool.  It's also a very good and easy visual representation of your HDD(s).

If you have more than one HDD, you will be able to select them via the drop-down menu in the upper right corner.  Poke around that and see which HDD has a pretty good sized NTFS (or maybe FAT32) partition.  That should be where your data is.  If you look at my example, you see a 40-GB NTFS partition with 18.72-GB in use.  

Sorry I made you do all the command-line before....  It's good to know it but sometimes it's good to have a visual representation.

---

### Post by Madmeeko on 2011-05-11
> **rkillcrazy said:**
>  
Open a terminal window again and list the contents of **/media/WindowsXP** and copy/past back here: ```
ls -l /media/WindowsXP
```
 
I really appreciate you trying to help.
 
Here it is ...
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ls -l /media/WindowsXP
ls: cannot access /media/WindowsXP/sqmnoopt07.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt09.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt12.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt14.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata03.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata07.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata08.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata13.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata14.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata16.sqm: Input/output error
total 3317412
drwx------ 1 ubuntu ubuntu          0 2006-08-21 06:24 bby
-rw------- 1 ubuntu ubuntu        211 2006-08-20 10:24 boot.ini
drwx------ 1 ubuntu ubuntu     552960 2011-04-21 15:02 Config.Msi
drwx------ 1 ubuntu ubuntu       4096 2008-11-14 03:22 Documents and Settings
drwx------ 1 ubuntu ubuntu      16384 2009-08-06 06:39 ec0f529251c91392942cf2ca2e
drwx------ 1 ubuntu ubuntu          0 2006-11-22 02:31 f05ca23eeeb1bd2e8b
-rw------- 1 ubuntu ubuntu 1063374848 2011-04-23 14:30 hiberfil.sys
drwx------ 1 ubuntu ubuntu          0 2006-08-20 10:26 hp
-rw------- 1 ubuntu ubuntu       1402 2011-04-24 14:45 hpqp.ini
drwx------ 1 ubuntu ubuntu    1196032 2006-08-20 05:12 I386
-rw------- 1 ubuntu ubuntu          0 2010-07-01 21:18 IO.SYS
-rw------- 1 ubuntu ubuntu          0 2010-07-01 21:18 MSDOS.SYS
-rw------- 1 ubuntu ubuntu      47564 2004-08-04 21:00 ntdetect.com
-rw------- 1 ubuntu ubuntu     250048 2008-11-01 19:09 ntldr
-rw------- 1 ubuntu ubuntu 1598029824 2011-04-23 14:30 pagefile.sys
drwx------ 1 ubuntu ubuntu      28672 2011-05-10 17:22 Program Files
drwx------ 1 ubuntu ubuntu          0 2009-08-04 13:53 RECYCLER
-rw------- 2 ubuntu ubuntu  733168699 2010-08-28 02:35 Salt (2010).mp4
-rw------- 2 ubuntu ubuntu        268 2010-08-17 06:16 sqmdata00.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-18 07:00 sqmdata01.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-19 07:34 sqmdata02.sqm
-????????? ? ?      ?               ?                ? sqmdata03.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-21 07:22 sqmdata04.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-22 07:37 sqmdata05.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-23 05:41 sqmdata06.sqm
-????????? ? ?      ?               ?                ? sqmdata07.sqm
-????????? ? ?      ?               ?                ? sqmdata08.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-26 07:56 sqmdata09.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-27 07:09 sqmdata10.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-28 08:19 sqmdata11.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-29 08:26 sqmdata12.sqm
-????????? ? ?      ?               ?                ? sqmdata13.sqm
-????????? ? ?      ?               ?                ? sqmdata14.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-12 12:29 sqmdata15.sqm
-????????? ? ?      ?               ?                ? sqmdata16.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-16 06:55 sqmdata17.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-13 07:30 sqmdata18.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-14 06:11 sqmdata19.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-20 07:24 sqmnoopt00.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-21 07:22 sqmnoopt01.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-22 07:37 sqmnoopt02.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-23 05:41 sqmnoopt03.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-24 07:50 sqmnoopt04.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-25 08:00 sqmnoopt05.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-26 07:56 sqmnoopt06.sqm
-????????? ? ?      ?               ?                ? sqmnoopt07.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-28 08:19 sqmnoopt08.sqm
-????????? ? ?      ?               ?                ? sqmnoopt09.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-30 08:05 sqmnoopt10.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-11 07:35 sqmnoopt11.sqm
-????????? ? ?      ?               ?                ? sqmnoopt12.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-13 07:30 sqmnoopt13.sqm
-????????? ? ?      ?               ?                ? sqmnoopt14.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-15 06:43 sqmnoopt15.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-18 07:00 sqmnoopt16.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-19 07:34 sqmnoopt17.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-16 06:55 sqmnoopt18.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-17 06:16 sqmnoopt19.sqm
drwx------ 1 ubuntu ubuntu       8192 2006-08-20 10:38 SwSetup
drwx------ 1 ubuntu ubuntu       4096 2006-08-20 10:38 system.sav
drwx------ 1 ubuntu ubuntu       4096 2009-02-26 00:03 System Volume Information
-rw------- 2 ubuntu ubuntu      40659 2011-03-26 04:41 whitebedroom.jpg
drwx------ 1 ubuntu ubuntu     266240 2011-04-23 14:35 WINDOWS
-rw------- 1 ubuntu ubuntu         39 2011-04-23 14:33 XP_TV.ini
-rw------- 1 ubuntu ubuntu        158 2007-12-29 06:48 YServer.txt
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

---

### Post by rkillcrazy on 2011-05-11
> **Madmeeko said:**
> I really appreciate you trying to help.
 
```
drwx------ 1 ubuntu ubuntu 4096 2008-11-14 03:22 Documents and Settings
```



Well, this looks promising...  It looks like **Documents and Settings** directory is there!  The stuff up front are permissions.  From the looks of things, OWNER has **r**ead, **w**rite & e**x**ecute  The **d** tells you it's a directory.

Now, correct me if I'm wrong but I think I recall you saying Windows was FUBAR.  If that's the case, then I guess the thing to do here is try to recover the data we need and then start from scratch with another OS when the time comes.  Now, I don't know if the permissions are keeping you from getting into that folder.  If they are, we should be able to change that but for now, we'll hold off on that.  We can easily test this theory with another command.  Do another **ls** command and see if you can list things inside that directory.  

[COLOR="Red"]**Note**: Before you go typing all this out, know that you should use **tab-complete** to do this.  It saves time, keeps things spelled correctly, keeps things capitalized correctly and keeps one's blood pressure down in the process.  Tab-complete is used by typing parts of the words and then hitting the tab key to complete the rest of the word.  This works in Windows & in Linux.  So, when you get to **ls /media/WindowsXP/Docume**, hit that tab key and it will fill in the rest - including escape-characters to get you past those spaces.  If you hit it a couple times, it'll show you what's deeper down the tree.  You'll see what I mean...  ;) [/COLOR]

```
ls /media/WindowsXP/Docume
```

Anyway, see if you can list the contents of that directory and others (preferably your profile's directory) inside it.

---

### Post by Madmeeko on 2011-05-11
[QUOTE=rkillcrazy;10802010] 
Now, correct me if I'm wrong but I think I recall you saying Windows was FUBAR. If that's the case, then I guess the thing to do here is try to recover the data we need and then start from scratch with another OS when the time comes. Now, I don't know if the permissions are keeping you from getting into that folder. If they are, we should be able to change that but for now, we'll hold off on that. We can easily test this theory with another command. Do another **ls** command and see if you can list things inside that directory. 
 QUOTE]
 
Yep, Windows is FUBAR. Here is the ls command results
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ls /media/WindowsXP/Documents\ and\ Settings/
ls: reading directory /media/WindowsXP/Documents and Settings/: Input/output error
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

---

### Post by Fraoch on 2011-05-11
> **Madmeeko said:**
> [EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ls -l /media/WindowsXP
ls: cannot access /media/WindowsXP/sqmnoopt07.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt09.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt12.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt14.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata03.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata07.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata08.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata13.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata14.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata16.sqm: Input/output error

At first this looked suspicious but some Googling turned up:

[http://filext.com/file-extension/SQM](http://filext.com/file-extension/SQM)

(they're Windows Messenger/MSN logs)

Of course a virus may be disguising itself inside them, but there's no way to know that right now.

What's more concerning is all these I/O errors.  Is it possible your drive is damaged?

I haven't used a LiveCD in a while but it's supposed to be mostly like regular Ubuntu.  If that's the case, go to System - Control Centre - Disk Utility, find the Windows XP disk here and select "SMART Data".  Select "Run Self-test" and post the results.

---

### Post by rkillcrazy on 2011-05-11
> **Madmeeko said:**
> [QUOTE=rkillcrazy;10802010] 
Now, correct me if I'm wrong but I think I recall you saying Windows was FUBAR. If that's the case, then I guess the thing to do here is try to recover the data we need and then start from scratch with another OS when the time comes. Now, I don't know if the permissions are keeping you from getting into that folder. If they are, we should be able to change that but for now, we'll hold off on that. We can easily test this theory with another command. Do another **ls** command and see if you can list things inside that directory. 
 /QUOTE]
 
Yep, Windows is FUBAR. Here is the ls command results
 
```
ls /media/WindowsXP/Documents\ and\ Settings/
ls: reading directory /media/WindowsXP/Documents and Settings/: Input/output error

```

Ok, so it's not letting you got deeper than the root of the old C:\ drive...  I wouldn't think it's a permission thing, as I've never ran into that before.  However, since the system is FUBAR, I'm not overly worried about permissions at this point.  They'll get reset once you get them back onto a functioning system.  Again, I wouldn't think we'd have to do this but we've got little to lose at this point...  Try opening the permissions up to EVERYONE with FULL access.  Don't forget the tab-complete after **Documents**.

```
sudo chmod -R 777 /media/WindowsXP/Documents
```

When you do another **ls -l /media/WindowsXP**, it should change from:
```
drwx------ 1 ubuntu ubuntu 4096 2008-11-14 03:22 Documents and Settings
```

to 

```
drwxrwxrwx 1 ubuntu ubuntu 4096 2008-11-14 03:22 Documents and Settings
```

Basically, it's the equivalent of setting NTFS permissions to EVERYONE = FULL CONTROL.

---

### Post by rkillcrazy on 2011-05-11
> **Fraoch said:**
> At first this looked suspicious but some Googling turned up:

[http://filext.com/file-extension/SQM](http://filext.com/file-extension/SQM)

(they're Windows Messenger/MSN logs)

Of course a virus may be disguising itself inside them, but there's no way to know that right now.

What's more concerning is all these I/O errors.  Is it possible your drive is damaged?

I haven't used a LiveCD in a while but it's supposed to be mostly like regular Ubuntu.  If that's the case, go to System - Control Centre - Disk Utility, find the Windows XP disk here and select "SMART Data".  Select "Run Self-test" and post the results.

I too am beginning to wonder about a bad HDD.

---

### Post by Madmeeko on 2011-05-11
> **Fraoch said:**
> At first this looked suspicious but some Googling turned up:
 
[http://filext.com/file-extension/SQM](http://filext.com/file-extension/SQM)
 
(they're Windows Messenger/MSN logs)
 
Of course a virus may be disguising itself inside them, but there's no way to know that right now.
 
What's more concerning is all these I/O errors. Is it possible your drive is damaged?
 
I haven't used a LiveCD in a while but it's supposed to be mostly like regular Ubuntu. If that's the case, go to System - Control Centre - Disk Utility, find the Windows XP disk here and select "SMART Data". Select "Run Self-test" and post the results.
 
I was trying to find a way to copy the test results but couldn't find a way to do it.
 
The self test failed. Everything was Good except ...
 
Warning
 
ID 5
Reallocated Sector Count
Normalized: 98
Worst: 98
threshold: 36
value: 95 sectors
 
 
Warning
 
ID 197
Current Pending Sector Count
Normalized: 85
worst: 85
Threshold: 0
Value: 319 sectors
 
Hope that gives you the info needed.
 
 
> **rkillcrazy said:**
> [QUOTE=Madmeeko;10802080]
 
Ok, so it's not letting you got deeper than the root of the old C:\ drive... I wouldn't think it's a permission thing, as I've never ran into that before. However, since the system is FUBAR, I'm not overly worried about permissions at this point. They'll get reset once you get them back onto a functioning system. Again, I wouldn't think we'd have to do this but we've got little to lose at this point... Try opening the permissions up to EVERYONE with FULL access. Don't forget the tab-complete after **Documents**.
 
```
sudo chmod -R 777 /media/WindowsXP/Documents
```
 
When you do another **ls -l /media/WindowsXP**, it should change from:
```
drwx------ 1 ubuntu ubuntu 4096 2008-11-14 03:22 Documents and Settings
```
 
to 
 
```
drwxrwxrwx 1 ubuntu ubuntu 4096 2008-11-14 03:22 Documents and Settings
```
 
Basically, it's the equivalent of setting NTFS permissions to EVERYONE = FULL CONTROL.
 
It didn't change. I ran it twice to be sure I did it correct.
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo chmod -R 777 /media/WindowsXP/Documents\ and\ Settings/
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ls -l /media/WindowsXP/Documents\ and\ Settings/
ls: reading directory /media/WindowsXP/Documents and Settings/: Input/output error
total 0
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ls -l /media/WindowsXP
ls: cannot access /media/WindowsXP/sqmnoopt07.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt09.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt12.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmnoopt14.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata03.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata07.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata08.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata13.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata14.sqm: Input/output error
ls: cannot access /media/WindowsXP/sqmdata16.sqm: Input/output error
total 3317412
drwx------ 1 ubuntu ubuntu          0 2006-08-21 06:24 bby
-rw------- 1 ubuntu ubuntu        211 2006-08-20 10:24 boot.ini
drwx------ 1 ubuntu ubuntu     552960 2011-04-21 15:02 Config.Msi
drwx------ 1 ubuntu ubuntu       4096 2008-11-14 03:22 Documents and Settings
drwx------ 1 ubuntu ubuntu      16384 2009-08-06 06:39 ec0f529251c91392942cf2ca2e
drwx------ 1 ubuntu ubuntu          0 2006-11-22 02:31 f05ca23eeeb1bd2e8b
-rw------- 1 ubuntu ubuntu 1063374848 2011-04-23 14:30 hiberfil.sys
drwx------ 1 ubuntu ubuntu          0 2006-08-20 10:26 hp
-rw------- 1 ubuntu ubuntu       1402 2011-04-24 14:45 hpqp.ini
drwx------ 1 ubuntu ubuntu    1196032 2006-08-20 05:12 I386
-rw------- 1 ubuntu ubuntu          0 2010-07-01 21:18 IO.SYS
-rw------- 1 ubuntu ubuntu          0 2010-07-01 21:18 MSDOS.SYS
-rw------- 1 ubuntu ubuntu      47564 2004-08-04 21:00 ntdetect.com
-rw------- 1 ubuntu ubuntu     250048 2008-11-01 19:09 ntldr
-rw------- 1 ubuntu ubuntu 1598029824 2011-04-23 14:30 pagefile.sys
drwx------ 1 ubuntu ubuntu      28672 2011-05-10 17:22 Program Files
drwx------ 1 ubuntu ubuntu          0 2009-08-04 13:53 RECYCLER
-rw------- 2 ubuntu ubuntu  733168699 2010-08-28 02:35 Salt (2010).mp4
-rw------- 2 ubuntu ubuntu        268 2010-08-17 06:16 sqmdata00.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-18 07:00 sqmdata01.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-19 07:34 sqmdata02.sqm
-????????? ? ?      ?               ?                ? sqmdata03.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-21 07:22 sqmdata04.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-22 07:37 sqmdata05.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-23 05:41 sqmdata06.sqm
-????????? ? ?      ?               ?                ? sqmdata07.sqm
-????????? ? ?      ?               ?                ? sqmdata08.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-26 07:56 sqmdata09.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-27 07:09 sqmdata10.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-28 08:19 sqmdata11.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-29 08:26 sqmdata12.sqm
-????????? ? ?      ?               ?                ? sqmdata13.sqm
-????????? ? ?      ?               ?                ? sqmdata14.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-12 12:29 sqmdata15.sqm
-????????? ? ?      ?               ?                ? sqmdata16.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-16 06:55 sqmdata17.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-13 07:30 sqmdata18.sqm
-rw------- 2 ubuntu ubuntu        268 2010-08-14 06:11 sqmdata19.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-20 07:24 sqmnoopt00.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-21 07:22 sqmnoopt01.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-22 07:37 sqmnoopt02.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-23 05:41 sqmnoopt03.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-24 07:50 sqmnoopt04.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-25 08:00 sqmnoopt05.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-26 07:56 sqmnoopt06.sqm
-????????? ? ?      ?               ?                ? sqmnoopt07.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-28 08:19 sqmnoopt08.sqm
-????????? ? ?      ?               ?                ? sqmnoopt09.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-30 08:05 sqmnoopt10.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-11 07:35 sqmnoopt11.sqm
-????????? ? ?      ?               ?                ? sqmnoopt12.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-13 07:30 sqmnoopt13.sqm
-????????? ? ?      ?               ?                ? sqmnoopt14.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-15 06:43 sqmnoopt15.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-18 07:00 sqmnoopt16.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-19 07:34 sqmnoopt17.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-16 06:55 sqmnoopt18.sqm
-rw------- 2 ubuntu ubuntu        244 2010-08-17 06:16 sqmnoopt19.sqm
drwx------ 1 ubuntu ubuntu       8192 2006-08-20 10:38 SwSetup
drwx------ 1 ubuntu ubuntu       4096 2006-08-20 10:38 system.sav
drwx------ 1 ubuntu ubuntu       4096 2009-02-26 00:03 System Volume Information
-rw------- 2 ubuntu ubuntu      40659 2011-03-26 04:41 whitebedroom.jpg
drwx------ 1 ubuntu ubuntu     266240 2011-04-23 14:35 WINDOWS
-rw------- 1 ubuntu ubuntu         39 2011-04-23 14:33 XP_TV.ini
-rw------- 1 ubuntu ubuntu        158 2007-12-29 06:48 YServer.txt
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] 

 
 
Thanks guys :)

---

### Post by Madmeeko on 2011-05-11
I just went into my BIOS setup utility and ran that hard drive self test.
 
Test Status #1- 07 Fail

---

### Post by Fraoch on 2011-05-11
> **Madmeeko said:**
> I was trying to find a way to copy the test results but couldn't find a way to do it.
 
The self test failed. Everything was Good except ...
 
Warning
 
ID 5
Reallocated Sector Count
Normalized: 98
Worst: 98
threshold: 36
value: 95 sectors
 
 
Warning
 
ID 197
Current Pending Sector Count
Normalized: 85
worst: 85
Threshold: 0
Value: 319 sectors
 
Hope that gives you the info needed.

Yes it does and it looks like bad news.  Your hard drive has failed.  You have portions of it that appear to be physically damaged.  Unfortunately the data is probably gone for good.:(

Go get yourself two new hard drives - one conventional one and one external one at least the same size designed for backups.  Use the external one with Ubuntu to copy over any data you want to keep.  Then swap out the conventional one for the damaged one inside your computer and reinstall your OS.  Obviously I'd advise to go with Ubuntu this time...not that it would have prevented this, but because you already have it and you won't have to pay someone for it.

Oh and whatever OS you end up going with, use the external drive to back up your data.

---

### Post by rkillcrazy on 2011-05-11
> **Fraoch said:**
> Yes it does and it looks like bad news.  Your hard drive has failed.  You have portions of it that appear to be physically damaged.  Unfortunately the data is probably gone for good.:(


I was afraid of this.  Unfortunately, I doubt there's much to keep.  If you can't get into the old %HomePath% directory, there's very little left to save - unless you're one to keep things stored outside your profile.

---

### Post by Fraoch on 2011-05-11
> **rkillcrazy said:**
> I was afraid of this.  Unfortunately, I doubt there's much to keep.  If you can't get into the old %HomePath% directory, there's very little left to save - unless you're one to keep things stored outside your profile.

Yes, because Madmeeko's Documents and Settings directory is gone, there's not really much personal data left...

Still, Madmeeko, do get those two drives including the external one.  Just skip copying anything over if there's nothing left to save, but do use it to make regular backups.  Another nice add-on which shouldn't be too expensive is a small fireproof safe (mine only cost about $20).  Store the drive here.

Another advantage of Ubuntu is Ubuntu One online backup.  It's only 2 GB (free) but it syncs automatically in the background, continually.  It's been around for a while now and has gotten mature and stable.

---

### Post by ClientAlive on 2011-05-11
> **Fraoch said:**
> Yes, because Madmeeko's Documents and Settings directory is gone, there's not really much personal data left...

Still, Madmeeko, do get those two drives including the external one.  Just skip copying anything over if there's nothing left to save, but do use it to make regular backups.  Another nice add-on which shouldn't be too expensive is a small fireproof safe (mine only cost about $20).  Store the drive here.

Another advantage of Ubuntu is Ubuntu One online backup.  It's only 2 GB (free) but it syncs automatically in the background, continually.  It's been around for a while now and has gotten mature and stable.


Not sure if this may be of use or not but I have heard that some people use knoppix to access and work on a system. Also, clonezilla is supposed to be great for making a clone of your o/s in case something were to happen to it. It works for windows also/ can make a clone of windows. Here are a few links in case you are interested:

_For Knoppix_:

[http://www.bayviewinternet.com/index.php?pageID=66](http://www.bayviewinternet.com/index.php?pageID=66)

[http://www.knoppix.net/wiki/Using_FAQ](http://www.knoppix.net/wiki/Using_FAQ)

[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

_For Clonezilla_:

[http://searchvirtualdesktop.techtarget.com/definition/Clonezilla](http://searchvirtualdesktop.techtarget.com/definition/Clonezilla)

[http://clonezilla.org/](http://clonezilla.org/)

[http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

HTH

---

### Post by ClientAlive on 2011-05-13
From reading the thread I know it may be a little late for this but a friend had sent me a link a little while back and I just got around to looking at it. Perhaps this would be useful for someone in the future.

[http://www.asrdata2.com/](http://www.asrdata2.com/)

I just came across this so I don't know. But based on some of the things it say this thing can do . . .

---


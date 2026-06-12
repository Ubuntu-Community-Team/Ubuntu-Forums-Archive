---
title: "Cannot open /usr/bin"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by beew on 2010-06-06
Hi, I am an absolute beginer to Linux. I have freshly installed Ubuntu 10.04 on my laptop and have had a fun time playing around. Everything seems to work great except I discovered yesterday that I couldn't open the /usr/bin folder via Nautilus. When I tried to open it with a click the little circle dot started rotating and then stopped. I tried to open other folders with the same right clicking method with no problem. However, I can view the content of /usr/bin by creating a new launcher and then use  the find function (without actually creating a new launcher, I just do that to bring up the search menu)

Another thing that may be related is that I can no longer install programs by right clicking the .bin file (the installer). However,  I can still activate the installer and complete the installation with command lines. Since I was able to do this before and the problem of opening /ur/bin seemed to occur at the same time, I think they may be related. 

I would like to post part of the apport report for the crash here, but I don't know how.
It seems that the following may be crucial : "XsessionErrors...libgdu-WARNING: Couldn't call GetAll() to get properties for /org/freedesktop/UDisk/devices/sdb1..." 

Finally, I am not sure if this is relevant, my computer is configured to dual boot with windows xp. dev/sda1 is the windows partition. The crash report mentions sdb1, can  it be related?

Thanks in advance for any help.

EDITED: I don't think it has anything to do with permission because I can open all the folders (except those marked with a cross) without special permission and I have tried "gksudo nautilus" (I know it is not advisable) but still no luck in opening /usr/bin

---

### Post by oldos2er on 2010-06-06
Have you tried running **fsck** on your root partition? **sudo touch /forcefsck** run in a terminal will cause fsck to run on next boot (you don't want to run it on a mounted partition). 

/usr/bin is a large directory, and it takes several seconds to open in Nautilus. If you run **nautilus /usr/bin** in a terminal, is there any output?

---

### Post by beew on 2010-06-06
Hi, oldoser,

Thanks for the hint. 

You see, I am a total beginer so I have no clue what fsck is and what it does. I will  look it up and try your method. But if it is not too much trouble it would be nice if you can give me some hint of what it does.

I did do nautilus /usr/bin in the terminal. The same result. Folder view popped up for a bit, little circle rotated and then  it just died.

---

### Post by sandyd on 2010-06-06
> **beew said:**
> Hi, oldoser,

Thanks for the hint. 

You see, I am a total beginer so I have no clue what fsck is and what it does. I will  look it up and try your method. But if it is not too much trouble it would be nice if you can give me some hint of what it does.
**fsck checks your filesystems for errors.**

I did do nautilus /usr/bin in the terminal. The same result. Folder view popped up for a bit, little circle rotated and then  it just died..Ive also compiled a guide on how to use FSCK and other Hard Disk tools, you can see it here -> [http://dolphinaura.com/tutorials/hard-disk-tools-in-linux](http://dolphinaura.com/tutorials/hard-disk-tools-in-linux)

---

### Post by oldos2er on 2010-06-06
fsck = file system check; it's similar to chkdsk in DOS/Win.

---

### Post by beew on 2010-06-06
Hi,

Thanks for the explanation. :)

I have tried oldos2er's suggestion to run a fsck. Nothing unusual happened and I got logged  back in automatically. But Nautilus still crashes whenever I try to open /usr/bin with a right click. :(

---

### Post by beew on 2010-06-07
Hello??! Anyone??

---

### Post by oldos2er on 2010-06-07
When you ran "nautilus /usr/bin" in a terminal, was there any output from that command? I understand Nautilus did nothing, but I'd like to know if there was any text output in the terminal.

---

### Post by Mariane on 2010-06-07
I don't see how sdb1 could be related, as far as I know that is an outside usb port. 

sda-somethings are hard disks and sdb-somethings are usb ports. Please correct me if this is not always the case. 

Mariane

---

### Post by oldos2er on 2010-06-07
It's been my experience that internal hard drives are "lettered" ahead of USB devices.

---

### Post by beew on 2010-06-07
Hi, Ann,

Thanks for getting back. After running nautilus /usr/bin the text output on the terminal said 
"initializing nautilus-gdu extension
segmentation fault"

I should have reported that earlier.

Mariane,

Indeed my laptop is plugged into a usb wireless card because the internal one has died. But after removing it and restart nautilus still crashes whenever I attempt to open /usr/bin.

---

### Post by Shhnap on 2010-06-08
There is a better step, we need to know if you have a /usr/bin.

Open a terminal:
```
id
ls -l /usr/
ls -la /usr/bin | head -n30
```

And give us the output of those commands. Thanks. It will prove if you actually have files there and they are readable for you.

---

### Post by beew on 2010-06-08
Hi Shhnap,

Thanks for the suggestion. Here is the output, it is a bit long:

bee@bee-laptop:~$ id
uid=1000(bee) gid=1000(bee) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(fuse),105(lpadmin),112(netdev),119(admin),121(nopasswdlogin),122(sambashare),1000(bee)
bee@bee-laptop:~$ ls -l /usr/
total 224
drwxr-xr-x   2 root root 69632 2010-06-07 23:48 bin
drwxr-xr-x   2 root root  4096 2010-06-07 03:34 games
drwxr-xr-x  49 root root 16384 2010-06-07 23:48 include
drwxr-xr-x 273 root root 94208 2010-06-07 23:48 lib
drwxr-xr-x   3 root root  4096 2010-05-24 19:11 lib64
drwxr-xr-x  10 root root  4096 2010-04-29 08:17 local
drwxr-xr-x   2 root root 12288 2010-06-06 22:53 sbin
drwxr-xr-x 384 root root 12288 2010-06-07 12:22 share
drwxrwsr-x   5 root src   4096 2010-06-01 22:09 src
bee@bee-laptop:~$ ls -la /usr/bin | head -n30
total 242036
drwxr-xr-x  2 root   root       69632 2010-06-07 23:48 .
drwxr-xr-x 11 root   root        4096 2010-05-24 19:11 ..
-rwxr-xr-x  1 root   root       42584 2010-03-04 22:29 [
lrwxrwxrwx  1 root   root           8 2010-05-23 01:55 2to3 -> 2to3-2.6
-rwxr-xr-x  1 root   root         106 2010-04-16 09:59 2to3-2.6
-rwxr-xr-x  1 root   root        9624 2010-04-17 04:20 411toppm
-rwxr-xr-x  1 root   root          39 2009-07-08 19:57 7z
-rwxr-xr-x  1 root   root          40 2009-07-08 19:57 7za
-rwxr-xr-x  1 root   root      105068 2010-04-23 04:23 a2p
lrwxrwxrwx  1 root   root           7 2010-05-29 18:47 abrowser -> firefox
-rwxr-xr-x  1 root   root     1551372 2010-02-16 12:44 acetoneiso
lrwxrwxrwx  1 root   root          25 2010-06-06 15:00 aclocal -> /etc/alternatives/aclocal
-rwxr-xr-x  1 root   root       31181 2010-02-01 19:59 aclocal-1.11
-rwxr-xr-x  1 root   root       13896 2010-03-28 19:02 aconnect
-rwxr-xr-x  1 root   root       18508 2009-06-12 13:16 acpi
-rwxr-xr-x  1 root   root        5528 2010-04-23 08:51 acpi_fakekey
-rwxr-xr-x  1 root   root        9864 2010-04-29 01:32 acpi_listen
-rwxr-xr-x  1 root   root        1221 2010-04-15 01:02 add-apt-repository
-rwxr-xr-x  1 root   root       26220 2010-02-22 05:21 addftinfo
-rwxr-xr-x  1 root   root        5500 2010-03-22 13:51 addpart
-rwxr-xr-x  1 root   root       22324 2010-04-18 22:00 addr2line
-rwxr-xr-x  1 root   root       26356 2010-05-03 12:57 afm2pl
-rwxr-xr-x  1 root   root       31624 2010-05-03 12:57 afm2tfm
-rwxr-xr-x  1 root   root      165806 2010-02-22 05:21 afmtodit
-rwxr-xr-x  1 root   root       13948 2010-03-30 16:42 akonadi2xml
-rwxr-xr-x  1 root   root       76396 2010-03-30 16:42 akonadi_birthdays_resource
-rwxr-xr-x  1 root   root       88708 2010-03-30 16:42 akonadi_contacts_resource
-rwxr-xr-x  1 root   root      268768 2010-04-13 14:00 akonadi_control
-rwxr-xr-x  1 root   root       71848 2010-04-13 14:00 akonadictl
bee@bee-laptop:~$ 

I am very sure that I have a /usr/bin/. I can actually see its content by right clicking on the screen, then do create launcher > browse.

---

### Post by philinux on 2010-06-08
> **beew said:**
> Hi, Ann,

Thanks for getting back. After running nautilus /usr/bin the text output on the terminal said 
"[B]initializing nautilus-gdu extension
segmentation fault"[/B]

Someone else got a similar error.
[http://ubuntuforums.org/showthread.php?t=1384038](http://ubuntuforums.org/showthread.php?t=1384038)

---

### Post by beew on 2010-06-08
Hi, philinux,

I checked out your link and removed the folder /.local/share/gvfs-metadata and then restarted the computer as they suggested. Still doesn't work. :(

---

### Post by oldos2er on 2010-06-08
Seg faults are beyond my ability to help (not a programmer). You might want to search launchpad.net to see if a similar bug has been filed; if not, you might want to file one yourself.

---

### Post by beew on 2010-06-09
Hi, 

Thanks for trying anyway. I have filed a bug report and I will get back to you if it doesn't sink into some black hole. In  the mean time, I will appreaciate it if any one can offer a solution.

---

### Post by beew on 2010-07-25
Hi,

I have an update. I have just wiped out my hard drive and made a clean reinstallation of Ubuntu but /usr/bin still doesn't open :confused:

I have also installed Ubuntu on a 40 G external hard disk, same problem. 

Now I have a third installation of Ubuntu on a 8G usb thumb drive (a full installation, not a live usb with persistence) and /usr/bin would open!

They all have similar softwares that I installed from the repo but a major difference, apart from the size is that both my laptop and 40 G hard disk installations have a separate /home partition while the thumb drive installation doesn't.

Is it possible that having a separate /home partition somehow prevents /usr/bin from opening?

---

### Post by Nabo00o on 2010-12-01
Hey beew I have more or less the exact same problem. 
I got a clean install of Ubuntu 10.04 and had experienced the problem earlier but forgot it.
Now when I just wanted to localize a program I got in the application menu, meaning going into folder usr, and then bin, it jumps out of nautilus, and it seems like gnome is actually restarting or something, since the bars at the bottom and top disappear and reappear again...

I can view some of the content by typing ls /usr/bin (so yes it is there), but as previously said nautilus can't handle it.

Hey, is this fixed in Marverick by any chance? I haven't upgraded yet...

Julian

---

### Post by karthikprasad on 2011-06-29
hello,
i too am facing the same issue...has the problem been solved?
thanks
kp

---

### Post by beew on 2011-06-29
Doesn't  look like it is solved, just tried this in Natty, same thing.

---

### Post by dFlyer on 2011-06-29
Just tried it and it works here with Unity.

---

### Post by beew on 2011-06-29
> **dFlyer said:**
> Just tried it and it works here with Unity.

I use Unity as well.

---

### Post by CVGH on 2011-06-29
Works fine here in 10.10

---

### Post by beew on 2011-06-29
So do you guys have a separate /home partition? I have tested a few installs (all Natty with Unity except one Maverick) it seems that  /usr/bin opens fine if there is no separate /home but crashes if it is present.

---

### Post by jtarin on 2011-06-29
Is the partition /home being mounted at boot with correct permissions?

---

### Post by beew on 2011-06-30
> **jtarin said:**
> Is the partition /home being mounted at boot with correct permissions?

How do I find out?

---

### Post by jtarin on 2011-06-30
> **beew said:**
> How do I find out?In the terminal issue the command```
 cat /etc/fstab
``` and post the results.

---

### Post by beew on 2011-06-30
Hi, here are the outputs
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=af9073f4-f16c-4285-8acc-01373932dbcc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7e5b410b-27e1-43c6-98c7-2df2cbe8dbd5 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8 none            swap    sw              0       0





---

### Post by CVGH on 2011-06-30
/home is on same partition as root.

```
brian@pioneerdrives:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b72eec44-de3c-4ccb-885d-0a5c799f4773 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=764d6ad3-868d-4df0-ad83-933a901dee9b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
brian@pioneerdrives:~$ 
```

---

### Post by beew on 2011-06-30
> **CVGH said:**
> /home is on same partition as root.




Not possible. /home is in sda5, / is in sda2.  If they were the same it would be like not having a separate /home partition, right? If that is the case /usr/bin would open just like in the other install where a separate /home is absent.

---

### Post by CVGH on 2011-07-01
Sorry, was talking about my two pc's and their layout.....

---

### Post by ravipfiles on 2011-11-02
> **oldos2er said:**
> When you ran "nautilus /usr/bin" in a terminal, was there any output from that command? I understand Nautilus did nothing, but I'd like to know if there was any text output in the terminal.


hii friends,
I also have same problem. when I type "nautilus /usr/bin/", from my user account, neither anything displayed on terminal nor browser windows comes (it comes and disappeard within 2-3 seconds). However if I run the same command from root, I got the following on terminal
Initializing nautilus-gdu extension

(nautilus:3442): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

browser windows is still not coming :(...please check if above error msg can help u.

---


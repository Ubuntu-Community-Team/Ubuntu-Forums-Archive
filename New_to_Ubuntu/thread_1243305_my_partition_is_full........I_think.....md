---
title: "my partition is full........I think...."
date: 2009-08-18
forum: New to Ubuntu
---

### Post by GMachine_24 on 2009-08-18
Hi:

I am running Jaunty and have it on a dual-boot with Windows XP. When I try to d/l and install updates, I get an error message that my drive is full. Which it is - I just can't figure out why.

Here is the information from Gparted:

/dev/sda1 is ntfs (windows) with 49.38 GB

/dev/sda2 is an extended partition of 6.51GB but...none is used.

/dev/sda3 is ext3 partition 6.18GB of which 6.04GB is used (problem)

/dev/sda5 is the swap file @ 337MB

I have never had an Ubuntu install that took up more than 2GB even with all added programs and files. How do I figure out what is hogging all that space?

TIA.

GM

---

### Post by t0p on 2009-08-18
The command ```
df -h
``` typed into the terminal may reveal more about the disk usage. Also, under Applications > Accessories you will find an app called Disk Usage Analyzer (i think) which will give you pretty diagrams of what is on your disk. Alternatively, you could open a terminal, navigate to the partition in question and type in the command ```
ls -la
``` That command will print to the terminal a list of the partition's contents, along with the sizes of the files etc. Post here the output of these commands and we will see what we can see.

---

### Post by wojox on 2009-08-18
It's recommended 8 GB of disk space for minimum requirements. 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by philinux on 2009-08-18
My root partition is 12g but only using 4.5g and has never been above 6g.

Check out this.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by credobyte on 2009-08-18
Cleaning Aptitude cache might free up *some* space:
```
sudo apt-get clean
```

---

### Post by Bartender on 2009-08-18
> **GMachine_24 said:**
> /dev/sda2 is an extended partition of 6.51GB but...none is used.

To me, the best way to picture an extended partition is to think of it as a "box" that holds logical partitions.  I'm not sure what you mean by "none is used" but I'm guessing that you have logical partitions inside the extended and there's probably no wasted space.

---

### Post by Penguin Guy on 2009-08-18
Please run [COLOR="Green"]sudo fdisk -l[/COLOR] and post back the results. I don't think you know what's going on with your hard drive (neither did I when I was new to Linux), this is how things are (from what you gave me):

/dev/sda1 NTFS [ 49.38 GB ] (Windows)

/dev/sda2 Extended [ 0 Bytes / 6.51GB ]
--/dev/sda5 Swap [ 0 Bytes / ? ] [COLOR="Green"]<- sda5 is *inside* sda2[/COLOR]

/dev/sda3 ext3 [ 6.04GB / 6.18GB ] (Linux) [COLOR="Green"]<- sda3 is *outside* sda2[/COLOR]

Overall this means your hard drive should be 62GB which, not being a power of 2, is an unusual size.

---

### Post by GMachine_24 on 2009-08-18
> **t0p said:**
> The command ```
df -h
``` typed into the terminal may reveal more about the disk usage. Also, under Applications > Accessories you will find an app called Disk Usage Analyzer (i think) which will give you pretty diagrams of what is on your disk. Alternatively, you could open a terminal, navigate to the partition in question and type in the command ```
ls -la
``` That command will print to the terminal a list of the partition's contents, along with the sizes of the files etc. Post here the output of these commands and we will see what we can see.

Hi: First, thanks for the prompt replies to everyone. I do some things about Ubuntu OK but this is not one of them.

```


gmachine@gmachine-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.1G  5.9G     0 100% /
tmpfs                 628M     0  628M   0% /lib/init/rw
varrun                628M  324K  628M   1% /var/run
varlock               628M     0  628M   0% /var/lock
udev                  628M  152K  628M   1% /dev
tmpfs                 628M   84K  628M   1% /dev/shm
lrm                   628M  2.2M  626M   1% /lib/modules/2.6.28-14-generic/volatile
overflow              1.0M  680K  344K  67% /tmp
gmachine@gmachine-laptop:~$ 


```

and....

```


gmachine@gmachine-laptop:~$ ls -la
total 7736
drwxr-xr-x 60 gmachine gmachine    4096 2009-08-18 15:35 .
drwxr-xr-x  3 root     root        4096 2009-05-08 18:42 ..
drwx------  2 gmachine gmachine    4096 2009-07-05 15:17 .AbiSuite
drwx------  4 gmachine gmachine    4096 2009-05-09 00:30 .adobe
drwx------  4 gmachine gmachine    4096 2009-07-16 18:49 .aqbanking
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-10 17:22 .audacity1.3-gmachine
drwxr-xr-x  5 gmachine gmachine    4096 2009-05-10 17:22 .audacity-data
-rw-------  1 gmachine gmachine       0 2009-08-18 15:28 .bash_history
-rw-r--r--  1 gmachine gmachine     220 2009-05-08 18:42 .bash_logout
-rw-r--r--  1 gmachine gmachine    3115 2009-05-08 18:42 .bashrc
-rw-r--r--  1 gmachine gmachine   87953 2009-07-14 15:18 Bruno.pdf
drwxr-xr-x 11 gmachine gmachine    4096 2009-07-02 21:21 .cache
drwxr-xr-x  2 gmachine gmachine    4096 2009-08-02 09:36 .clive
drwx------  3 gmachine gmachine    4096 2009-05-08 19:49 .compiz
-rwxr-xr-x  1 gmachine gmachine   28360 2009-05-22 13:46 compiz-check
drwxr-xr-x 19 gmachine gmachine    4096 2009-07-22 23:24 .config
drwx------  2 gmachine gmachine    4096 2009-06-17 14:58 .cups
drwx------  3 gmachine gmachine    4096 2009-05-08 18:47 .dbus
drwxr-xr-x  4 gmachine gmachine    4096 2009-08-13 18:02 Desktop
-rw-------  1 gmachine gmachine      25 2009-08-03 23:41 .dmrc
drwxr-xr-x  2 gmachine gmachine    4096 2009-07-30 10:32 Documents
-rw-r--r--  1 gmachine gmachine   31082 2009-05-09 11:36 dreamtime.odt
drwxr-xr-x  3 gmachine gmachine    4096 2009-05-08 19:32 .dvdcss
-rw-------  1 gmachine gmachine   11744 2009-07-16 18:49 eriksm.kmy
-rw-------  1 gmachine gmachine      16 2009-05-08 18:47 .esd_auth
drwxr-xr-x  8 gmachine gmachine    4096 2009-06-23 23:27 .evolution
-rw-r--r--  1 gmachine gmachine     357 2009-05-08 18:42 examples.desktop
drwxr-xr-x  2 gmachine gmachine    4096 2009-06-23 22:39 .fontconfig
drwx------  5 gmachine gmachine    4096 2009-08-18 15:32 .gconf
drwx------  2 gmachine gmachine    4096 2009-08-04 00:11 .gconfd
drwx------  4 gmachine gmachine    4096 2009-05-22 14:40 .gegl-0.0
drwxr-xr-x 22 gmachine gmachine    4096 2009-05-22 14:42 .gimp-2.6
-rw-r-----  1 gmachine gmachine       0 2009-08-18 15:33 .gksu.lock
-rw-------  1 gmachine gmachine    6477 2009-07-05 14:10 gmachine1.kmy
-rw-------  1 gmachine gmachine    6908 2009-07-05 14:06 gmachine.kmy
drwx------  3 gmachine gmachine    4096 2009-05-15 20:19 .gnome
drwx------ 13 gmachine gmachine    4096 2009-08-02 10:18 .gnome2
drwx------  2 gmachine gmachine    4096 2009-05-08 18:47 .gnome2_private
drwx------  2 gmachine gmachine    4096 2009-05-08 18:47 .gnupg
lrwxrwxrwx  1 gmachine gmachine      40 2009-05-15 20:18 googleearth -> /home/gmachine/google-earth//googleearth
drwx------  4 gmachine gmachine    4096 2009-05-19 11:43 .googleearth
drwxr-xr-x 10 gmachine gmachine    4096 2009-05-15 20:19 google-earth
drwxr-xr-x  2 gmachine gmachine    4096 2009-08-02 09:24 .gstreamer-0.10
-rw-r--r--  1 gmachine gmachine       0 2009-08-18 15:35 .gtk-bookmarks
dr-x------  2 gmachine gmachine       0 2009-08-18 15:32 .gvfs
drwxr-----  2 gmachine gmachine    4096 2009-06-17 15:05 .hplip
-rw-------  1 gmachine gmachine       0 2009-08-18 15:32 .ICEauthority
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 20:48 .icons
drwxr-xr-x  3 gmachine gmachine    4096 2009-05-08 19:24 .java
drwx------  3 gmachine gmachine    4096 2009-05-08 19:03 .kde
drwxr-xr-x  4 gmachine gmachine    4096 2009-07-07 00:45 .listen
drwx------  3 gmachine gmachine    4096 2009-05-08 19:04 .local
drwx------  3 gmachine gmachine    4096 2009-05-15 20:18 .loki
drwxr-xr-x  3 gmachine gmachine    4096 2009-06-11 01:23 .lyrics
drwx------  3 gmachine gmachine    4096 2009-05-08 19:41 .macromedia
drwxr-xr-x  3 gmachine gmachine    4096 2009-06-23 23:28 .mission-control
drwx------  8 gmachine gmachine    4096 2009-07-03 20:13 .mozilla
drwxr-xr-x  7 gmachine gmachine    4096 2009-05-20 19:13 Music
drwxr-xr-x  3 gmachine gmachine    4096 2009-05-08 18:47 .nautilus
-rw-r--r--  1 gmachine gmachine     967 2009-05-22 13:58 .nvidia-settings-rc
drwxr-xr-x  3 gmachine gmachine    4096 2009-05-09 10:30 .openoffice.org
-rw-r--r--  1 gmachine gmachine  696179 2009-06-17 15:12 .pdf
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 18:47 Pictures
-rw-r--r--  1 gmachine gmachine      37 2009-06-17 15:04 .printer-groups.xml
-rw-r--r--  1 gmachine gmachine     675 2009-05-08 18:42 .profile
-rw-r--r--  1 gmachine gmachine 1558727 2009-06-17 15:12 .ps
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 18:47 Public
drwx------  2 gmachine gmachine    4096 2009-08-18 15:32 .pulse
-rw-------  1 gmachine gmachine     256 2009-05-08 18:47 .pulse-cookie
drwx------  6 gmachine gmachine    4096 2009-07-27 02:46 .purple
drwxr-xr-x  2 gmachine gmachine    4096 2009-06-29 22:30 .qt
-rw-------  1 gmachine gmachine    7898 2009-08-02 10:18 .recently-used.xbel
-rw-r--r--  1 gmachine gmachine 5166354 2009-05-17 00:53 R.E.M. - The Great Beyond.mp3
drwx------  3 gmachine gmachine    4096 2009-08-13 17:48 .Skype
drwx------  4 gmachine gmachine    4096 2009-05-16 21:30 .songbird2
-rw-r--r--  1 gmachine gmachine       0 2009-05-08 18:48 .sudo_as_admin_successful
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 18:47 Templates
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 20:48 .themes
drwx------  4 gmachine gmachine    4096 2009-06-17 23:30 .thumbnails
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 18:48 .update-manager-core
drwx------  2 gmachine gmachine    4096 2009-07-04 22:11 .update-notifier
-rw-r--r--  1 root     root         147 2009-06-20 13:50 update-rc.d: warning etc. missing LSB information
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 18:47 Videos
drwxr-xr-x  2 gmachine gmachine    4096 2009-08-02 09:18 .wapi
-rw-------  1 gmachine gmachine       0 2009-08-18 15:32 .Xauthority
drwx------  4 gmachine gmachine    4096 2009-08-18 07:20 .xchat2
drwxr-xr-x  2 gmachine gmachine    4096 2009-05-08 19:03 .xine
-rw-r--r--  1 gmachine gmachine       0 2009-08-18 15:38 .xsession-errors
gmachine@gmachine-laptop:~$ 


I can see the drive is full - I just don't know what it's full of.

Thanks.

GM


```

---

### Post by GMachine_24 on 2009-08-18
I clean the aptitude cache after every update/upgrade.

---

### Post by GMachine_24 on 2009-08-18
Here is other information you asked for. I am beginning to believe I just didn't give the initial partition enough space.

```


gmachine@gmachine-laptop:~$ sudo fdisk -l
[sudo] password for gmachine: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa41ea41e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6446    51777463+   7  HPFS/NTFS
/dev/sda2            6447        7296     6827625    5  Extended
/dev/sda5            6447        7253     6482196   83  Linux
/dev/sda6            7254        7296      345366   82  Linux swap / Solaris
gmachine@gmachine-laptop:~$ 


```

---

### Post by GMachine_24 on 2009-09-11
Sorry to take so long to post this - my Linux partitions were full. I finally just installed or reinstalled v. 9.0.4 or whatever it is. Gave the partitions more room; everything is fine.

Although I do wonder because it seems the installs are getting bigger by a factor of several GBs and ... I wonder why.

Anyway, thanks to all those who posted.

Namaste.

GM

---


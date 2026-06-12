---
title: "Help with Installing drivers for wireless"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Tholley on 2009-12-27
I am trying to download and install a Bzip archive (.tar.bz2) which should contain linux drivers for my linksys wireless adapter, from Ralink software which was the choice from the ndiswrapper list.

The default shows to be "Open with Archive Manager (default)", but after downloading I get an error stating 
"/tmp/2009_0123_RT61_Linux_STA_v1.1.2.3.tar-1.bz2 could not be opened, because the associated helper application does not exist. Change the association in your preferences."

I downloaded again and saved the file, extracted it I think, but not seeing the .sys or .inf files that the ndiswrapper instructions say to look for.

I must be doing something wrong?

---

### Post by taurus on 2009-12-27
Where did you extract it to?  It probably created a new directory (or folder to some people) where all the files should be in.

---

### Post by Tholley on 2009-12-27
I think I extracted it to the same "downloads" folder the zip file is in.

It created a folder next to the .tar.bz2 box, with the same title excluding the .tar.bz2.

---

### Post by taurus on 2009-12-27
You mean you extracted it in /tmp?  Do you see a new directory with the same name as the file but without the .tar.bz2?  Look in that directory.

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la /tmp
```

---

### Post by Tholley on 2009-12-27
yeah, there is a new directory (folder) with the same name, but after searching through the files, no sign of any .sys or .ini files.

here is the output...

total 1756
drwxrwxrwt 12 root   root     4096 2009-12-27 12:00 .
drwxr-xr-x 21 root   root     4096 2009-12-27 08:36 ..
-r--------  1 kaylen kaylen 871253 2009-12-27 11:41 2009_0123_RT61_Linux_STA_v1.1.2.3.tar-1.bz2
-r--------  1 kaylen kaylen 871253 2009-12-27 11:37 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2
drwx------  2 kaylen kaylen   4096 2009-12-27 11:10 .esd-1000
drwxrwxrwt  2 root   root     4096 2009-12-27 11:10 .ICE-unix
drwx------  2 kaylen kaylen   4096 2009-12-27 11:10 keyring-CfZy3u
drwx------  2 kaylen kaylen   4096 2009-12-27 12:15 orbit-kaylen
drwx------  2 root   root     4096 2009-12-27 12:00 orbit-root
drwx------  2 kaylen kaylen   4096 2009-12-27 11:10 pulse-LXHuIUtYi4rE
drwx------  2 kaylen kaylen   4096 2009-12-27 11:10 seahorse-AmIlfq
drwx------  2 kaylen kaylen   4096 2009-12-27 11:10 ssh-XWftVv2898
drwx------  2 kaylen kaylen   4096 2009-12-27 11:10 virtual-kaylen.zExFpg
-r--r--r--  1 root   root       11 2009-12-27 11:10 .X0-lock
drwxrwxrwt  2 root   root     4096 2009-12-27 11:10 .X11-unix

---

### Post by taurus on 2009-12-27
> **Tholley said:**
> yeah, there is a new directory (folder) with the same name, but after searching through the files, no sign of any .sys or .ini files.

here is the output...

total 1756
drwxrwxrwt 12 root   root     4096 2009-12-27 12:00 .
drwxr-xr-x 21 root   root     4096 2009-12-27 08:36 ..
-r--------  1 kaylen kaylen 871253 2009-12-27 11:41 **2009_0123_RT61_Linux_STA_v1.1.2.3.tar-1.bz2**
-r--------  1 kaylen kaylen 871253 2009-12-27 11:37 **2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2**


You just downloaded the same file twice.  Here is what you should do.  Move it to your own directory and unpack it from there.

```
mv 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2 ~/Desktop
cd ~/Desktop
tar xvjf 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2
cd 2009_0123_RT61_Linux_STA_v1.1.2.3
ls -la
```

---

### Post by grief -l on 2009-12-27
If you're using ndiswrapper it uses only windoze drivers (which have .sys and .ini files. I don't know whether the linux ones have them but I think not.

Gabe

---

### Post by Tholley on 2009-12-27
> **taurus said:**
> You just downloaded the same file twice.  Here is what you should do.  Move it to your own directory and unpack it from there.

```
mv 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2 ~/Desktop
cd ~/Desktop
tar xvjf 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2
cd 2009_0123_RT61_Linux_STA_v1.1.2.3
ls -la
```

I move the .tar.bz2 to the desktop and ran your code. Not sure what I should be seeing?

looks like just a list of what is on the desktop...

---

### Post by taurus on 2009-12-27
What's the output of the last command?

---

### Post by Tholley on 2009-12-27
output = 
As you can see, it is my kids computer with games on the desktop.

kaylen@kaylen-desktop:~/Desktop$ !!
ls -la
total 916
drwxr-xr-x  2 kaylen kaylen   4096 2009-12-27 12:24 .
drwxr-xr-x 52 kaylen kaylen   4096 2009-12-27 12:00 ..
-rw-r--r--  1 kaylen kaylen 871253 2009-12-27 11:47 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2
-rwxr-xr-x  1 kaylen kaylen    426 2009-11-15 16:45 childsplay.desktop
-rwxr-xr-x  1 kaylen kaylen    423 2009-12-06 09:40 extremetuxracer.desktop
-rwxr-xr-x  1 kaylen kaylen    399 2009-11-15 10:56 gnibbles.desktop
-rwxr-xr-x  1 kaylen kaylen    402 2009-12-14 19:54 gnotski.desktop
-rwxr-xr-x  1 kaylen kaylen    259 2009-12-05 14:59 icebreaker.desktop
-rwxr-xr-x  1 kaylen kaylen    301 2009-12-14 17:35 kbattleship.desktop
-rwxr-xr-x  1 kaylen kaylen    365 2009-12-06 09:41 ktuberling.desktop
-rwxr-xr-x  1 kaylen kaylen    395 2009-12-06 09:42 neverball.desktop
-rwxr-xr-x  1 kaylen kaylen    323 2009-12-06 09:42 neverputt.desktop
-rwxr-xr-x  1 kaylen kaylen    198 2009-12-06 09:41 pacman.desktop
-rwxr-xr-x  1 kaylen kaylen   8155 2009-11-15 16:47 tuxpaint.desktop
-rwxr-xr-x  1 kaylen kaylen    180 2009-12-06 09:40 xgalaga.desktop
-rwxr-xr-x  1 kaylen kaylen    211 2009-12-02 19:28 xgalaga-hyperspace (copy).desktop
kaylen@kaylen-desktop:~/Desktop$

---

### Post by Tholley on 2009-12-27
speaking of kids.... gotta take them to the park now.

will check back later!

---

### Post by taurus on 2009-12-27
What happens when you run the third command, tar, from my previous post to unpack 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2?

```
tar xvjf 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2
```

---

### Post by Tholley on 2009-12-27
> **taurus said:**
> What happens when you run the third command, tar, from my previous post to unpack 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2?

```
tar xvjf 2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2
```

Looks like it unpacked it, created the same folder as I did, when I extracted it earlier.
This is the folder... /home/kaylen/Desktop/2009_0123_RT61_Linux_STA_v1.1.2.3

In it are 2 more folders named Module and WPA Supplicant.

Still don't see the .sys or .inf files as per these instructions....
**3.3. Downloading Windows Drivers**

 
[LIST=1]
[*]Retrieve the Windows driver corresponding to your chipset: Use the ID information you have just found and the ndiswrapper [list]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page") to find and download the correct windows driver files for your wireless adapter, or one which is very similar (same chipset ID). 
[*]Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install *cabextract* and *unshield*. 
[*]If there are multiple INF/SYS files, look in the ndiswrapper [list]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/") to see if there are any hints about which of them should be used. 
[*]If you have Windows drivers on a cd and cant extract the INF file or the Bin files you can try installing the drivers on a Windows computer. Then look in control panel-system-hardware tab-device driver button. Then look for the device under network adapters. Once you have located the network adapter see what driver is being used by double clicking on the adapter in the list. Then go to the driver tab and click the driver information button. The driver and path will be listed it will usually be in C:/windows/system32/drivers folder. To be sure do a search for the file. The BIN file and INF file are usually the same name in the C:/windows/system32 folder. After you locate all the files copy to flash drive or burn to cd to move to Ubuntu computer for installation using Ndiswrapper. 
[*]Make sure that the INF file, SYS file and any BIN files are all put into one directory.
[/LIST]
**Maybe I'm reading it wrong and may not even need to do all that?**

---

### Post by taurus on 2009-12-27
Look in those two directories, Module and WPA.

```

cd ~/Desktop/2009_0123_RT61_Linux_STA_v1.1.2.3
ls -la Module
ls -la WPA
```

---

### Post by Tholley on 2009-12-27
here is the output of that... I don't see the files myself.

[B]I also tried to copy the driver files off the cd, put them in a folder named drivers in the home folder, then using System, Admin, Windows Wireless Drivers, I installed said driver, but still no workie.
[/B] 
anyway here is output...

kaylen@kaylen-desktop:~/Desktop$ cd ~/Desktop/2009_0123_RT61_Linux_STA_v1.1.2.3
kaylen@kaylen-desktop:~/Desktop/2009_0123_RT61_Linux_STA_v1.1.2.3$ ls -la Module
total 1772
drwxr-xr-x 2 kaylen kaylen   4096 2009-02-08 10:01 .
drwxr-xr-x 4 kaylen kaylen   4096 2009-12-27 13:40 ..
-rw-r--r-- 1 kaylen kaylen  50077 2008-05-05 09:24 assoc.c
-rw-r--r-- 1 kaylen kaylen  16924 2008-05-05 09:25 auth.c
-rw-r--r-- 1 kaylen kaylen   4921 2008-05-05 09:25 auth_rsp.c
-rw-r--r-- 1 kaylen kaylen     72 2007-12-10 00:47 config.mk
-rw-r--r-- 1 kaylen kaylen   3210 2007-12-10 00:47 Configure
-rw-r--r-- 1 kaylen kaylen  62177 2008-05-05 09:25 connect.c
-rw-r--r-- 1 kaylen kaylen   5482 2008-05-05 09:25 eeprom.c
-rw-r--r-- 1 kaylen kaylen    142 2007-12-10 00:47 ifcfg-ra0
-rw-r--r-- 1 kaylen kaylen   9843 2007-12-10 00:47 iwpriv_usage.txt
-rw-r--r-- 1 kaylen kaylen    107 2008-05-04 10:10 load
-rw-r--r-- 1 kaylen kaylen   2630 2008-05-04 10:02 Makefile
-rw-r--r-- 1 kaylen kaylen   2761 2007-12-10 00:47 Makefile.4
-rw-r--r-- 1 kaylen kaylen   2735 2007-12-10 00:47 Makefile.6
-rw-r--r-- 1 kaylen kaylen   1217 2007-12-10 00:47 Makefile.RTL865x
-rw-r--r-- 1 kaylen kaylen   6851 2008-05-05 09:28 mat.h
-rw-r--r-- 1 kaylen kaylen  47414 2008-05-05 09:26 md5.c
-rw-r--r-- 1 kaylen kaylen   3648 2008-05-05 09:28 md5.h
-rw-r--r-- 1 kaylen kaylen 199214 2008-05-05 09:26 mlme.c
-rw-r--r-- 1 kaylen kaylen  18248 2009-02-06 06:23 mlme.h
-rw-r--r-- 1 kaylen kaylen      0 2008-05-04 10:09 Module.markers
-rw-r--r-- 1 kaylen kaylen     67 2009-01-22 23:07 modules.order
-rw-r--r-- 1 kaylen kaylen      0 2007-12-10 02:05 Module.symvers
-rw-r--r-- 1 kaylen kaylen  27838 2008-05-05 09:28 oid.h
-rw-r--r-- 1 kaylen kaylen  11124 2007-12-10 00:47 README
-rw-r--r-- 1 kaylen kaylen   5240 2008-05-06 00:49 ReleaseNote
-rw-r--r-- 1 kaylen kaylen   8192 2007-12-10 00:47 rt2561.bin
-rw-r--r-- 1 kaylen kaylen   8192 2007-12-10 00:47 rt2561s.bin
-rw-r--r-- 1 kaylen kaylen   8192 2007-12-10 00:47 rt2661.bin
-rw-r--r-- 1 kaylen kaylen  63214 2008-05-05 09:29 rt2661.h
-rw-r--r-- 1 kaylen kaylen    477 2007-12-10 00:47 rt61sta.dat
-rw-r--r-- 1 kaylen kaylen   6532 2009-01-22 23:40 rt_config.h
-rw-r--r-- 1 kaylen kaylen   6532 2008-07-23 08:33 rt_config.h~
-rw-r--r-- 1 kaylen kaylen 139279 2008-07-23 08:32 rtmp_data.c
-rw-r--r-- 1 kaylen kaylen  28415 2008-05-05 09:29 rtmp_def.h
-rw-r--r-- 1 kaylen kaylen 118004 2008-05-05 09:29 rtmp.h
-rw-r--r-- 1 kaylen kaylen 283733 2009-01-22 22:59 rtmp_info.c
-rw-r--r-- 1 kaylen kaylen 257299 2008-07-23 08:32 rtmp_init.c
-rw-r--r-- 1 kaylen kaylen  30772 2009-01-22 23:01 rtmp_main.c
-rw-r--r-- 1 kaylen kaylen  14353 2008-05-05 09:27 rtmp_task.c
-rw-r--r-- 1 kaylen kaylen  14038 2008-05-05 09:27 rtmp_tkip.c
-rw-r--r-- 1 kaylen kaylen   5142 2008-05-05 09:29 rtmp_type.h
-rw-r--r-- 1 kaylen kaylen  12351 2008-05-05 09:27 rtmp_wep.c
-rw-r--r-- 1 kaylen kaylen   7482 2008-05-05 09:27 rtmp_wext.c
-rw-r--r-- 1 kaylen kaylen   2128 2008-05-05 09:29 rtmp_wext.h
-rw-r--r-- 1 kaylen kaylen  42201 2008-05-05 09:27 sanity.c
-rw-r--r-- 1 kaylen kaylen   5313 2007-12-10 00:47 STA_iwpriv_ATE_usage.txt
-rw-r--r-- 1 kaylen kaylen  77799 2008-05-05 09:28 sync.c
-rw-r--r-- 1 kaylen kaylen     42 2007-12-10 00:47 unload
-rw-r--r-- 1 kaylen kaylen  76567 2008-05-05 09:28 wpa.c
-rw-r--r-- 1 kaylen kaylen   7279 2008-05-05 09:29 wpa.h
kaylen@kaylen-desktop:~/Desktop/2009_0123_RT61_Linux_STA_v1.1.2.3$ ls -la WPA

---

### Post by Tholley on 2009-12-27
here is what I got when I ran this code... if it helps at all.

kaylen@kaylen-desktop:~/Desktop$ sudo ndiswrapper -i ~/drivers/rt61.inf
driver rt61 is already installed
kaylen@kaylen-desktop:~/Desktop$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt61 : driver installed
    device (1814:0301) present (alternate driver: rt61pci)

---

### Post by Tholley on 2009-12-27
then this one as per the instructions...

kaylen@kaylen-desktop:~/Desktop$ sudo depmod -a
kaylen@kaylen-desktop:~/Desktop$   sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
kaylen@kaylen-desktop:~/Desktop$ tail /var/log/messages
Dec 27 14:08:42 kaylen-desktop kernel: [10742.370454] sd 2:0:0:0: [sdb] 2015232 512-byte hardware sectors: (1.03 GB/984 MiB)
Dec 27 14:08:42 kaylen-desktop kernel: [10742.416294] sd 2:0:0:0: [sdb] Write Protect is off
Dec 27 14:08:42 kaylen-desktop kernel: [10742.421963] sd 2:0:0:0: [sdb] 2015232 512-byte hardware sectors: (1.03 GB/984 MiB)
Dec 27 14:08:42 kaylen-desktop kernel: [10742.422701] sd 2:0:0:0: [sdb] Write Protect is off
Dec 27 14:08:42 kaylen-desktop kernel: [10742.422724]  sdb: sdb1
Dec 27 14:08:42 kaylen-desktop kernel: [10742.550946] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Dec 27 14:08:42 kaylen-desktop kernel: [10742.551099] sd 2:0:0:0: Attached scsi generic sg2 type 0
Dec 27 14:09:13 kaylen-desktop kernel: [10773.957404] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Dec 27 14:09:13 kaylen-desktop kernel: [10773.994854] usbcore: registered new interface driver ndiswrapper
Dec 27 14:10:36 kaylen-desktop kernel: [10856.278585] eth0: link down.

---

### Post by grief -l on 2009-12-27
Repeating myself from post #7

> If you're using ndiswrapper it uses only windoze drivers (which have .sys and .ini files. I don't know whether the linux ones have them but I think not.

---

### Post by Tholley on 2009-12-27
> Repeating myself from post #7

     Quote:
                    If you're using ndiswrapper it uses only windoze drivers (which have .sys and .ini files. I don't know whether the linux ones have them but I think not.
Not sure what your getting at... ?
I believe ndiswrapper utilizes the win .inf driver files so that a wireless adapter designed for windows, will work in Linux.

I'm now starting to wonder if my router is just so old, it wont work with the newer adapters.
My other computer with Ubuntu and windows (dualboot) works fine with it's older adapter, but have not been able to connect to the old linksys router even with a newer windows machine. :confused:

---

### Post by grief -l on 2009-12-27
> I downloaded again and saved the file, extracted it I think, but **not seeing the .sys or .inf files that the ndiswrapper instructions say to look for**.
 

Well I may be talking out of both ends so forgive me if I'm wrong. I went down the ndiswrapper road and the .sys and inf files are **not in a Linux_STA file.** They're in a windoze driver folder. I took them straight out of the install disk that came with the dongle. I was never given any list of Linux_STA drivers to look for or mess with.

Hope that's of some help.

Gabe

---


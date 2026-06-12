---
title: "Cannot mount sims 3 iso/cd"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by uncibex on 2009-07-09
I am trying to install Sims 3 through play on linux, but I have been unable to actually mount the image to begin the installation

I have a dvd with the image that runs flawlessly in windows, but will not mount in ubuntu, I also have the image file that I have not been able to mount from my hdd, my external drive, or any other combination of things that I have tried

After searching through forums for the past couple days, I have found the following suggestions, but none of them have worked:

1.Install scripts to mount the iso from a hard disk
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

-prompted for password, see the notification with the correct iso and location, then I get an error message from ISO mounter that says, "Cannot mount!"

2. Mount dvd manually
[http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html)

$mount /media/dvd
mount: can't find /media/dvd/ in /etc/fstab or /etc/mtab
$mount /media/cdrom
mount: no medium found on /dev/sr0

3. Mount using gmount-iso
[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

-with .iso file on hard drive:
  -selected .iso file for "image file (.iso)"
  -selected empty folder (after a bit of trial and error) for "mount point"
  -error: "An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

(I don't know if I'm using this program correctly, honestly)


I've never tried to mount an .iso inside of ubuntu before and would really appreciate any help that you could give!  Like I said, I do know that the dvd is good - it runs in windows, and I also know that my cd drive is good as it mounts other cds and dvds fine.

---

### Post by uncibex on 2009-07-09
also, I'd prefer to not have to run an emulator if at all possible.  I feel like this defeats the purpose of running linux =)

---

### Post by CLomax on 2009-07-09
Do **sudo mount -t auto -o loop /path/to/sims.iso /your/mount/point**

That should stop the *wrong fs type* error and mount the .iso.

I suggest using PlayOnLinux to install it: [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) as it automatigically does all the configuring of WINE for you.

---

### Post by Jazzy_Jeff on 2009-07-09
> **uncibex said:**
> also, I'd prefer to not have to run an emulator if at all possible.  I feel like this defeats the purpose of running linux =)

I don't know if this program will run natively on Linux. Never played it.

---

### Post by CLomax on 2009-07-09
I'll be pendantic and point out that WINE isn't an emulator. In fact, that's what it stands for: **W**INE **I**s **N**ot and **E**mulator.

And to clear up any confusion, PlayOnLinux is almost like a front-end for installing WINE programs which does all the required patching, configuration and such automatically.

The Sims 3 is definitely on the PlayOnLinux list.

---

### Post by uncibex on 2009-07-09
> **CLomax said:**
> Do **sudo mount -t auto -o loop /path/to/sims.iso /your/mount/point**

Thanks so much!  That mounted just fine.  I've still got a few things to work out inside of playonlinux, but getting the iso mounted was the only thing that was really causing me problems.

---

### Post by redshift88 on 2009-07-31
I used the above code and it still asks me to specify a file type.  


sudo mount -t auto -o loop /home/andrew/Desktop/sims3/Sims3.iso /home/andrew/Desktop/mount

mount: you must specify the filesystem type

---

### Post by redshift88 on 2009-08-01
I also tried...

sudo mount -o loop -t iso9660 ~/Desktop/sims3/Sims3.iso ~/Desktop/mount
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by redshift88 on 2009-08-02
Did a reinstall of ubuntu with no improvement.

andrew@awesome-hp:~$ dmesg | tail
[ 1660.608939] wlan0: disassociating by local choice (reason=3)
[ 1663.041535] wlan0: deauthenticated
[ 1684.956722] wlan0: authenticate with AP 00:14:bf:4b:51:6b
[ 1684.958528] wlan0: authenticated
[ 1684.958534] wlan0: associate with AP 00:14:bf:4b:51:6b
[ 1684.960846] wlan0: RX AssocResp from 00:14:bf:4b:51:6b (capab=0x411 status=0 aid=1)
[ 1684.960852] wlan0: associated
[ 3596.752206] ISOFS: Unable to identify CD-ROM format.
[ 3722.182069] ISOFS: Unable to identify CD-ROM format.
[ 3738.376450] ISOFS: Unable to identify CD-ROM format.
andrew@awesome-hp:~$ 


Why me?

---

### Post by redshift88 on 2009-08-02
Okay, I found this.

[http://ubuntuforums.org/showthread.php?t=707555&page=2](http://ubuntuforums.org/showthread.php?t=707555&page=2)

Is this my problem?


I also found this [http://ubuntuforums.org/showthread.php?t=180668](http://ubuntuforums.org/showthread.php?t=180668)

I used the file command to see what kind of file system my .iso is, and it says data.  So, I used the command presented on this website to a directory instead of a usb drive.  The process completes, but there is nothing inside my destination folder.  My target directory is /home/andrew/Desktop/Rename


andrew@awesome-hp:~/Desktop$ sudo dd if=Sims3.iso of=/Rename
11658112+0 records in
11658112+0 records out
5968953344 bytes (6.0 GB) copied, 380.84 s, 15.7 MB/s
andrew@awesome-hp:~/Desktop$

---

### Post by RedSh on 2009-12-05
i have THE SAME problem... and no solution or hopes to get this game working.

anyone? :KS

---

### Post by TanelSargava on 2012-04-19
I have that same problem. Trying to mount heroes of might and magic 5 .iso file. Gmount kind of mounts it, but when opening it, it doesn't show any files. When using command-line, writing ```
mount -t udf -o loop filename.iso /path/to/mount
``` it states me that it's a wrong filesystem, also states the same thing for '-t iso9660/nfs/auto' and leaving blank aswell.... WHAT MUST I DO?! :(

---

### Post by jerome1232 on 2012-04-19
On my system (Ubuntu 11.10) If I right click an iso one of the options in the context menu is to "open with" when I highlight that an option is "archive mounter" if I open the iso with archive mounter it gets automatically mounted.

Try that.

---

### Post by TanelSargava on 2012-04-19
Yes, it mounts it (or something) but it doesn't show anything in the .iso file. It's totally empty, although the .iso file size is 4,4GB AND the MD5 checksum is correct aswell.

---


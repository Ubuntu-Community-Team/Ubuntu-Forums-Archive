---
title: "this is making me mad"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by strivehosting on 2007-03-14
I went to here. [http://132.68.73.235/linmodems/first.html](http://132.68.73.235/linmodems/first.html) and I followed all of the instructions correctly but when i get to the ls /mnt part and type it into terminal, nothing happens. I then typed the cp /mnt/msdos/temp/scanModem.gz . but a No such file or directory error came up. Btw, im using a dell 1501 laptop if that changes anything. Oh, also im dual booting XP and Ubuntu.

---

### Post by JAwuku on 2007-03-14
Which point is your Windows partition mounted at? In my install, it's usually in a directory such as /media/Windows.

type ```
cat /etc/fstab
```

Just substitute /mnt/msdos with whatever your Windows mount point is at.

---

### Post by strivehosting on 2007-03-14
Well, I sorta forget what exactly it is. Is there any way I can see where its pointed to?

---

### Post by yabbadabbadont on 2007-03-14
> **JAwuku said:**
> Which point is your Windows partition mounted at? In my install, it's usually in a directory such as /media/Windows.

type ```
cat /etc/fstab
```

Just substitute /mnt/msdos with whatever your Windows mount point is at.

strivehosting: Did you do what he suggested?  If not, do so and if the answer isn't obvious (it might not be), please post the output here.

---

### Post by JAwuku on 2007-03-14
It may be that your windows partition is not mounted. 

What is the output of ```
cat /etc/fstab
```

of just simply type ```
mount
```

to see all your mounted partitions.

Usually your windows partition is on the line /dev/hda1 or /dev/sda1. The mount point is next to it.

For example on my system the entry in /etc/fstab is:

```
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

the mount-point being **/media/windows** 

If there is no Windows mount point, follow the ubuntuguide.org (Quotes and my alterations detailed below):

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only 

e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
 
Local mount folder: /media/windows 

```
sudo mkdir /media/windows

sudo cp /etc/fstab /etc/fstab_backup

gksudo gedit /etc/fstab (kdesu kate /etc/fstab for kde)
```

Append the following line at the end of file 

```
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```
save the file

type ```
sudo mount -a
``` to remount without rebooting

---

### Post by strivehosting on 2007-03-14
#
#
#<file system> <mount point>   <type>  <options>   <dump>  <pass>
proc                   /proc               proc       defaults        0           0
# /dev/sda5
UUID=7ddbd1ca-3d0b-471e-8721-4845908f6b48 /        ext 3       defaults,error
s=remount-ro 0
# /dev/sda6
UUID=304324cd-62e9-4d82-a87f-86dec9a6983a  none    swap       sw
   0              0     
/dev/hda             /media/cdrom0       udf,iso9660  user,noauto  0    0

-yea thats what I got. Now what. I know im a noob. Sorry and thanks for the help guys.

---

### Post by yabbadabbadont on 2007-03-14
Try running in a terminal window, "sudo fdisk -l"  (without the quotation marks ;))

Please post the output.

---

### Post by strivehosting on 2007-03-14
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280

  Device Boot        Start              End         Blocks       Id    System
/dev/sda1               1                  9            72261      de      Dell Utility
/dev/sda2  *           10                5108     40957717    7       HPFS/NTFS
/dev/sda3             6844              7295        3630690   db     CP/M / CTOS / ...
/dev/sda4             5109              6843      13936387+  5      Extended
/dev/sda5  *         5109              6768      13333918+  83      Linux
/dev/sda6             6769              6843           602406  82   Linux swap / Solaris

Partition table entries are not in disk order

-Sorry it took so long. I have to type it manually because I'm on a whole separate computer.

---

### Post by yabbadabbadont on 2007-03-14
```
/dev/sda2 * 10 5108 40957717 7 HPFS/NTFS
```
That is your windows partition.  See the following for details on mounting windows partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by strivehosting on 2007-03-14
Alright thank you.

---

### Post by strivehosting on 2007-03-14
alright im kind of confused nowt hat you both have posted separate links..which one should i use for my problem?

---

### Post by yabbadabbadont on 2007-03-14
Read both, follow whichever one seems easier to you.  :D

---

### Post by strivehosting on 2007-03-14
lol alrighty probably yours.

---

### Post by strivehosting on 2007-03-14
Ahh, sorry but i have one more question. When im editing it do i put this in exactly: 
/dev/sda2 * 10 5108 40957717 7 HPFS/NTFS 
or would i put
/dev/sda2 /windows ntfs (but what do i put here)
or am i completely off?

---

### Post by yabbadabbadont on 2007-03-14
Like Jawuku posted earlier:

```
/dev/sda2 /windows  ntfs  nls=utf8,umask=0222 0    0
```

Always better to ask if you are unsure though.  :D

That will give you read-only access to your ntfs partition.  (which is the only kind that is safe without installing extra software and configuring it)

---

### Post by strivehosting on 2007-03-14
alright it worked. one last question about the scanModem.gz.
I typed cp /windows/temp/scanModem.gz and it says cp: missing destination file operand after `/windows/temp/scanModem.gz'
but when i put the dot(period) after it like this cp /windows/temp/scanModem.gz . it says No such file or directory..
Whats my problem now :(

---

### Post by yabbadabbadont on 2007-03-14
What does "ls -l /windows/temp" return?

Edit:
```
ls -l /windows/temp
```

(In code tags so that it will be easier to read)

---

### Post by strivehosting on 2007-03-14
says no such file or directory

---

### Post by yabbadabbadont on 2007-03-14
Did you forget to mount your windows partition?
```
sudo mount /windows
```

---

### Post by strivehosting on 2007-03-14
Lol, alrighty i did that and now it says cant find /windows in /etc/fstab or /etc/mtab so I guess i messed something up completely! Should I just start completely over?

---

### Post by yabbadabbadont on 2007-03-14
That might be the easiest thing to do at this point.  :lol:

---

### Post by strivehosting on 2007-03-14
Lol, I'm such a noob at this. I'm sorry man, but thank you so much for your help.

---

### Post by yabbadabbadont on 2007-03-14
No problem.  Post back here if you still have issues after going through the instructions a second time.  If I can't help, I'm sure there will be someone here who can.

Edit: You may want to print out those instructions for easy access while making the changes.

---

### Post by strivehosting on 2007-03-15
well I figured out what i did wrong and corrected it. It was just a # sign infront of my partition lol. Thank  you so much for your help!

---

### Post by amaurynieto on 2007-08-01
Hey Strive

Here you go:

Download this driver from Dell (it's a self installing DEB file for 32 bit only)

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

Then reboot (it's restricted driver manager so it needs to reboot).

Get GNOME PPP (software to dial up through Automatix)
([www.getautomatix.com](www.getautomatix.com))

You're set.

A.
(I have a 1501 and this works for me straight out of the box.)

Thank Dell for liberating us from the STUPID tax Linuxant levvies upon their users for full hardware compatibility on Conexant Modems

(the free driver from Linuxant has a Data-only-14.4k-cap)

Shame on them. Thank Dell :)

---


---
title: "HELP! Grub error 22 on daul boot acer"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by helamsirrine on 2010-01-13
I have an Acer aspire x1301w/ AMD athlonIIx2 and I am dual booting the copy of windows 7 that came with it, and 32-bit Ubuntu 9.10. My 320 Gb hard drive is partitioned w/ about 70 Gb(ntfs) for windows and a 220 Gb(ext3) for Karmic. The rest is taken up by swap and by the 14 Gb Acer windows install partition.

On the Grub boot loader Both the windows 7 installation and the Acer install partition are named "Windows(loader)". I selected windows(loader) from the grub, and then went to the can while I waited for windows to boot up. When I came back I was on the front screen of the Acer install/repair partition..oops. I immediately hit the 'exit' option and rebooted my computer.

Now when I boot I immediately get a grub error 22 and crash. I can't boot windows or linux.

I put in my 64-bit 9.10 live CD and checked for drive errors. none. Then I ran the Ubuntu install and clicked through to the partitioner. It shows a 220 Gb unallocated space almost the entire size of sda4(my ext3 part). I quit out and am on the Live Karmic now. 
I opened up GParted and following the ntfs parts it shows: 
> /dev/sda4 
file system: extended
mount point: 
label: 
size: 216.11 GiB used: --- unused: ---[INDENT]unallocated/unallocated blank/blank
size: 215.95 GiB used: --- unused: ---
[/INDENT][INDENT]/dev/sda5
file system: linux-swap size: 172.54MiB[/INDENT]Is my data gone? I cant see how. I was only away from the computer a few moments, not nearly long enough to format a partition. 

I tried to re-install the grub from the terminal based on info from this thread:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+22](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+22)

Step one:
```
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ 

```I got a grub error 22 when I first set up the system, but then I simply reinstalled Karmic. I could do that because it was a new computer with no imprtant data on it. That is not the case now. I  intend to copy that Acer Install to CD and delete that partition. Then I'll copy all my important data to the windows partition, reformat sda4 and the unallocated space as ext4, install and set up 64-bit Karmic on the new partition, and finally copy the data back to my fresh linux system.

To do this I first need to fix the boot loader, assuming my data is still there. I am a n00b.. Please HELP!

EDIT:
tried from same thread linked above
> ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda4 /mnt/root
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by tom.swartz07 on 2010-01-13
> **helamsirrine said:**
> I have an Acer aspire x1301w/ AMD athlonIIx2 and I am dual booting the copy of windows 7 that came with it, and 32-bit Ubuntu 9.10. My 320 Gb hard drive is partitioned w/ about 70 Gb(ntfs) for windows and a 220 Gb(ext3) for Karmic. The rest is taken up by swap and by the 14 Gb Acer windows install partition.

On the Grub boot loader Both the windows 7 installation and the Acer install partition are named "Windows(loader)". I selected windows(loader) from the grub, and then went to the can while I waited for windows to boot up. When I came back I was on the front screen of the Acer install/repair partition..oops. I immediately hit the 'exit' option and rebooted my computer.

Now when I boot I immediately get a grub error 22 and crash. I can't boot windows or linux.

I put in my 64-bit 9.10 live CD and checked for drive errors. none. Then I ran the Ubuntu install and clicked through to the partitioner. It shows a 220 Gb unallocated space almost the entire size of sda4(my ext3 part). I quit out and am on the Live Karmic now. 
I opened up GParted and following the ntfs parts it shows: 
Is my data gone? I cant see how. I was only away from the computer a few moments, not nearly long enough to format a partition. 

I tried to re-install the grub from the terminal based on info from this thread:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+22](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+22)

Step one:
```
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ 

```I got a grub error 22 when I first set up the system, but then I simply reinstalled Karmic. I could do that because it was a new computer with no imprtant data on it. That is not the case now. I  intend to copy that Acer Install to CD and delete that partition. Then I'll copy all my important data to the windows partition, reformat sda4 and the unallocated space as ext4, install and set up 64-bit Karmic on the new partition, and finally copy the data back to my fresh linux system.

To do this I first need to fix the boot loader, assuming my data is still there. I am a n00b.. Please HELP!

Alrighty! Lets get cracking.

Before we start, I need some vital information about your hard drive.


Could you post the output of 
```
sudo fdisk -l
```

and assure that any information that is vital (i.e. you cant get it back again) is backed up to a safe place? Although the chances you will lose any data are slim, it is always better to be sure before you perform a triage such as this.


Let me know and we could get started!

---

### Post by helamsirrine on 2010-01-13
I am a noob, but I did explain my inability to boot my system, and therefore access and back up my data. Won't "sudo fdisk" format my drive?

---

### Post by tom.swartz07 on 2010-01-13
> **helamsirrine said:**
> I am a noob, but I did explain my inability to boot my system, and therefore access and back up my data. Won't "sudo fdisk" format my drive?

yeah, i understand. sorry i wasnt more clear. You said that you were running the liveCd, so i assumed you would continue to do so.


While in the livecd, run that command from the terminal. its a command that outputs the basic layout of your drive. It will help me, or others, get a handle on what your drive looks like so that we could re-install Grub and boot your system.


My output for fdisk looks like this; just in case youre wary.
```
tom@ubuntu-karmic:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       11904    85064175    7  HPFS/NTFS
/dev/sda4           11905       38913   216949792+   f  W95 Ext'd (LBA)
/dev/sda5           19233       19558     2618595   dd  Unknown
/dev/sda6           11905       18723    54773554+  83  Linux
/dev/sda7           18724       19232     4088511   82  Linux swap / Solaris
/dev/sda8           22979       24571    12795741   83  Linux
/dev/sda9           24572       36181    93257293+   7  HPFS/NTFS

Partition table entries are not in disk order
tom@ubuntu-karmic:~$ 

```


Thats pretty much all I need to help you get your system back to a workable state.

Again, sorry for the confusion.

---

### Post by helamsirrine on 2010-01-13
No, I'm sorry, thanks for the help. I am new to the terminal and my only familiarity w/ an 'fdisk' command comes from dos. Here's my terminal output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4577cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1785    14336000   27  Unknown
/dev/sda2   *        1785        1798      102400    7  HPFS/NTFS
/dev/sda3            1798       10701    71516358+   7  HPFS/NTFS
/dev/sda4           10702       38913   226612890    5  Extended
/dev/sda5           38892       38913      176683+  82  Linux swap / Solaris

Disk /dev/sdd: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          16        7748     1979456    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 


```

---

### Post by tom.swartz07 on 2010-01-13
> **helamsirrine said:**
> No, I'm sorry, thanks for the help. I am new to the terminal and my only familiarity w/ an 'fdisk' command comes from dos. Here's my terminal output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4577cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1785    14336000   27  Unknown
/dev/sda2   *        1785        1798      102400    7  HPFS/NTFS
/dev/sda3            1798       10701    71516358+   7  HPFS/NTFS
/dev/sda4           10702       38913   226612890    5  Extended
/dev/sda5           38892       38913      176683+  82  Linux swap / Solaris

Disk /dev/sdd: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          16        7748     1979456    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

```

No worries, bro.

Alrighty. From the looks of it, you just have Windows on your drive. What has me confused is the fact that you have a massive space on the beginning of your drive... I guess thats the mystery format that you were talking about. Whatever it was, isnt there anymore.
Lets work on that first.

Open GParted from the system panel. system>administration>gparted (if its not installed, you could grab it from the software center)

Run that, and post a screenshot here before going on, if possible.

I would suggest that the easiest way to fix this problem is to re-install in that unallocated area in the beginning of your drive.

Follow this guide: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Skip the part about using the entire drive, and just select 'install side-by-side'.

The bottom bar will allow you to change how much space is used. Take it from there.


After the install goes, it should fix everything. I guess you had a bad install and it just formatted the area on the drive.

---

### Post by helamsirrine on 2010-01-13
Well, here's the scrrenshot of GParted.
[attach]143538[/attach]

Are you saying that my linux patition has been deleted? 'cause that's where all my data was.

---

### Post by tom.swartz07 on 2010-01-13
> **helamsirrine said:**
> Well, here's the scrrenshot of GParted.
[attach]143538[/attach]

Are you saying that my linux patition has been deleted? 'cause that's where all my data was.

Unfortunately, thats what it looks like. /dev/sda5 shouldve been your ubuntu partition, but its no longer there...
Can you mount the partition? When you go to places>computer, does it have your ubuntu partition listed?


One more thing we could check before all hope is lost. You might have bad blocks...

in the terminal again-```
sudo badblocks /dev/sda
``` and ```
sudo fsck /dev/sda
```

See what they say and post back. It might be that your drive has some bad blocks on it that make the ubuntu partition unreadable.

---

### Post by Sef on 2010-01-13
>  Are you saying that my linux patition has been deleted? 'cause that's where all my data was.

You might be able to get that partition back with [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by helamsirrine on 2010-01-13
thanks for all the help

---

### Post by tom.swartz07 on 2010-01-13
> **helamsirrine said:**
> how long would you estimate to get an output from the badblocks command? my terminal seemsto be working w/no text output after entering command for quite a few minutes now.

it takes a little while, depends on the speed of your drive. I would say if its not done after 15 or 20 minutes though, hit CTRL and Z to quit out of it.

Like Sef said, you might still be able to recover the data with the methods from that link.


If the test turns up that you have bad blocks on your drive, it would be best if you got a new one, or-if its in warranty- get it replaced. fsck should check the disk one more time and fix the badblocks.

---


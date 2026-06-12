---
title: "Managed to do some damage partition resize"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Shrimply on 2009-01-25
Hi, 

Thought I'd start by explaining that this computer is for messing about on and getting used to ubuntu so am not too worried about messing things up, hence why I just do them and get myself into these situations.  So most of this problem you will read thinking I'm a total idiot.

Basically i had a very small ubuntu partition and it was basically full.  So I booted to usb stick and used partition manager to enlarge the partition from 8gb to 20gb, and enlarged the swap partition to 1gb (I fear this is the problem)and the other ( sorry forget its name) to fill the rest of the space.

But on booting Ubuntu is now so slow its practically unusable, I've tried resizing the swap partition back to 300mb but its made no difference.  Any ideas what I can do to get it working again?

---

### Post by Rim on 2009-01-25
<.< with swap u should stick with 1/2 of ur total ram installed always ^^. But i dun get it..<.< how come ti got slower? Hmm <.< when i put on Ubuntu i used 1 gb for the swap 8gb for the "/" ^^ trust me its enough and the rest of the hard drive for the "/home", it works super fast. 

o.o u can try getting back to 8 gb for the root and seting up a new partition for your personal folders "/home". One advantage of this is that u can reinstall ubuntu again anad again if need be on the root ^^ but u will still have all ur files in the "/home" partition.

---

### Post by kestrel1 on 2009-01-25
I would recommend using a /home partition as mentioned above. I have Ubuntu 8.04 & 8.10 using the same /home. Works good for me.

---

### Post by Shrimply on 2009-01-25
Thanks I'll take that onboard regarding the space issue but I don't think its really going to help me right now.  When I say slow I mean ridiculously slow, like i can hardly move the mouse, nothing will work, I can't even get the shutdown options to come up.

I also resized my XP partition and its working fine, I don't know if that's important or not.

---

### Post by Shrimply on 2009-01-25
It's really beginning to get me down now, I mean it is unusable once I get past the log in screen which is fine.

And it was running so well yesterday.

---

### Post by KIAaze on 2009-01-25
Maybe this can help:
[https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27](https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27)

But since you said this PC is for messing around, you might as well reinstall with the new sizes you want.

---

### Post by kestrel1 on 2009-01-25
If it is only a test machine, why not re-install & use the following partitions:
```
/ (root partition for OS)
/home (for all personal files & settings)
/swap (ummm swap)

```
I have about 8gb for the OS, a larger partition (25gb+) for /home & 1gb swap

---

### Post by Shrimply on 2009-01-25
I know reinstalling is probably the sensible thing to do, I had hoped for another solution after I spent most of yesterday getting my internet connection to work after upgrading to 8.10.

---

### Post by caljohnsmith on 2009-01-25
How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
And for whichever is your main Ubuntu partition, try:
```
sudo fsck -yCM /dev/sdaX
```
And replace sdaX with the Ubuntu partition. If fsck is successful, how about doing:
```
sudo mount /dev/sdaX /mnt && ls -l /mnt
df -h
```
And please post the output. We can work from there if you want.

---

### Post by Shrimply on 2009-01-25
Thank you here's the output for the three commands

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004bc13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31455269    15727603+   7  HPFS/NTFS
/dev/sda2        31455270   114350669    41447700    7  HPFS/NTFS
/dev/sda3       114350670   156296384    20972857+   5  Extended
/dev/sda5       114350733   155685914    20667591   83  Linux
/dev/sda6       155685978   156296384      305203+  82  Linux swap / Solaris

Disk /dev/sdb: 4126 MB, 4126146560 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8058880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ba852

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1477979      738958+   6  FAT16
/dev/sdb2         1477980     8048564     3285292+  83  Linux


> fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda5: clean, 167156/1294336 files, 1440136/5166897 blocks

> ls: cannot access df: No such file or directory
/mnt:
total 120K
drwxr-xr-x   2 root root 4.0K 2009-01-24 01:46 bin
drwxr-xr-x   3 root root 4.0K 2009-01-25 14:24 boot
lrwxrwxrwx   1 root root   11 2008-09-05 19:23 cdrom -> media/cdrom
drwxr-xr-x   5 root root  12K 2009-01-24 08:04 dev
drwxr-xr-x 143 root root  12K 2009-01-25 15:10 etc
drwxr-xr-x   4 root root 4.0K 2008-09-07 18:24 home
drwxr-xr-x   2 root root 4.0K 2008-07-02 10:16 initrd
lrwxrwxrwx   1 root root   32 2009-01-24 08:06 initrd.img -> boot/initrd.img-2.6.27-9-generic
drwxr-xr-x  18 root root  12K 2009-01-24 16:04 lib
drwx------   2 root root  16K 2008-09-05 19:22 lost+found
drwxr-xr-x   3 root root 4.0K 2009-01-25 15:10 media
drwxr-xr-x   2 root root 4.0K 2008-04-15 05:53 mnt
drwxr-xr-x   3 root root 4.0K 2008-09-06 15:55 opt
drwxr-xr-x   2 root root 4.0K 2008-04-15 05:53 proc
drwxr-xr-x  19 root root 4.0K 2009-01-24 15:35 root
drwxr-xr-x   2 root root 4.0K 2009-01-24 08:26 sbin
drwxr-xr-x   2 root root 4.0K 2008-07-02 10:16 srv
drwxr-xr-x   2 root root 4.0K 2008-04-19 05:05 sys
drwxrwxrwt   6 root root  12K 2009-01-25 15:11 tmp
drwxr-xr-x  13 root root 4.0K 2009-01-24 01:50 usr
drwxr-xr-x  15 root root 4.0K 2008-07-02 10:34 var
lrwxrwxrwx   1 root root   29 2009-01-24 08:06 vmlinuz -> boot/vmlinuz-2.6.27-9-generic

Hope thats right

---

### Post by caljohnsmith on 2009-01-25
So while you still have sda5 mounted on /mnt, please post:
```
df -h
```

---

### Post by llamakc on 2009-01-25
Is swap enabled?

You can check the output of

```

cat /proc/swaps

```

and enable swap with the command:

```

sudo swapon /dev/sdXZ

```

Where /dev/sdXZ points to your swap partition.

---

### Post by Shrimply on 2009-01-25
Sorry still getting used to the command lines

> Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 125M   17M  109M  13% /lib/modules/2.6.24-19-generic/volatile
tmpfs                 125M   17M  109M  13% /lib/modules/2.6.24-19-generic/volatile
varrun                125M   92K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   64K  125M   1% /dev
devshm                125M   12K  125M   1% /dev/shm
tmpfs                 125M   20K  125M   1% /tmp
gvfs-fuse-daemon      125M  5.9M  120M   5% /home/ubuntu/.gvfs
/dev/sdb2             3.2G  5.5M  3.0G   1% /media/disk
/dev/sda5              20G  5.4G   14G  28% /mnt
/dev/sda1              15G  6.7G  8.4G  45% /media/disk-1

---

### Post by caljohnsmith on 2009-01-25
OK, that's a good sign, your sda5 main Ubuntu partition isn't full. While sda5 is still mounted on /mnt, please post:
```
sudo blkid -c /dev/null
cat /mnt/etc/fstab
cat /mnt/etc/initramfs-tools/conf.d/resume
```

---

### Post by Shrimply on 2009-01-25
here you go, thanks for all the help

> /dev/sda1: UUID="B89CCD9A9CCD5392" TYPE="ntfs" 
/dev/sda2: UUID="14A631021624A6BB" TYPE="ntfs" 
/dev/sda5: UUID="757b8e44-cdd3-4e5c-877d-362d9521a4ea" TYPE="ext3" 
/dev/sda6: UUID="aa3eacf9-c069-423a-97b1-ee6b953433a3" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="ubuntu8" UUID="48B9-64F3" TYPE="vfat" 
/dev/sdb2: UUID="b84b6bb6-e469-4071-8ad9-01194e8282d9" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=757b8e44-cdd3-4e5c-877d-362d9521a4ea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=885684e5-72d4-41ca-a975-caaf537def39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

> RESUME=UUID=885684e5-72d4-41ca-a975-caaf537def39

---

### Post by caljohnsmith on 2009-01-25
OK, I see at least part of the problem; both your fstab and resume file are using "885684e5-72d4-41ca-a975-caaf537def39" as the UUID for your swap partition, but according to blkid, your swap partition's UUID is now "aa3eacf9-c069-423a-97b1-ee6b953433a3". Usually the easiest way to fix that type of problem is to simply change the UUID of the swap partition back to what it originally was, so how about doing:
```
sudo swapoff -a && sudo mkswap -U 885684e5-72d4-41ca-a975-caaf537def39 /dev/sda6
```
Then reboot into your Ubuntu install, and do:
```
mount
free
```
And please post the output.

---

### Post by Shrimply on 2009-01-25
Sorry bit of a problem, the install doesn't run well enough to get the terminal open

---

### Post by caljohnsmith on 2009-01-25
OK, can you boot into Ubuntu "recovery mode" from the Grub menu? If so, once you get to the command line, try:
```
top
```
And see which processes are eating the most CPU time. Also let me know if it is still really slow in recovery mode. Does it take a long time to boot into Ubuntu in normal mode? Or is it only once you get into Ubuntu that everything slows to a crawl?

---

### Post by Shrimply on 2009-01-25
Hi, probably a stupid question but what do I choose in the recovery mode.

I chose something and got a list of process but the cpu usage  jumps between 0% and 100% with PID USER 4590 using the 100%, so don't know if thats the right thing or not.

Loading in normal mode seems to be slightly slower than usual but it loads everything fine.

The login screen responds as normal and the loading doesn't seem much slower.

---

### Post by caljohnsmith on 2009-01-25
So you're saying when you boot normally into Ubuntu, it seems to boot fine and doesn't take an excessive amount of time to boot? But once you get into Ubuntu, if you try and open a terminal, it takes forever? When you normally boot into Ubuntu, if you do "Alt-F2", then enter "gnome-terminal", does that bring up a terminal, or does it hang forever?

---

### Post by Shrimply on 2009-01-25
Yeah pretty much.

I just tried and got as far as typing gnome before it froze up.

---

### Post by Shrimply on 2009-01-25
Don't know if this helps but i used failsafe terminal to put in the commands you asked for before, hope you can read it all right

[ATTACH]100995[/ATTACH]

---

### Post by caljohnsmith on 2009-01-25
Let's do a quick sanity check to make sure the swap UUID changes went through, so please do the following from your Live CD:
```
sudo blkid -c /dev/null
sudo mount /dev/sda5 /mnt
cat /mnt/etc/fstab
cat /mnt/etc/initramfs-tools/conf.d/resume
```

---

### Post by Shrimply on 2009-01-25
OK thanks

> /dev/sda1: UUID="B89CCD9A9CCD5392" TYPE="ntfs" 
/dev/sda2: UUID="14A631021624A6BB" TYPE="ntfs" 
/dev/sda5: UUID="757b8e44-cdd3-4e5c-877d-362d9521a4ea" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f8b00408-5859-8ebf-7c8b-0408a4befab7" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="ubuntu8" UUID="48B9-64F3" TYPE="vfat" 
/dev/sdb2: UUID="b84b6bb6-e469-4071-8ad9-01194e8282d9" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=757b8e44-cdd3-4e5c-877d-362d9521a4ea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=885684e5-72d4-41ca-a975-caaf537def39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


> RESUME=UUID=885684e5-72d4-41ca-a975-caaf537def39

---

### Post by caljohnsmith on 2009-01-25
I don't get it, because your swap partition UUID is still incorrect. How about doing:
```
sudo swapoff -a && sudo mkswap -U 885684e5-72d4-41ca-a975-caaf537def39 /dev/sda6
sudo blkid -c /dev/null
```
And please post the output of the above commands.

---

### Post by Shrimply on 2009-01-25
Its saying permission denied for /dev/sda6

Sorry this is taking so long

---

### Post by caljohnsmith on 2009-01-25
Are you doing those commands from the Live CD? Can you copy/paste the output from the terminal so I can see exactly what happened?

---

### Post by phantomjoker on 2009-01-25
Can someone explain why you don't want too much swap space? I think i have 7GB!

is this a problem?

---

### Post by Shrimply on 2009-01-25
yes this is from the live cd it just says

> /dev/sda6: Permission denied

and the second one is the same as previously

---

### Post by caljohnsmith on 2009-01-25
What I mean is please copy/paste your terminal session showing where you entered the command, and then what the output is. How about trying again with the commands on separate lines:
```
sudo swapoff -a
sudo mkswap -U 885684e5-72d4-41ca-a975-caaf537def39 /dev/sda6
sudo blkid -c /dev/null
```

---

### Post by Shrimply on 2009-01-25
sorry i misunderstood

> ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo mkswap -U 885684e5-72d4-4lca-a975-caaf537def39 /dev/sda6
Setting up swapspace version 1, size = 312520 kB
no label, UUID=f8b00408-8842-a2bf-7c8b-0408a46eeeb7
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="B89CCD9A9CCD5392" TYPE="ntfs" 
/dev/sda2: UUID="14A631021624A6BB" TYPE="ntfs" 
/dev/sda5: UUID="757b8e44-cdd3-4e5c-877d-362d9521a4ea" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f8b00408-8842-a2bf-7c8b-0408a46eeeb7" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="ubuntu8" UUID="48B9-64F3" TYPE="vfat" 
/dev/sdb2: UUID="b84b6bb6-e469-4071-8ad9-01194e8282d9" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 

---

### Post by caljohnsmith on 2009-01-25
For some reason mkswap does not seem to let you change the UUID, so please post:
```
lsb_release -a
cat /etc/issue
apt-cache policy util-linux
sudo swapon -s
```

---

### Post by Shrimply on 2009-01-25
Thank you 

> ubuntu@ubuntu:~$ lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 8.04.1 \n \l

ubuntu@ubuntu:~$ apt-cache policy util-linux
util-linux:
  Installed: 2.13.1-5ubuntu2
  Candidate: 2.13.1-5ubuntu2
  Version table:
 *** 2.13.1-5ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.13.1-5ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
ubuntu@ubuntu:~$ sudo swapon -s
Filename				Type		Size	Used	Priority

---

### Post by caljohnsmith on 2009-01-25
> **Shrimply said:**
> ```
ubuntu@ubuntu:~$ sudo mkswap -U 885684e5-72d4-4[COLOR="Red"]l[/COLOR]ca-a975-caaf537def39 /dev/sda6
```
I think I see the problem; you have a lowercase "L" in the UUID above, when it should be a one or "1". Can you copy/paste the commands I give, or do you have to enter them in by hand? If you have to do it by hand, please redo that command with a "1" in the UUID instead of an "l", and then post the new output of:
```
sudo blkid -c /dev/null
```

---

### Post by Shrimply on 2009-01-25
Sorry yeah, I've been doing it by hand as I have no internet access to the internet using the live cd.

But I think its worked
> /dev/sda1: UUID="B89CCD9A9CCD5392" TYPE="ntfs" 
/dev/sda2: UUID="14A631021624A6BB" TYPE="ntfs" 
/dev/sda5: UUID="757b8e44-cdd3-4e5c-877d-362d9521a4ea" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="885684e5-72d4-41ca-a975-caaf537def39" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="ubuntu8" UUID="48B9-64F3" TYPE="vfat" 
/dev/sdb2: UUID="b84b6bb6-e469-4071-8ad9-01194e8282d9" TYPE="ext2" 
/dev/loop0: TYPE="squashfs"

---

### Post by caljohnsmith on 2009-01-25
Great, it looks like that finally worked, so how about trying to boot into your Ubuntu install again and see if you can open a terminal. If you can, please post:
```
sudo swapon -s
free
```

---

### Post by Shrimply on 2009-01-25
Yes its working great thanks

> darren@darren-desktop:~$ sudo swapon -s
[sudo] password for darren: 
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	305192	72592	-1
darren@darren-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        254596     248692       5904          0       2976      61512
-/+ buffers/cache:     184204      70392
Swap:       305192      72592     232600
darren@darren-desktop:

---

### Post by caljohnsmith on 2009-01-25
So is your Ubuntu working faster than a crawl now that your swap is back? If so, cheers and have fun with Ubuntu. :)

---

### Post by Shrimply on 2009-01-25
Yes thank you so much, I really wasn't looking forward to reinstalling so I really am very grateful.

---

### Post by Loki1989 on 2009-01-25
> **Rim said:**
> <.< with swap u should stick with 1/2 of ur total ram installed always..

actually you should have a swap of at least one and a half times the amount of your installed ram. Winblows and Ubuntu both do it that way by default.

---

### Post by boof1988 on 2009-01-25
> **Loki1989 said:**
> actually you should have a swap of at least one and a half times the amount of your installed ram. Winblows and Ubuntu both do it that way by default.

I don't think this is correct (for Ubuntu).  Is there a source for this info?

---

### Post by Loki1989 on 2009-01-26
> **boof1988 said:**
> I don't think this is correct (for Ubuntu).  Is there a source for this info?

I do not have one but I do remember it from my computer science class I just did my fresh install using Ubuntu 8.10 and it made a swap one and a half time the size of my ram.

---

### Post by -kg- on 2009-01-26
I don't think the size of the swap partition matters in the positive direction.  You just need to have *at least* a certain amount.

Since Shrimply increased his swap size, that alone shouldn't have affected it.  The problem was that the UUID changed and it caused an access problem until he corrected it.

I have heard many different theories as to minimum swap partition size.  Some say the same amount as RAM; some say 1 1/2 X RAM; some say 2 X.  One could experiment with their system, I suppose, but the theory I personally adhere to is *at least* the same amount as RAM, and maybe just a little more.

The Swap partition is used when the RAM is at or near 100% usage and the software requires more to be loaded to RAM.  Since this is not possible, certain (presently) unused data is written from RAM to the swap partition for storage so that data that is needed more immediately can be loaded and processed.  Once that data is processed, it is either written to the disk, or swapped with the earlier data in the swap partition so that that data can be processed.

Usually, the amount of data written in a swap is significantly less than the total amount of RAM you have.  However, there might be software that would swap nearly all of the contents of RAM to swap back and forth.  In these circumstances, you might want to have your swap file to be 2 X the amount of RAM that you have installed.

Anyway, it is desirable to have a good size swap...as much as you can afford depending on the space available.  Of course, you can have over-kill, wasting space that you could be using for software and data unnecessarily, but that won't affect the operation of the system.  Too little certainly can.

You might be able to get away with using a swap partition at 1/2 the size of RAM (if you use low profile software that doesn't take much RAM to use), but personally I would use "at least" the same size of swap partition as RAM, since this usually will give you the least problems with almost any software you're likely to run.  Of course, this presupposes that you aren't experiencing limited disk space...in that case one would have to experiment with the minimum swap size that one could get away with and still have sufficient space for the rest of the installation.

BTW, I use 2 X RAM on my system, but I anticipate using Linux in editing and processing video files, which is a memory and disk intensive process.

---

### Post by -kg- on 2009-01-26
> **boof1988 said:**
> I don't think this is correct (for Ubuntu).  Is there a source for this info?

OK, I found the documentation.  From [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq"):

> How much swap do I need?

    * If you have n MB of RAM, you need between n and 2*n MB of swap.
    * If you have a disk big enough, just put 2*n MB swap. 

This confirms what I have heard, and confirms Loki1989's statement and experiences.

Actually, this page contained a little information that I didn't know before:

> Should I reinstall with more swap?

    * Definitely no.
    *

      With the 2.6 kernel, "a swap file is just as fast as a swap partition." 

How do I add more swap?

    * Usually, people associate swap with a swap partition, maybe because they've been proposed to create a swap partition on install. In fact any file can be used as a swapping device, be it a partition or a conventional file.

It goes on to show how to set such a file up.  Of course, this won't change your hard drive requirements, since according to the instructions, the file is set up at a static size (unlike Windows, which will set up a "paging file" as a dynamic file), but this is interesting none-the-less.

I think, though, that I will stick with a conventional swap partition.  If I'm not mistaken, such a partition can be shared between different installations.

---

### Post by kestrel1 on 2009-01-26
You are correct in your assumption that a swap partition can be used by different installs.
I have a multi-boot (Ubuntu, Mint, Mandriva & Opensuse) & I am only using a single swap partition, that is shared between them.

---

### Post by boof1988 on 2009-01-26
> **Loki1989 said:**
> I do not have one but I do remember it from my computer science class I just did my fresh install using Ubuntu 8.10 and it made a swap one and a half time the size of my ram.

My apologies... I should have been more clear.  I was only (trying) to say the the Ubuntu 8.10 does not (when the installer chooses partition sizes) automatically set swap to be 1-1/2 times installed RAM.  That's all I was trying to say.

I believe you when you tell me that your install of Ubuntu 8.10 (automatically) allocated 1-1/2 times *your* RAM...  but... Ubuntu 8.10 does not by default make every install 1-1/2 times the installed RAM on the machine.

-kg- is probably right in that the install will use a certain amount needed for the install.  Also -kg-'s link indicates 2 times RAM which is not 1-1/2.

I'm not trying to argue about a bunch of different things... The only thing I'm am saying is the the Ubuntu 8.10 Desktop Installer does not have a default (when the installer decides partition sizes) swap partition value of 1-1/2 time installed RAM.

EDIT:
I just installed Ubuntu 8.10 on a virtual machine (twice) and attached screenshot showing "free -m" and the installer chose the same swap size (~1/2 G) for both 1G RAM and 1/2 G RAM...  Take a look...

---

### Post by -kg- on 2009-01-27
> Also -kg-'s link indicates 2 times RAM which is not 1-1/2.

Sorry, but -kg-'s link says:

> If you have **"n"** (a variable, as in 1000) MB of RAM, you need between **"n and 2*n"** (again, the variable, as in 1000 and 2 X 1000) MB of swap.

Which puts his quote of 1 1/2 X RAM right in the middle of the range.

> I'm not trying to argue about a bunch of different things... The only thing I'm am saying is the the Ubuntu 8.10 Desktop Installer does not have a default (when the installer decides partition sizes) swap partition value of 1-1/2 time installed RAM.

That, and the further statement in the edit I can't argue with.  What I stated is just from the quoted Ubuntu Community Documentation page.  And frankly, I agree with it, considering what swap is used for.

I did say that you could probably get away with less...it just depends on what type of software you plan on using and how memory intensive it is.  You would have to experiment with your particular system to see how little you can get away with.  But the more, the better, if you can afford it.

---


---
title: "Mysterious booting problem"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by llmunro on 2011-03-27
Hi everyone!

I have a mysterious problem with my Ubuntu 10.10 installation on my aging desktop computer.  I turned the computer on today and got to the GRUB menu and then...

I get a whole bunch of code and a message that says, "Target filesystem doesn't have requested /sbin/init. No init found. Try passing init=bootarg.

Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built in commands.

And a whole bunch of code and a flashing cursor.

I've tried rebooting several times and booting into older kernels and still no dice.  I was messing around with the BIOS yesterday to test out a live CD on a USB drive, but the computer booted fine after that, so I'm stumped.

Any ideas? Advice? Thoughts?

Many thanks.  

Best,
Lisa

---

### Post by Rubi1200 on 2011-03-27
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by llmunro on 2011-03-27
Hi,

I am running the boot info script in the terminal, although its been running for a very long time now.  It appears to be stuck on:
  
```
Searching sda5 for information...
```

I'll let you know if it produces a text file.

Thanks much for the help.

Best,
Lisa

---

### Post by Dutch70 on 2011-03-27
Do you mean you've downloaded the boot info script **to your desktop**

and you ran the command he gave you in a terminal???

Oh.. Congrats on your(Arizona) win over Duke btw. :D

---

### Post by llmunro on 2011-03-27
Yes, I put the little bootscript on the desktop of the live CD that I'm running.  It seemed to be working but now looks stuck, as its been running for well over an hour. :(

The Arizona win over Duke was indeed amazing.  Much celebration was had until last night's loss! :P

Best,
Lisa

---

### Post by Dutch70 on 2011-03-27
> **llmunro said:**
> Yes, I put the little bootscript on the desktop of the live CD that I'm running.  It seemed to be working but now looks stuck, as its been running for well over an hour. :(

The Arizona win over Duke was indeed amazing.  Much celebration was had until last night's loss! :P

Best,
Lisa


Something is wrong, it should only take a few seconds to do that.
You may want to try downloading the boot info script again.

Well, sorry I hadn't heard about that yet. Been reading about Kentucky & UNC all day. :)
Huge rivals & they play this evening.

---

### Post by Rubi1200 on 2011-03-27
Okay, still on the LiveCD, do this:

```
sudo fdisk -lu
```

post the output

```
sudo lsof | grep sda5
```

ditto

---

### Post by llmunro on 2011-03-27
Hi!

Here goes:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    21053439    10485760    7  HPFS/NTFS
/dev/sda3   *    21053440   164560895    71753728    7  HPFS/NTFS
/dev/sda4       205037719   312496379    53729330+   5  Extended
/dev/sda5       205037721   280440831    37701555+  83  Linux
/dev/sda6       309476223   312496379     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097991

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773119   488385536    b  W95 FAT32
ubuntu@ubuntu:~$ \

```


and

```
ubuntu@ubuntu:~$ \sudo lsof | grep sda5
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda5  483       root  cwd       DIR       0,17      280          2 /
jbd2/sda5  483       root  rtd       DIR       0,17      280          2 /
jbd2/sda5  483       root  txt   unknown                                /proc/483/exe



```



I don't really understand any of this, so I await further instructions or thoughts.

Thanks to all! :)

Best,
Lisa

---

### Post by llmunro on 2011-03-27
Also, I tried downloading the boot info script again, putting it on the desktop, and running it in the terminal.  It zooms through searching for info on sda1, sda2, etc., but then gets stuck again at sda5.

Thanks again for the help.

Best,
Lisa

---

### Post by deconstrained on 2011-03-27
The error message you got may indicate that the kernel was unable to mount your root filesystem.

The first thing I'd try is booting to a livedisk and running fsck on sda5, mounting it (at /mnt for example) and checking /etc/fstab in it (/mnt/etc/fstab). If it doesn't work then there might be something wrong with the partition. 

From there I'd chroot, rebuild the initramfs and run update-grub.

---

### Post by llmunro on 2011-03-27
Hi deconstrained,

Thanks for the response and the help! 

I'm afraid that you'll have to break down your suggestions into some slightly simpler steps, as I'm still pretty new at Ubuntu! :)

So, I'm running the live cd right now.  How might I:

1. run fsck on sda5
2. mount it
3. check /etc/fstab

Thanks much.

Best,
Lisa

---

### Post by Rubi1200 on 2011-03-27
Try running this command:

```
sudo kill 483 /dev/sda5
```

Then try running the boot script again.

---

### Post by oldfred on 2011-03-27
If boot script cannot mount it, it says it has problems. I also would try fsck first.

From liveCD so everything is unmounted,swap off if necessary, change sda5 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

---

### Post by llmunro on 2011-03-27
Hi Oldfred,

I'm not quite sure what you mean by change sda5 to my partition(s)?

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

```Perhaps I have done this wrong.

Thanks to all for the help and ideas.

Best,
Lisa

---

### Post by llmunro on 2011-03-27
P.S.  I have also tried:

```
sudo kill 483 /dev/sda5
```

and running the boot script again.  Still encountering the same problem with it getting stuck at sda5.

Thanks for the help.

Best,
Lisa

---

### Post by Dutch70 on 2011-03-27
I think when you tried oldfred's suggestion, you need to first open gparted, right click your swap partition & select "swapoff"  
Then try running his suggested commands again.

---

### Post by oldfred on 2011-03-27
My instructions were meant to be generic. Since sda5 is your partition then the example I gave was correct.

Try Dutch70's suggestion on swap off.

I have seen several users with issues of not being able to get partition unmounted. Maybe they just did not swap off and Slitaz does not mount swap by default.

Problem running e3fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz & Slitaz does not use sudo but su.

---

### Post by llmunro on 2011-03-27
Hi Oldfred,

I turned the swap off in Gparted and it looks to me like there's nothing mounted.

But, still...


```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```So, the next step is to use Slitaz?

Thanks much.

Best,
Lisa

P.S. Would it be easier at this point to try reinstalling Ubuntu?

---

### Post by oldfred on 2011-03-27
If you have nothing that is not backed up, reinstall is an alternative.

Do you know why you are getting a file error? Did you shutdown abnormally or is disk starting to fail. In System, Admin, Disk Utility you can click on drive in left panel an it will show Smart Status if your drive supports it.

Many have made lots of configuration changes or added a lot of programs that then is some work to redo. Then repair makes more sense.

You can usually reinstall in about an hour if you have good backups.

Slitaz is a smaller distribution so it is relatively easy to download and create a liveCD.

---

### Post by Onyx1 on 2011-03-27
> **Rubi1200 said:**
> Okay, still on the LiveCD, do this:

```
sudo fdisk -lu
```post the output

```
sudo lsof | grep sda5
```ditto

Hi everyone I am having the same problems. I've already loaded from a live usb and i am ran the first boot script code and I am getting stuck on sda5 too. I did what is quoted and here is my output 
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xca094a65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   264690200   132344076+   7  HPFS/NTFS
/dev/sda2       456896512   488353791    15728640   1b  Hidden W95 FAT32
/dev/sda3       488353792   488397167       21688   ef  EFI (FAT-12/16/32)
/dev/sda4       264691710   456896511    96102401    5  Extended
/dev/sda5       264691712   450754559    93031424   83  Linux
/dev/sda6       450756608   456896511     3069952   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16     7813119     3906552    b  W95 FAT32
```

here is my output for the second quoted command.
```
ubuntu@ubuntu:~$ udo lsof | grep sda5
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
You will have to enable the component called 'universe'

```


What should I do now?

---

### Post by Onyx1 on 2011-03-28
> **oldfred said:**
> If you have nothing that is not backed up, reinstall is an alternative.

Do you know why you are getting a file error? Did you shutdown abnormally or is disk starting to fail. In System, Admin, Disk Utility you can click on drive in left panel an it will show Smart Status if your drive supports it.

Many have made lots of configuration changes or added a lot of programs that then is some work to redo. Then repair makes more sense.

You can usually reinstall in about an hour if you have good backups.

Slitaz is a smaller distribution so it is relatively easy to download and create a liveCD.

On mine, mine shutdown by the battery dying if that helps.

---

### Post by Dutch70 on 2011-03-28
Onyx1, please start your own thread. If you want help, read this first.
[[COLOR="Red"]How to get your support questions answered quickly[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by deconstrained on 2011-03-28
> **llmunro said:**
> So, I'm running the live cd right now.  How might I:

1. run fsck on sda5
2. mount it
3. check /etc/fstab
Well it seems you've got something running that is keeping the disk busy...So find out what it is:
```
root@ubuntu# fuser -vam /dev/sda5
root@ubuntu# lsof /dev/sda5
```
Then once you've identified and terminated the process*:
```
root@ubuntu:~# fsck /dev/sda5
root@ubuntu:~# mount /dev/sda5 /mnt # (for example)
```
If mounted to /mnt, the fstab file (see "man fstab" or [here](http://en.wikipedia.org/wiki/Fstab) for more detail on this file and its role in your system) would be at /mnt/etc/fstab [b](note: this is assuming that sda5 is your root partition. This hasn't been established yet. If in doubt, use the "blkid" command, or "fdisk -l" (as root) to help you identify partitions.

* Terminate with "kill *[pid]*" or "kill -9 *[pid]*" if it's not behaving, where *[pid]* is the process ID number listed in the output of the "fuser" command.

---

### Post by llmunro on 2011-03-28
Hi everyone!

I was going to just reinstall Ubuntu, which doesn't take me that long generally and I have the vast majority of my files backed up.  I've been trying to reinstall from the Live CD and find that I can't get the install to advance past the screen where it advises to have 2.6 GB of disk space and an internet connection, etc.  I can only assume that this is a Very Bad Sign. So, I'm going to attempt to try to keep recovering my installation that seems to be messed up at the moment, although I think I might be in over my head.

I don't think that the disk is failing.  I checked it with the Disk Utility and from what I can tell its okay.  I don't remember shutting down abnormally before this problem started, so I'm stumped.

Most recently, I did this:

```
ubuntu@ubuntu:~$ fuser -vam /dev/sda5
Cannot stat file /proc/4386/fd/40: Stale NFS file handle
                     USER        PID ACCESS COMMAND
/dev/sda5:
ubuntu@ubuntu:~$ lsof /dev/sda5
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
ubuntu@ubuntu:~$ 
```


I do not see a process ID number to stop whatever is hanging up my sda5.  I still can't run fsck, as I keep getting messages that sda5 is busy.

I don't quite know what to do at this point.  Is my Ubuntu beyond recovery?

Thanks to all.

Best,
Lisa

---

### Post by oldfred on 2011-03-28
Were you using NFS?

This says you have to remount it in NFS.
[http://www.phppop.net/d/node/162](http://www.phppop.net/d/node/162)

I now think the Slitaz does not recognize the NFS and then e2fsck works for those who have had similar issues.

---

### Post by Rubi1200 on 2011-03-29
You could try downloading and burning to CD a distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

I have had success using Slax to run fsck and the boot script when other options failed.

---


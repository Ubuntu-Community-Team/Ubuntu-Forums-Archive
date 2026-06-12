---
title: "Sharing a NTFS partition between two linux boxes through NFS?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by odiseo77 on 2007-10-30
Hi folks. I'm trying to connect two Ubuntu machines so that machine 1 can access a FAT32 partition on machine 2, and machine 2 can access a NTFS partition on machine 1. To explain myself better, let's say machine 1 is my own machine, located in my bedroom, and machine 2 is my mother's machine, located in the living room. I store my personal data on my machine, in a NTFS partition and machine 2 stores personal data on a FAT32 partition. I followed [this guide]("http://easylinux.info/wiki/Ubuntu:Gutsy#NFS_Server") in order to set up a NFS server and client on both machines (so that both have access to each other). The point is, after following the procedure in the guide, I can access my mother's machine from mine, but I can't access my own machine (machine 1) from my mother's PC. I'm not sure why, but my guess is that this is due to the fact that the partition on machine 1 I want to share is in NTFS format? I say this because, when following the  procedure in the guide, I get these messages on machine 1 when running the following commands:

> sudo /etc/init.d/nfs-kernel-server restart
[sudo] password for userxxx:
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1:/media/sda5".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x
exportfs: **Warning: /media/sda5 does not support NFS export.**
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 
vicente@ubuntu-box:~$ sudo exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1:/media/sda5".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x
exportfs: **Warning: /media/sda5 does not support NFS export.**

(/media/sda5 is the moint point for my NTFS partition).

Instead, when running the previous commands on my mother's machine, I didn't get this "**Warning: /media/sdxn does not support NFS export.**" message.

So, how to share/export this NTFS partition? Any ideas about what could be wrong and how to solve it?

Thanks in advance for your answers.

---

### Post by Lambert on 2007-10-30
I can't directly help you as I don't have a windows machine, ubuntu 7.10 now has ntfs-3g integrated. Do a search for that term and you should find more info. 

Some of it is old and the howtos include installing on older versions of ubuntu. It is installed by default on gutsy 7.10 if you're using that version then you  just need to configure it.

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by szaka on 2007-10-31
The Ubuntu kernel unfortunately doesn't support NFS exports of FUSE based file systems. You may submit an Ubuntu kernel bug report. Till fixed, you can find the solution here: [http://ntfs-3g.org/support.html#nfs](http://ntfs-3g.org/support.html#nfs)

---

### Post by odiseo77 on 2007-10-31
Hi people, thanks a lot for your answers and interest. I'll submit an Ubuntu kernel bug at launchpad as soon as possible.

Thank you again :)

---

### Post by odiseo77 on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/159004](https://bugs.launchpad.net/ubuntu/+bug/159004) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Sorry for double post; this is just to let you know that I already reported the bug:

[https://bugs.launchpad.net/ubuntu/+bug/159004](https://bugs.launchpad.net/ubuntu/+bug/159004)

I'll report back about the notifications/advances I receive.

Regards.

---

### Post by Jive Turkey on 2008-01-12
So it looks to me like the problem is with FUSE, and can be worked around by compiling FUSE kernel module ones' self but not if the it's compiled with the OS kernel,  I don't know if it is or not, and I'm not sure how to tell if it is or not.

Is there some other way to mount a partition besides FUSE that will allow it to be exported?

FUSE README.NFS> 
FUSE module in official kernels (>= 2.6.14) don't support NFS
exporting.  In this case if you need NFS exporting capability, use the
'--enable-kernel-module' configure option to compile the module from
this package.  And make sure, that the FUSE is not compiled into the
kernel (CONFIG_FUSE_FS must be 'm' or 'n').

You need to add an fsid=NNN option to /etc/exports to make exporting a
FUSE directory work.

You may get ESTALE (Stale NFS file handle) errors with this.  This is
because the current FUSE kernel API and the userspace library cannot
handle a situation where the kernel forgets about an inode which is
still referenced by the remote NFS client.  This problem will be
addressed in a later version.

In the future it planned that NFS exporting will be done solely in
userspace.

---

### Post by 655 on 2008-01-31
This is still an unsolved bug, right? :(

---

### Post by user1234 on 2008-05-23
> **655 said:**
> This is still an unsolved bug, right? :(
Aparently... sucks... I was counting on pluging my USB drive into my home server and exporting it to my laptops... no go.. :-(  Hope they fix soon.

So, did I miss something, it was a kernel option not enabled?

---

### Post by odiseo77 on 2008-05-23
> **user1234 said:**
> Aparently... sucks... I was counting on pluging my USB drive into my home server and exporting it to my laptops... no go.. :-(  Hope they fix soon.

So, did I miss something, it was a kernel option not enabled?

Have you tried it on Hardy's kernel? I didn't receive an answer at launchpad, but maybe they fixed it? (I haven't tried again because I bought an external HDD to back up my data and share it when I need to).

Other solution I see is to compile the kernel module as szaka suggests, but I don't know how safe and tricky this would be.

---

### Post by 655 on 2008-05-24
Yeah, still not working in a clean install of Hardy.

---

### Post by zarpa37 on 2008-05-24
There is a work arround using nfs-user-server instead of nfs-kernel-server.

You could find an explanation in spanish at:
[http://ubuntubenidorm.blogspot.com/2008/02/compartir-archivos-entre-equipos-linux.html](http://ubuntubenidorm.blogspot.com/2008/02/compartir-archivos-entre-equipos-linux.html)

It has worked for me.

---

### Post by Vladimir Hidalgo on 2008-06-02
I did a little guide to solve this problem in Feisty (I guess it work for Hardy too), it's in Spanish, but most can be understood even if you don't know the language.

[http://www.svcommunity.org/forum/ind...?topic=55193.0](http://www.svcommunity.org/forum/ind...?topic=55193.0)

Vlad.

P.S. it does not need to use nfs-user-server.

---

### Post by 655 on 2008-06-03
The link did not work for me.

---

### Post by Vladimir Hidalgo on 2008-06-03
Yes, sorry, here's again:
[http://www.svcommunity.org/forum/index.php?topic=55193.0](http://www.svcommunity.org/forum/index.php?topic=55193.0)

---

### Post by 655 on 2008-06-04
Interesting guide, thank you.  

I attempted to follow it, but failed at the step where we must stop the FUSE module.
Issuing the command rmmod fuse command results in:

```
ERROR: Module fuse is in use
```

I did a umount -a prior to this to stop any devices that might be using FUSE, btw.
What could be using FUSE and how do I stop it?

Thanks!

---

### Post by Vladimir Hidalgo on 2008-06-05
655, after you do 'umount -a' (btw, I did use 'fusermount -u /media/...') you must do 'sudo /etc/init.d/fuse stop' prior 'sudo rmmod fuse' otherwise you will get that error.

---

### Post by 655 on 2008-06-05
Vladimir:

Sorry, I neglected to mention that I did try to stop fuse before performing the rmmod command.
The thing is, fuse-utils *isn't even installed*...  that is why I did umount -a rather than fusermount.

Which is what puzzles me.  When I run sudo /etc/init.d/fuse stop, it says the command was not found.  Naturally, because fuse is supposedly not installed.

Yet, rmmod fuse returns the error from above about it being in use.

```
me@desktop:~$ fusermount -u /media/disk2
The program 'fusermount' is currently not installed.  You can install it by typing:
sudo apt-get install fuse-utils
bash: fusermount: command not found
me@desktop:~$ sudo umount -a
umount: /home: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
me@desktop:~$ sudo /etc/init.d/fuse stop
sudo: /etc/init.d/fuse: command not found
me@desktop:~$ find /etc/init.d/fuse
**find: /etc/init.d/fuse: No such file or directory**
me@desktop:~$ sudo rmmod fuse
**ERROR: Module fuse is in use**
```Should I disregard that last bit as erroneous?  Or, what is going on here?

Thanks.

---

### Post by Vladimir Hidalgo on 2008-06-05
Please install fuse-utils and try again with fusermount -u.

If it does not work, just continue installing the new FUSE and ntfs-3g but be sure to umount ntfs partitions first, I don't want to take any risk about your data.

Edit:

btw, I looked into /init.d/fuse to see what "stop" does, and found:

> MOUNTPOINT=/sys/fs/fuse/connections
....
    stop)
        if ! grep -qw fuse /proc/filesystems; then
                echo "Fuse filesystem not loaded."
                exit 7
        fi
        if grep -qw $MOUNTPOINT /proc/mounts; then
                echo -n "Unmounting fuse control filesystem"
                if ! umount $MOUNTPOINT >/dev/null 2>&1; then
                        echo " failed!"
                else
                        echo "."
                fi

So, try '*grep  /sys/fs/fuse/connections /proc/mounts*' and if you got a line like this: "fusectl /sys/fs/fuse/connections fusectl rw 0 0" then you instead of installing fuse-utils do: '*sudo umount /sys/fs/fuse/connections*'

It has to stop any FUSE thing in your system, so you after it you can do 'rmmod fuse'.

---

### Post by 655 on 2008-06-09
Thanks for the update.

I didn't see your edit at first, and I still was unable to stop FUSE at the time, so I tried the other workaround involving using nfs-user-server instead of nfs-kernel-server.  

nfs-user-server apparently doesn't install the current nfs-common package, which is where the bug lies, if I recall correctly.

So, for the time being that workaround did the trick, although I am curious about trying your (albeit longer) solution.  The thing is, I am slowly replacing the contents of these NTFS drives and formatting them with ext3, so the issue will eventually be moot.  ATM I'm sitting on my haunches with the current fix.

Thank you for walking me through all of the troubleshooting, though.  I hope these steps can serve future comers.

---

### Post by Vladimir Hidalgo on 2008-06-17
Hey don't worry :)

By the way, I had upgraded to Hardy, the fastest way I found was to compile the new ntfs-3g driver (1.2531 ATM).

It does not have dependence on FUSE package anymore (because now it's included a FUSE-Lite version in NTFS-3g :)

NFS does not complain after it and you got a even better driver ;)

By the way, changing from NTFS to Ext3/ReiserFS/Anything else is a good move -and the best solution IMHO- but for the moment I'll stay with NTFS until I found another disk to move my 250GB of data LOL.

Oh! about the nfs-user-server, I did not wanted to use because of this:
[http://linux.about.com/cs/linux101/g/nfsuserserver.htm](http://linux.about.com/cs/linux101/g/nfsuserserver.htm)

I just hope you won't get into troubles :)

---

### Post by 655 on 2008-06-25
Well, I juggled my data around and reformatted everything to ext3, so, problem "solved."  Good-bye NTFS...:-\"

Thanks for everything Vladimir.

---

### Post by robb0100 on 2008-07-07
> **Vladimir Hidalgo said:**
> 

By the way, I had upgraded to Hardy, the fastest way I found was to compile the new ntfs-3g driver (1.2531 ATM).

It does not have dependence on FUSE package anymore (because now it's included a FUSE-Lite version in NTFS-3g :)

NFS does not complain after it and you got a even better driver ;)



Vladimir
Thanks for the info.
I tried to use this in Hardy(64 bit) but after installing Vers 1.2531 and running
exportfs -ra
it still reported
exportfs :Warning : /media/NTFSdrive does not support NFS export.

Does the exports file require some reference to NTFS or NTFS-3g or is there something else I am missing?
Pls be patient I am a bit of a noob.

---


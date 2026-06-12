---
title: "Internet Does Not Work Ubuntu 10.04.2 LTS"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by deckerry on 2011-03-26
I just went through an 11 page thread trying to get Ubuntu installed on my computer. Now I can't get the internet to work. The internet worked easy while booting from a usb, but now that I can boot without any external device I am having trouble.

I tried enabling drivers with the hardware driver application, which worked on the usb, but it's trying to connect to the internet to get the drivers or something. Ironic huh?

Should I just download the drivers from another computer and put them in using an external memory device?

Can somebody help me?

---

### Post by samcot on 2011-03-27
Are you using ethernet or wireless? Have you right-clicked on your network icon on the upper system tray to take a look? And then there is the terminal command *ifconfig*.

---

### Post by Hedgehog1 on 2011-03-27
Here is the image of the error and the hardware:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187227&d=1301194807[/IMG]

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-27
This is wireless.

---

### Post by samcot on 2011-03-27
Hedgehog, I'm absolutely amazed! How did you know what kind of error deckerry is getting?
 
:o

---

### Post by Hedgehog1 on 2011-03-27
He posted the image in the other thread, before I asked him to make a new one because I don't know network in Ubuntu very well.

***The 'amazing' Hedge***

:KS

---

### Post by samcot on 2011-03-27
Okay, wireless. But are you getting the error that Hedgehog posted? 
 
Anyway, it may be a driver issue as you first suspected, but what do you see when you open up the network icon and use the ifconfig command in terminal?

---

### Post by samcot on 2011-03-27
*The 'amazing' Hedge.*
 
Well, even if you're not psychic I still think you're pretty amazing. Does this mean he'll have to get a proprietary driver?

---

### Post by deckerry on 2011-03-27
Samcot, I'll be right on that but first I must say one thing to Hedgehog1.
 
Dear Hedgehog1,
You'll never believe this but I can't get into ubuntu anymore without the usb drive. I get this error message:
 
```

[FONT=Calibri][SIZE=3]Gave up waiting for root device. Common problems:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Boot args (cat /proc/cmdline)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Check rootdelay= (did the system wait long enough?)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Check root= (did the system wait for the reight device?)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Missing modules (cat /proc/modules; ls /dev)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Alert! /dev/disk/by-uuid/f264b1c4-9dbc-4b50-84f0-f8dad7719ecd does not exist. Dropping to a shell![/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Enter ‘help’ for a list of built-in commands.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3](initframs) _[/SIZE][/FONT]

```

---

### Post by Dutch70 on 2011-03-27
Boot up the usb drive and post the output of...
```
sudo gedit /etc/fstab
```

Actually that will open a window. Paste the contents into your next post.

---

### Post by samcot on 2011-03-27
deckerry, if you have that driver issue, then I wouldn't bother with what I was saying. But anyway, now you've got bigger fish to fry. Good luck!

---

### Post by fabricator4 on 2011-03-27
> **Hedgehog1 said:**
> Here is the image of the error and the hardware:


That file is already on the LiveUSB.  If he goes to /pool/main/p/patch the file is right there. 

Since the system knows what file it is looking for, maybe if he copies that file to the file system on the boot partition, specifically into /var/cache/apt/archives, then the system may just use it instead of trying to download it.

There's an option to add the LiveCD to the repository, but I don't know if there's something similar for the LiveUSB.

Seems like the OP has other problems at the moment in any case...

Chris

---

### Post by Hedgehog1 on 2011-03-27
> **deckerry said:**
> Samcot, I'll be right on that but first I must say one thing to Hedgehog1.
 
Dear Hedgehog1,
You'll never believe this but I can't get into ubuntu anymore without the usb drive. I get this error message:
 
```

[FONT=Calibri][SIZE=3]Gave up waiting for root device. Common problems:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Boot args (cat /proc/cmdline)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Check rootdelay= (did the system wait long enough?)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]-Check root= (did the system wait for the reight device?)[/SIZE][/FONT]

```

Sadly, I do believe it...

***Murphy's law is alive and well in Wisconsin!***.  I think that because the LiveUSB was coming up as /dev/sda, the install wasn't expecting that and it caused this to happen.

If the liveUSB is still coming up as /dev/sda, please do these commands from the LiveUSB:

Please boot off your LiveCD/LiveUSB, select 'TRY'

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**b5** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**b**
```



***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-27
> **fabricator4 said:**
> That file is already on the LiveUSB.  If he goes to /pool/main/p/patch the file is right there. 

Since the system knows what file it is looking for, maybe if he copies that file to the file system on the boot partition, specifically into /var/cache/apt/archives, then the system may just use it instead of trying to download it.

There's an option to add the LiveCD to the repository, but I don't know if there's something similar for the LiveUSB.

Chris

Thanks Chris!

deckerry, here is what Chris is talking about:

[IMG]http://img21.imageshack.us/img21/7484/loadfromcd.png[/IMG]

The snag is: Your CD drive is busted.

***The Hedge***

:KS

**p.s. Is it possible to temporarily connect to the network using a cable, so you can get all your drivers updated?  Then you can go back to wireless...**

---

### Post by fabricator4 on 2011-03-27
> **Hedgehog1 said:**
> 
The snag is: Your CD drive is busted.


Just a quick reality check...  was the original screen you posted (where it was looking for the .deb file) from deckerry's machine?

If so, the system is trying to download the patch directly - ie it already knows what file it wants to download.

Therefore, if it finds the .deb already in the right directory will (fingers crossed) probably just use it instead of trying to download it "again".

Deckerry, open a terminal window (after booting off the hard drive and inserting the usb) and try the following:

```

sudo cp /media/volume_name/pool/main/p/patch /var/cache/apt/archives/

```

You'll have to change "volume_name" to the actual volume name of the USB.  If you don't know what this is, in the terminal window type:

```

ls /media

```

and it should be printed on the screen.  If the volume name is a huge string of digits you can use the autocomplete feature in bash instead of typing the whole thing: when you get to the volume name in the above command line type the first few characters and then press the tab key.  Bash will insert the rest of the volume name for you.

Chris.

---

### Post by deckerry on 2011-03-27
> **samcot said:**
> Okay, wireless. But are you getting the error that Hedgehog posted? 
 
Anyway, it may be a driver issue as you first suspected, but what do you see when you open up the network icon and use the ifconfig command in terminal?
yes images from post #3 are from my screen after booting from the hard drive, which I can't do anymore with out the error from post #9. Here's the output from ifconfig:
 
```

ifconfig
eth0 Link encap:Ethernet HWaddr 00:1b:24:b7:3c:fe 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:27 Base address:0x4000 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)
ubuntu@ubuntu:~$ 

```

---

### Post by deckerry on 2011-03-27
> **Dutch70 said:**
> Boot up the usb drive and post the output of...
```
sudo gedit /etc/fstab
```
 
Actually that will open a window. Paste the contents into your next post.
 
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb6 swap swap defaults 0 0

```

---

### Post by deckerry on 2011-03-27
> **fabricator4 said:**
> That file is already on the LiveUSB.  If he goes to /pool/main/p/patch the file is right there. 

Since the system knows what file it is looking for, maybe if he copies that file to the file system on the boot partition, specifically into /var/cache/apt/archives, then the system may just use it instead of trying to download it.

There's an option to add the LiveCD to the repository, but I don't know if there's something similar for the LiveUSB.

Seems like the OP has other problems at the moment in any case...

Chris
While booting from the usb, 
I found [COLOR=red]/var/cache/apt/[/COLOR]archives but
I don't know how to find [COLOR=red]/pool/main/p/patch.[/COLOR]

---

### Post by deckerry on 2011-03-27
> **Hedgehog1 said:**
> Sadly, I do believe it...
 
***Murphy's law is alive and well in Wisconsin!***. I think that because the LiveUSB was coming up as /dev/sda, the install wasn't expecting that and it caused this to happen.
 
If the liveUSB is still coming up as /dev/sda, please do these commands from the LiveUSB:
 
Please boot off your LiveCD/LiveUSB, select 'TRY'
 
In the Terminal (Menu to: Applications >> Accessories >> Terminal):
 
```
sudo mount /dev/sd**b5** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**b**
```
 
 
 
***The Hedge***
 
:KS
How do I know if the liveUSB is still coming up as /dev/sda?
I did the commands anyway and it said this:
 
```
Installation finished. No error reported.
```
 
Then I restarted and tried booting to Ubuntu and got the same error message from post #9.

---

### Post by deckerry on 2011-03-27
> **Hedgehog1 said:**
> Thanks Chris!

deckerry, here is what Chris is talking about:

[IMG]http://img21.imageshack.us/img21/7484/loadfromcd.png[/IMG]

The snag is: Your CD drive is busted.

***The Hedge***

:KS

**p.s. Is it possible to temporarily connect to the network using a cable, so you can get all your drivers updated?  Then you can go back to wireless...**
I cannot plugin to get internet through ethernet 'cause i'm in an apartment and the landlord has the router locked in a closet somewhere.
 
I might be able to download the drivers in Vista, save them to an external drive, boot into Ubuntu and put them in that way. But I can only get into Ubuntu thrrough usb.

---

### Post by Hedgehog1 on 2011-03-27
That fstab file is the one for the LiveUSB, sadly.

Please do this to get to the fstab (**F**ile **S**ystem **TAB**le) on the install:

```
sudo mount /dev/sdb5 /mnt
```

```
gksudo gedit /mnt/etc/fstab
```

Look at all the Linux stuff you are learning?!?!

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-27
> **deckerry said:**
> How do I know if the liveUSB is still coming up as /dev/sda?
I did the commands anyway and it said this:
 
```
Installation finished. No error reported.
```
 
Then I restarted and tried booting to Ubuntu and got the same error message from post #9.

Based on your other recent posts, your hard drive is still /dev/sdb.  So this still isn't fixing this.

Hopefully the fstab from the disk will give us some clue...

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-27
> **fabricator4 said:**
> Just a quick reality check...  was the original screen you posted (where it was looking for the .deb file) from deckerry's machine?

If so, the system is trying to download the patch directly - ie it already knows what file it wants to download.

Therefore, if it finds the .deb already in the right directory will (fingers crossed) probably just use it instead of trying to download it "again".

Deckerry, open a terminal window (after booting off the hard drive and inserting the usb) and try the following:

```

sudo cp /media/volume_name/pool/main/p/patch /var/cache/apt/archives/

```

You'll have to change "volume_name" to the actual volume name of the USB.  If you don't know what this is, in the terminal window type:

```

ls /media

```

and it should be printed on the screen.  If the volume name is a huge string of digits you can use the autocomplete feature in bash instead of typing the whole thing: when you get to the volume name in the above command line type the first few characters and then press the tab key.  Bash will insert the rest of the volume name for you.

Chris.
1) The image from post #3 was from my screen after booting into Ubuntu through my computer's hard drive, which I can't access anymore. (see post #9)
 
2)You said "[COLOR=blue]Deckerry, open a terminal window (after booting off the hard drive and inserting the usb) and...[/COLOR]" I would love to boot off my hard drive but I can't. So I don't know if entering that code after booting from the usb would help. Would it? Maybe. I have no Idea?
 
3)After booting from the usb I tried the code: [COLOR=red]ls /media[/COLOR][COLOR=black] and it said: [/COLOR][COLOR=red]ls: cannot access media: No such file or directory[/COLOR]

---

### Post by Hedgehog1 on 2011-03-27
You are limited to working from the LiveUSB.  You are posting from it, right?  You don't have to jump back to windows to post when you are on the LiveUSB - that still has wireless access.

To get to the the terminal, you can menu to it. 

In the Terminal (Menu to: Applications >> Accessories >> Terminal),  please run this command:
```
mount
```
Then copy the text from the output and paste it into your next post.

This will tell us what partitions are mounted...

***The Hedge***

:KS

p.s. my goal is to get your working BEFORE we reach another 10 page thread...

---

### Post by deckerry on 2011-03-27
> **Hedgehog1 said:**
> That fstab file is the one for the LiveUSB, sadly.

Please do this to get to the fstab (**F**ile **S**ystem **TAB**le) on the install:

```
sudo mount /dev/sdb5 /mnt
```

```
gksudo gedit /mnt/etc/fstab
```

Look at all the Linux stuff you are learning?!?!

***The Hedge***

:KS
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdb5 during installation
UUID=f264b1c4-9dbc-4b50-84f0-f8dad7719ecd / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb6 during installation
UUID=cc68e7f2-e551-45e6-addc-073158cb1199 none swap sw 0 0

```

---

### Post by deckerry on 2011-03-27
> **Hedgehog1 said:**
> You are limited to working from the LiveUSB. You are posting from it, right? You don't have to jump back to windows to post when you are on the LiveUSB - that still has wireless access.
 
To get to the the terminal, you can menu to it. 
 
In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:
```
mount
```
Then copy the text from the output and paste it into your next post.
 
This will tell us what partitions are mounted...
 
***The Hedge***
 
:KS
 
p.s. my goal is to get your working BEFORE we reach another 10 page thread...
 
```

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sda1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/loop1 on /media/casper-rw type ext2 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5 on /media/f264b1c4-9dbc-4b50-84f0-f8dad7719ecd type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5 on /mnt type ext4 (rw)
ubuntu@ubuntu:~$ 
&#12288;

```

---

### Post by deckerry on 2011-03-27
Hedgehog1, you're going to make me a linux supergenious - hopefully in under 10 pages! LOL

---

### Post by Hedgehog1 on 2011-03-27
This is just insane...

The error message says it cannot find **f264b1c4-9dbc-4b50-84f0-f8dad7719ecd** during boot:

/dev/disk/by-uuid/**f264b1c4-9dbc-4b50-84f0-f8dad7719ecd** does not exist.

But you are mounted to it successfully from the LiveCD:

/dev/sdb5 on /media/**f264b1c4-9dbc-4b50-84f0-f8dad7719ecd** type ext4 (rw,nosuid,nodev,uhelper=udisks)

And your fstab file correctly identifies it:

UUID=**f264b1c4-9dbc-4b50-84f0-f8dad7719ecd** / ext4 errors=remount-ro 0 1

At this moment, I just do not see why this partition is not being found during boot up.  Everything looks just as it should...

***The Hedge***

:(

---

### Post by Hedgehog1 on 2011-03-27
> **deckerry said:**
> Hedgehog1, you're going to make me a linux supergenious - hopefully in under 10 pages! LOL

First I have to make myself a supergenious...

Your 'puter may be the death of me...

I gotta ask for help.

***The Hedge***

---

### Post by deckerry on 2011-03-27
is there something we could do at the error message screen from post #9 while booting from the computer's hard drive without the usb?
 
I'm sitting in front of 2 computers right now. I'm on the internet on one computer and looking at the ubuntu error message on the other

---

### Post by deckerry on 2011-03-27
(deleted message)

---

### Post by Hedgehog1 on 2011-03-27
It is possible to tell grub the UUID of the partition - but grub already has the correct one (based on the error message).  Other than increasing the wait time, but the partition should be ready as it is on the very same drive as we are booting off of.

I would cry - but that NEVER helps....

***The Hedge***

*Waiting for the calvary to arrive...  Quackers is having a look.  He has the persona of 'John Wayne', in the body of 'Donald Duck'*.

---

### Post by Quackers on 2011-03-27
Hello deckerry,
first what is your hardware - ie laptop/desktop/make & model please.
Then, if you are not there already please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by deckerry on 2011-03-27
Before I installed Ubuntu to my hard drive, I could get the internet to work while booting off the usb. Now I can't get the internet to work while booting off the usb. I don't know why but anyway I just downloaded that file off a different computer then booted Ubuntu off the usb. Here's the output:
 
```
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdb1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb3: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD
sdc1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdd1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *             63   150,328,426   150,328,364   7 HPFS/NTFS
/dev/sdb2         150,336,268   216,765,044    66,428,777   5 Extended
/dev/sdb5         150,336,270   212,684,534    62,348,265  83 Linux
/dev/sdb6         212,684,598   216,765,044     4,080,447  82 Linux swap / Solaris
/dev/sdb3         216,781,110   234,436,544    17,655,435   7 HPFS/NTFS

Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdc1                  63   234,436,544   234,436,482   7 HPFS/NTFS

Drive: sdd ___________________ _____________________________________________________
Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdd1    *             63   976,768,064   976,768,002   c W95 FAT32 (LBA)

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/loop1       69322da9-ca3b-3c4f-b0dc-129f6a71dba1   ext2       casper-rw                     
/dev/sda1        16E6-0A57                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EC8AF1E38AF1A9EA                       ntfs       OS                            
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sdb5        f264b1c4-9dbc-4b50-84f0-f8dad7719ecd   ext4                                     
/dev/sdb6        cc68e7f2-e551-45e6-addc-073158cb1199   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F248CE0448CDC815                       ntfs       DATA                          
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        3DD7-40B2                              vfat       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== sdb5/boot/grub/grub.cfg: ===========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi
function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
 linux /boot/vmlinuz-2.6.32-28-generic root=UUID=f264b1c4-9dbc-4b50-84f0-f8dad7719ecd ro   quiet splash
 initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
 echo 'Loading Linux 2.6.32-28-generic ...'
 linux /boot/vmlinuz-2.6.32-28-generic root=UUID=f264b1c4-9dbc-4b50-84f0-f8dad7719ecd ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sdb1)" {
 insmod ntfs
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set ec8af1e38af1a9ea
 drivemap -s (hd0) ${root}
 chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
 insmod ntfs
 set root='(hd1,3)'
 search --no-floppy --fs-uuid --set 2c88743c8874071c
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sdb5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=f264b1c4-9dbc-4b50-84f0-f8dad7719ecd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=cc68e7f2-e551-45e6-addc-073158cb1199 none            swap    sw              0       0
=================== sdb5: Location of files loaded by Grub: ===================

  85.7GB: boot/grub/core.img
 103.0GB: boot/grub/grub.cfg
  85.7GB: boot/initrd.img-2.6.32-28-generic
  85.6GB: boot/vmlinuz-2.6.32-28-generic
  85.7GB: initrd.img
  85.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sdd1
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  02 4c 38 3a b4 d1 01 00  00 00 00 00 02 00 00 00  |.L8:............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b2 40 d7 3d 4d  79 20 42 6f 6f 6b 20 20  |..).@.=My Book  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 88  a3 03 1d 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Hedgehog1 on 2011-03-27
Quackers,

Is the boot failing because:

```
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='**(hd1,5)**'
 search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
 linux /boot/vmlinuz-2.6.32-28-generic root=UUID=f264b1c4-9dbc-4b50-84f0-f8dad7719ecd ro   quiet splash
 initrd /boot/initrd.img-2.6.32-28-generic
```

s/b 

```
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='**(hd0,5)**'
 search --no-floppy --fs-uuid --set f264b1c4-9dbc-4b50-84f0-f8dad7719ecd
 linux /boot/vmlinuz-2.6.32-28-generic root=UUID=f264b1c4-9dbc-4b50-84f0-f8dad7719ecd ro   quiet splash
 initrd /boot/initrd.img-2.6.32-28-generic
```

Because the LiveUSB is taking the role of (**hd0**) when present {forcing the hard drive to (**hd1**)}, but then the hard drive is (**hd0**} when booting without the LiveUSB?

***The Hedge***

---

### Post by Quackers on 2011-03-27
Ok thanks.
I notice from the boot script that /Windows/System32/winload.exe is missing from Windows' boot files in sdb3. Does Windows boot at all?
Also, just to recap, if you take out the usb flash drive which is registering as sda, what error message are you getting, and do you get a grub menu first?

Hedgehog1, I suspect that may have something to do with it.I've seen other systems call usb flash drives /dev/sda, but I'm not sure what governs that. On my system a flash drive is always /dev/sdc

---

### Post by Hedgehog1 on 2011-03-27
> **Quackers said:**
> Hedgehog1, I suspect that may have something to do with it.I've seen other systems call usb flash drives /dev/sda, but I'm not sure what governs that. On my system a flash drive is always /dev/sdc

The only system where I see the USB as /dev/sda is when I boot off a system using a USB and there is no hard drive in the computer.

Otherwise my USB drives are also always the letter following my hard drives (/dev/sdc in my case, too).

:confused:

---

### Post by deckerry on 2011-03-27
Vista works just fine, actually when I boot into Vista, I can hear it laughing in my face! Here's a picture of my ubuntu error. I think it's the same as in post #9.
 
This computer may require fixing by the use of a hammer.:)

---

### Post by Hedgehog1 on 2011-03-27
It is the same error message:

```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/f264b1c4-9dbc-4b50-84f0-f8dad7719ecd does not exist. Dropping to a shell!
Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter ‘help’ for a list of built-in commands.
(initframs) _
```

So it is consistent, anyway...

Where are the hammers?

---

### Post by Quackers on 2011-03-27
I presume that you are getting a grub menu?
If you are, highlight the previous-numbered kernel and then press enter (if you have one). Does the system then boot?
If that doesn't work and you still get the busybox prompt, wait a few seconds then type "exit" without the quotes and press enter.
What happens then?

---

### Post by Hedgehog1 on 2011-03-27
The real bummer of this is:

*I think that if your CD worked, we would have skipped over this issue because of how removable drives are identified.*

***The Hedge***

---

### Post by deckerry on 2011-03-27
> **Quackers said:**
> I presume that you are getting a grub menu?
If you are, highlight the previous-numbered kernel and then press enter (if you have one). Does the system then boot?
If that doesn't work and you still get the busybox prompt, wait a few seconds then type "exit" without the quotes and press enter.
What happens then?
After selecting to boot to ubuntu on the screen whether to boot to Vista or Ubuntu or several other choices, it spits out come code and ends up right to the "does not exist" error with Bubybox and initramfs.
 
I don't know what a grub menu is.
I don't know how to "highlight the previous-numbered kernel"
I don't know what a kernel is.
 
HOLY CRAP! I TYPED EXIT AND I'M IN UBUNTU!
It's asking me to log in. Sweet. I think I'll do that.

---

### Post by Quackers on 2011-03-27
Good idea :-)
On your normal system (when it used to boot up normally) what screen did you get when you first press the power button? Did you get a choice to boot Windows or Ubuntu? That's a grub menu.

---

### Post by Hedgehog1 on 2011-03-27
Grub Menu Example:

[IMG]http://img860.imageshack.us/img860/5730/small37grub2ndtime.png[/IMG]

---

### Post by deckerry on 2011-03-27
These are the very very very first screens that I see when no usb is connected.
 
Oh and by the way, I rebooted the computer to take photos of these screens and when I tried choosing ubuntu from the list, the busybox error message came up again. 
 
So I tried "exit" again and guess what...
 
Instead of going into ubuntu like last time, it just repeated the error message again.
 
Crap!

---

### Post by deckerry on 2011-03-27
Wait, no. Now I just waited a little longer and typed exit again for the heck of it and now I'm in ubuntu's sign-in screen again. Waow I'm so confused.

---

### Post by Hedgehog1 on 2011-03-27
This is starting to make a little sense to me (not much, just a little).

First though - while you are booted from the hard drive, please do this from the terminal:

```
sudo update-grub
```

Once it is done, reboot into Ubuntu again.

This will tell us a few things...

***The Hedge***

---

### Post by deckerry on 2011-03-27
> **Hedgehog1 said:**
> This is starting to make a little sense to me (not much, just a little).
 
First though - while you are booted from the hard drive, please do this from the terminal:
 
```
sudo update-grub
```
 
Once it is done, reboot into Ubuntu again.
 
This will tell us a few things...
 
***The Hedge***
```

ryan@ryan-laptop:~$ sudo update-grub
[sudo] password for ryan: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
ryan@ryan-laptop:~$ 
```
 
here's the output.
 
after i restarted, it gave me the busybox message again
 
but "quit" worked and i've logged back into ubuntu

---

### Post by Quackers on 2011-03-27
Try this please.
At the grub menu and while your Ubuntu option is highlighted, press the "e" key.
A new window will appear.
Using the arrow keys navigate the cursor to the end of the line that starts ```
kernel	/boot/vmlinuz-
``` then go to the end of that line. It should currently end with "quiet splash"
after quiet splash press the space bar then type in ```
rootdelay=120
``` then press ctrl+X to boot.
What happens then?

---

### Post by Hedgehog1 on 2011-03-27
**EDIT:** Please follow Quackers instructions first...

OK - Now I would like you to:

Menu to: System >> Administration >> Disk Utility

Then look at the 'SMART data' for each of your hard drives

What is their current health?

***The Hedge***

:KS

---

### Post by deckerry on 2011-03-27
after puting in the rootdelay it boots up with no problem

---

### Post by Quackers on 2011-03-27
It seems that your hard drive may be spinning up a bit more slowly than Ubuntu expects it to. This can happen sometimes. The fix is to tell it to wait a bit longer before dropping to a busybox shell.
You can enter the rootdelay=120 (or probably less, eg 90, or even 60) permanently, so that you don't need to put it in manually.
I've never done it, but I would assume it goes in /etc/default/grub, but I'm not sure which line it goes in. I'll ask an old-timer where it goes and get back with proper instructions :-)

---

### Post by deckerry on 2011-03-27
Disc Health seems good

---

### Post by Hedgehog1 on 2011-03-27
To add the boot delay to grub permanently:

```
gksudo gedit /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **rootdelay=120**"

```
sudo update-grub
```

***The Hedge***

---

### Post by Quackers on 2011-03-27
I wasn't sure whether it was that line or
GRUB_CMDLINE_LINUX=""
Also I suspect the amount of time can be reduced significantly (maybe 90 or 60) but no matter.

---

### Post by Hedgehog1 on 2011-03-27
> **Quackers said:**
> I wasn't sure whether it was that line or
GRUB_CMDLINE_LINUX=""
Also I suspect the amount of time can be reduced significantly (maybe 90 or 60) but no matter.

This is the line we put the **acpi_osi=\\\"Linux\\\"** for laptops that are running hot.

Can you help get the Broadcomm wireless network driver off the USB and running on the install?

---

### Post by Hedgehog1 on 2011-03-27
The disks are OK - that is good.

The root delay will deal with he slower 'spin up' time - that is good.

Now there is the network issue that we started with.

While you are running Ubuntu from the hard drive, insert the USB and wait for it to appear on the desktop.

Then

```
sudo cp /media/**PENDRIVE**/pool/main/p/patch /var/cache/apt/archives/
```

***The Hedge***

---

### Post by Quackers on 2011-03-27
Sorry, but I am absolutely useless with drivers and particularly network stuff :-(
I've been lucky, never having to struggle in that area :-)

---

### Post by deckerry on 2011-03-27
ok so here's what i'm looking at. does this mean the internet should work? at least technically?

---

### Post by deckerry on 2011-03-27
OMG IT WORKS IT WORKS IT WORKS!!!!!!!!!!!!!!!!!!
 
 
Holy crap. After one of the greatest battles of all time, I came out on top with the help of Ubuntu Forum Supergeniuses!!!! 
 
Thank you Quackers and Hedgehog1. If I wasn't broke, I'd pay you!
Thanks also to fabricator4, samscot, and dutch70 who helped. You guys all rock!!!
 
Next mission: Getting Ubuntu to look cool with desktop effects and sweet stuff like that!!

---

### Post by Hedgehog1 on 2011-03-27
**[SIZE="3"]It has taken 17 pages of posts - but we did it![/SIZE]**


That is true team work - thanks to ***everyone*** for your efforts.


*I am going to watch TV now...*



***The Hedge***

:KS

---

### Post by fabricator4 on 2011-03-27
Edit:
[deleted]

You guys work so fast, I looked in to see (I'm on lunch break) and didn't realised you'd solved it.  There must have been another page and I didn't realise...

Great outcome, well done everyone.  Have fun with your new system!

Chris

---


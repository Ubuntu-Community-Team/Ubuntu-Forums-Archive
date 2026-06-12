---
title: "cd/dvd drive? where is it?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by janem on 2009-02-14
hello all, thanks in advance for any help you care to offer.

I am an absolute newbie with linux and have just reformatted my laptop with ubuntu 8.10. I am slowly navigating around to become familiar with it.

I apologise if this is a stupid question...I have only ever used windows before...but where do I locate my cd/dvd drive? Also, will I be able to read data discs (jpegs, mp3's etc) backed up from my vista pc?

Thanks again,

Jane:)

---

### Post by m_duck on 2009-02-15
If you click "Places" in the top left, there will be a CD / DVD drive entry. Also, if you insert a CD or DVD some form of pop up should appear to acknowledge the fact and let you choose what you want to do with it.

More technically, they will be mounted in the */media* directory, probably as *cdrom* or *cdrom0.*

---

### Post by janem on 2009-02-15
Hello and thanks for your reply. I have looked under "places" and all there is listed is; home folder, desktop, documents, music, pictures, video, computer, cd/dvd creator, network, connect to server, search for files.

When I click on cd/dvd creator it just takes me to a box that i can drag files to to write to cd...but does not actually list what is already in my drive.

Any other suggestions?

Jane

---

### Post by cariboo on 2009-02-15
If you have a cd in the drive, it will have the disc label instead of saying cdrom. In the attached screenshot my cd/dvd drive has a dvd caleed Queen in it.

Jim

---

### Post by janem on 2009-02-15
Thanks for the screenview. It doesn't help though, I have tried several different cd's and dvd's and nothing shows up and nothing pops up asking what to do with them. 

I know the drive works, it worked yesterday with Vista and I used it to install ubuntu from the cd. i just can't find it. Do I have to install drivers maybe?

Jane:) Trying to stay positive...:confused:

---

### Post by kimikrishna on 2009-02-15
as for me , if i insert cd/dvd 
it automatically comes up in desktop

---

### Post by 3rdalbum on 2009-02-15
That's an interesting problem. After inserting a disc, wait about 30 seconds and open a terminal window (Applications > Accessories > Terminal) and paste this command in:

```
dmesg
```

Select the last few lines of it, go to the Edit menu and choose Copy, and then paste it into a reply here.

---

### Post by janem on 2009-02-15
Hi, Thanks, the following is from the end of dmesg

[  629.098720] wlan0: associated
[  629.099319] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  639.136057] wlan0: no IPv6 routers present
[ 1269.256865] CPU0 attaching NULL sched-domain.
[ 1269.256889] CPU1 attaching NULL sched-domain.
[ 1269.284235] CPU0 attaching sched-domain:
[ 1269.284250]  domain 0: span 0-1 level MC
[ 1269.284256]   groups: 0 1
[ 1269.284266]   domain 1: span 0-1 level CPU
[ 1269.284271]    groups: 0-1
[ 1269.284277]    domain 2: span 0-1 level NODE
[ 1269.284283]     groups: 0-1
[ 1269.284293] CPU1 attaching sched-domain:
[ 1269.284297]  domain 0: span 0-1 level MC
[ 1269.284301]   groups: 1 0
[ 1269.284309]   domain 1: span 0-1 level CPU
[ 1269.284313]    groups: 0-1
[ 1269.284319]    domain 2: span 0-1 level NODE
[ 1269.284324]     groups: 0-1
[ 1270.161123] usb 4-1: USB disconnect, address 4
jane@jane-laptop:~$ 


jane:P

---

### Post by janem on 2009-02-20
i guess no one has any idea then?
i can use usb and sd card no problems, so i know how the media should show up...it is simply not happening...

jane:(

---

### Post by Ben Page on 2009-02-20
You won't see any cd drives if they are not "mounted". So before you go searching for a drive first "mount"-insert it. Then you can open nautilus (the file browser) like in the screen Jim posted, and click the computer icon in the toolbar, this will bring you to something like my computer in windows, there you will see "filesistem" drive, and if you have them every other drive, so if your DVD drive is not here it won't be anywhere else. Remember, DVD or CD must be inserted to be "mounted"

Assuming that /media/cdrom0/ is the location of CD/DVD-ROM
To mount CD/DVD-ROM:
 sudo mount /media/cdrom0/ -o unhide
To unmount CD/DVD-ROM:
 sudo umount /media/cdrom0/
To make a directory (like - /media/cdrom0/) use mkdir ...

---

### Post by tarps87 on 2009-02-20
Can you post the contents of your fstab file:
```
gedit /etc/fstab
```

You can try mounting it manually.
First put a cd in the drive, now open a terminal and type
```
sudo mkdir /media/cdrom
```
(If the directory /media/cdrom already exists you can skip this step)
```
sudo mount /dev/scd0 /media/cdrom
nautilus /media/cdrom
```

---

### Post by mc4man on 2009-02-20
Whether or not there is media in the drive you should see the device, click on places -> computer and there should be an icon for the cd/dvd drive.

Put some media in the drive with a known, readable filesystem, (preferably either a data cd or dvd movie.
Give it it few seconds or so and open a terminal. (Applications -> Accessories -> terminal.

When it pops up copy and paste this in and press enter.

```
sudo lshw -C disk
```

copy and paste the terminal output into your reply. (after pasting in do this
> 
highlight the text and click on the little quote icon in the reply task bar, (fourth from right

> Also, will I be able to read data discs (jpegs, mp3's etc) backed up from my vista pc?


Data disks  must be in the "mastered" format, not the "live system" one or they won't be readable in 8.10 (definitely for data dvd's, not sure about data cd's

---

### Post by janem on 2009-02-21
> **Ben Page said:**
> 
 sudo mount /media/cdrom0/ -o unhide



When I do this I get the line

"special device /dev/scd0 does not exist"

> **tarps87 said:**
> Can you post the contents of your fstab file:
```
gedit /etc/fstab
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=861e5055-1e97-49ea-a89d-ac978bca02b9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=254d802f-c891-47c7-8aaa-481dd57dc3fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

> **tarps87 said:**
> 
You can try mounting it manually.
First put a cd in the drive, now open a terminal and type
```
sudo mkdir /media/cdrom
```


i get mkdir: cannot create directory `/media/cdrom': File exists


> **tarps87 said:**
> 
(If the directory /media/cdrom already exists you can skip this step)
```
sudo mount /dev/scd0 /media/cdrom
nautilus /media/cdrom
```

This opens the cdrom file browser. cdrom and cdrom0 exist, just nothing in them, regardless of what cd or dvd i have in the drive.

> **mc4man said:**
> Whether or not there is media in the drive you should see the device, click on places -> computer and there should be an icon for the cd/dvd drive.



there is no icon in places -> computer. It only has one icon for file system. Within this I can find a cdrom folder with an arrow top right corner...nothing in folder. also can find a media folder, within this folder is a cdrom folder and a cdrom0 folder. Again, both are empty.

> **mc4man said:**
> 



```
sudo lshw -C disk
```

copy and paste the terminal output into your reply. 

 *-disk                  
       description: ATA Disk
       product: ST9120822AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.CL
       serial: 5LZ42L5K
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=95f3457a


hope someone can make sense of all this.

thanks
jane:)

---

### Post by stalkingwolf on 2009-02-21
Can you boot from the live CD?  If you can that tells you that it is not a hardware issue(IE the drive is good and it is not a cabling issue).
Run the above commands and save the output to an external source or your
home file on the installed system.  you can then compare both out puts line by line and see where the difference is.
If not check that the drive is seated properly (laptop) or cables are seated properly ( desktop).

---

### Post by janem on 2009-02-22
Yes, I can boot from the Live CD. When I do this I can now see my cd/dvd drive in places.

I ran all the same commands and here is difference.


gedit /etc/fstab 
aufs / aufs rw 0 0

tmpfs /tmp tmpfs nosuid,nodev 0 0

/dev/sda5 swap swap defaults 0 0

ubuntu@ubuntu:~$ sudo mount /dev/scd0 /media/cdrom

mount: block device /dev/scd0 is write-protected, mounting read-only

ubuntu@ubuntu:~$ nautilus /media/cdrom






ubuntu@ubuntu:~$ sudo lshw -C disk

  *-cdrom                 

       description: DVD-RAM writer

       product: DVDRAM GMA-4082N

       vendor: HL-DT-ST

       physical id: 0.1.0

       bus info: scsi@3:0.1.0

       logical name: /dev/cdrom

       logical name: /dev/cdrw

       logical name: /dev/dvd

       logical name: /dev/dvdrw

       logical name: /dev/scd0

       logical name: /dev/sr0

       logical name: /cdrom

       logical name: /media/cdrom

       version: TX07

       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram

       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro state=mounted status=ready

     *-medium

          physical id: 0

          logical name: /dev/cdrom

          logical name: /cdrom

          logical name: /media/cdrom

          configuration: mount.fstype=iso9660 mount.options=ro state=mounted

  *-disk

       description: ATA Disk

       product: ST9120822AS

       vendor: Seagate

       physical id: 0.0.0

       bus info: scsi@0:0.0.0

       logical name: /dev/sda

       version: 3.CL

       serial: 5LZ42L5K

       size: 111GiB (120GB)

       capabilities: partitioned partitioned:dos

       configuration: ansiversion=5 signature=95f3457a

  *-disk

       description: SCSI Disk

       product: STORAGE DEVICE

       vendor: Generic

       physical id: 0.0.0

       bus info: scsi@5:0.0.0

       logical name: /dev/sdb

       version: 9451

       size: 8085MiB (8477MB)

       capabilities: removable

     *-medium

          physical id: 0

          logical name: /dev/sdb

          size: 8085MiB (8477MB)

          capabilities: partitioned partitioned:dos


Pretty obvious difference in the sudo lshw -C disk, haha, is that the cd/dvd drive shows up!

What next?

Jane:confused:

---

### Post by tarps87 on 2009-02-23
This seems a little strange.
What was the output from
```
sudo mount /dev/scd0 /media/cdrom
```
when running from the installed version?
One thing you can try is commenting out the cd line is fstab
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
to
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
Try rebooting and running the command
```
sudo lshw -C disk
```
I can see why this would change things but other than that I am out of ideas at the moment

---

### Post by janem on 2009-02-23
> **tarps87 said:**
> This seems a little strange.
What was the output from
```
sudo mount /dev/scd0 /media/cdrom
```
when running from the installed version?


output from installed version is

mount: special device /dev/scd0 does not exist

> **tarps87 said:**
> 
One thing you can try is commenting out the cd line is fstab
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
to
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
Try rebooting and running the command
```
sudo lshw -C disk
```


will try this now and report back

jane:)

seems to have made no change

jane@jane-laptop:~$ sudo lshw -C disk
[sudo] password for jane: 
  *-disk                  
       description: ATA Disk
       product: ST9120822AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.CL
       serial: 5LZ42L5K
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=95f3457a
jane@jane-laptop:~$

---

### Post by janem on 2009-02-24
Help??? I am thinking of reformatting back to windows if i can't resolve this problem](*,)#-o

---

### Post by HunkirDowne on 2009-02-24
Can you show me your partitions?

```
sudo fdisk -l > fdisk-list.txt
```

The above will read (read-only) the disk devices connected to your system whether they are mounted or not.  From there we can determine what the mount command should look like.

---

### Post by prinny42 on 2009-02-24
This is quite a bit of a stretch, and I honestly have pretty much no knowledge about this kind of thing, but I got my floppy drive working in pretty much this exact way, so it seems worth a shot.

Issue
```
gksudo gedit /etc/modules
```

This file will probably look like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```

Add "cdrom" at the end so it looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
cdrom
```

Save and close the file, then reboot and see if it can detect your CD drive.  Just let me reiterate though that this is purely based off of intuition from my experience with my floppy drive.  However, I think it's worth a shot.  Best case scenario:  it works.  Probable scenario:  nothing happens.  Worst case scenario:  it breaks something and you have issue the command (possibly from a live CD if it messed something up *really* badly):

```
sudo cp /etc/modules~ /etc/modules
```

---

### Post by janem on 2009-02-24
> **HunkirDowne said:**
> Can you show me your partitions?

```
sudo fdisk -l > fdisk-list.txt
```

The above will read (read-only) the disk devices connected to your system whether they are mounted or not.  From there we can determine what the mount command should look like.

This code did nothing. asked for my password and then returned to command line.

Jane

---

### Post by janem on 2009-02-24
> **prinny42 said:**
> This is quite a bit of a stretch, and I honestly have pretty much no knowledge about this kind of thing, but I got my floppy drive working in pretty much this exact way, so it seems worth a shot.

Issue
```
gksudo gedit /etc/modules
```

This file will probably look like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```

Add "cdrom" at the end so it looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
cdrom
```

Save and close the file, then reboot and see if it can detect your CD drive.  Just let me reiterate though that this is purely based off of intuition from my experience with my floppy drive.  However, I think it's worth a shot.  Best case scenario:  it works.  Probable scenario:  nothing happens.  Worst case scenario:  it breaks something and you have issue the command (possibly from a live CD if it messed something up *really* badly):

```
sudo cp /etc/modules~ /etc/modules
```

Thanks but didn't work, changed nothing.

Jane

---

### Post by HunkirDowne on 2009-02-25
> **janem said:**
> This code did nothing. asked for my password and then returned to command line.

Jane

Sorry, should have been more explicit.  This is what was supposed to happen but it should have also created a file in whatever directory you ran it in.  The file will be called 'fdisk-list.txt' and you can open it in gedit and copy/paste as a reply.  I wasn't as clear as I could've been.

But let's say that your fdisk shows that it is '/dev/sdb1'.  There are a few ways to mount disks (including CDs, DVDs, hard disks, etc.) and these can be viewed by typing 'info mount' in the command line or viewing online at [Super Man Pages]("http://gd.tuwien.ac.at/linuxcommand.org/man_pages/mount8.html").

You probably have a mount point (directory) to go to already, but just in case, make sure that you have something like '/media/cdrom'.  If not, execute the following in the terminal window to create one.

```
 sudo mkdir /media/cdrom 
```

Here are three possibilities assuming that /dev/sdb1 is the device file for your drive:

**auto mount:** ```
 sudo mount /dev/sdb1 /media/cdrom 
```
This will let mount guess what the format is.

udf mount: ```
 sudo mount -t udf /dev/sdb1 /media/cdrom 
```

iso-format: ```
 sudo mount -t iso9660 /dev/sdb1 /media/cdrom 
```


Forgive me if I'm treading back over an old trail.  I did a quick check of this thread and hadn't seen anything at all about mounting as a scsi disk device (the 'sd' in '/dev/sdb1'; scsi = small computer system interface -- pronounced 'scuzzy' by most, although rumor has it the originators thought it would be called 'sec-si' or 'sexy'.)

I hope it's as easy as the above.  I know how frustrating it can be to not be able to get something done when it really should be much more simple than that.  Also assuming that you likely installed from the very drive that you are now trying to access.


Take care,
-HD.

---

### Post by janem on 2009-02-25
> **HunkirDowne said:**
> Sorry, should have been more explicit.  This is what was supposed to happen but it should have also created a file in whatever directory you ran it in.  The file will be called 'fdisk-list.txt' and you can open it in gedit and copy/paste as a reply. .

thanks for that. this is the fdisk-list.txt

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14223   114246216   83  Linux
/dev/sda2           14224       14593     2972025    5  Extended
/dev/sda5           14224       14593     2971993+  82  Linux swap / Solaris

Does the rest of your post still apply given this list? If so I shall give it a go tomorrow, time for bed now, this linux is doing my head in! Yes, you are correct, it is the drive I installed from too lol](*,)

Truth be known, I will probably hardly use the drive anyway, and will just use sd cards and usbs. But I just HATE not being able to do something and if it SHOULD work, I want to get it to work!!

Thanks so much for everyone's help so far. These forums are fantastic.

Jane

---

### Post by geirha on 2009-02-25
It's very odd that it works in the live session, but not from the installed system. 

Is the cdrom module loaded (in the installed system)?
```
lsmod | grep cdrom
```

Does it detect the cd-rom during boot (of the installed system), at all?
```
dmesg | egrep -C3 'CD|DVD'
```

Also, in the GRUB menu, could you try booting an older kernel and see if the dvd drive works with that kernel?

---

### Post by HunkirDowne on 2009-02-25
> **janem said:**
> thanks for that. this is the fdisk-list.txt

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14223   114246216   83  Linux
/dev/sda2           14224       14593     2972025    5  Extended
/dev/sda5           14224       14593     2971993+  82  Linux swap / Solaris

Does the rest of your post still apply given this list? 

**No, it does not!**  :confused:

I'm beginning to get a very small taste of your frustration.

For whatever reason (you do have a CD in the drive, right?  That will need to be there for the system to see it properly, if indeed it can ever see it properly, which it sounds like it can't...
...properly).  I've interrupted myself again.

For whatever reason, your system is only seeing the one hard disk and no other disk devices including, of course, your cd/dvd, and including any usb devices, card devices, etc.  There will need to be media in the drive, the external devices will need power (some get that from USB, others, obviously require a separate power supply).

Essentially, what the system is looking for is available media.  'fdisk' will normally see all this media even if it is not mounted.  However, to do so the media must be recognizable as a device (even a device with an "unknown" filesystem or no filesystem at all).

I'm going to have to bail out on this one as far as advice as the only time I haven't been able to see a device in fdisk is when Windows couldn't see it either so it is most likely a device failure (but not necessarily a complete failure).

For my experience, I was always going to Linux because I could see devices in Linux that *(1)* I could not see at all in **Windows** or *(2)* could not see it as well in **Windows** as I could in Linux.  One day I decided that rather than treat Linux as (merely) a rescue system, that it might actually suffice as an everyday operating system, so I bought (before broadband) a copy of **Redhat 5.*something*** (I still have an unopened **v6.1** on the shelf.).  I played around with **OS/2** and then back in Windows for a while but got hold of **Debian** and now **Ubuntu** and *for me* this is totally the way to go -- given that my all-time favorite operating system was **OS/2** but, alas, IBM didn't like it as much as I did.  Ultimately, from the terminal, I prefer Linux either way, but the object oriented user interface in **OS/2 *Warp*** was, in my opinion, a more superior design than I had seen elsewhere.

Getting back to the business at hand, the other advice given here seems sound as far as my experience goes and I bow to the more experienced ladies and gentlemen.  I'll probably continue to lurk.  Should the problem be solved, I will certainly learn something from it.

**Keep up the good work, y'all!**

---

### Post by HunkirDowne on 2009-02-25
One last thought before I get ready for work.  Is there information available when booting from the LiveCD that would be of use on the installed system?

My original thought was the fstab (/etc/fstab) but since 'fdisk' doesn't see the device...  But perhaps there is a driver that works in the LiveCd that doesn't work (or isn't installed) on the installed system.

I have been frustrated in the past with the ability of the installed system to properly identify and configure my wireless (Atheros).  While this is as much a vendor issue as it is a Linux thing, I found that the Ubuntu LiveCD would recognize it and allow for easy configuration.  But the GUI config tool in the installed system never seems to work properly -- at least not right away.  (It always eventually works but only after stopping and starting the service for several iterations.)

Bottom line, those of you that are familiar with the /dev files might be able to recognize a difference between the two systems and find the solution that way.

HTH
-HD

H2G2-Don't Panic! and all that.

---

### Post by HunkirDowne on 2009-02-25
Guess what I'm having trouble with now?  I can't see my CD drive on our new laptop.  I can see it from Linux, just not Vista.   :lolflag:

Also, I deleted desktop icons in one user account and they were gone for all users accounts.  Interesting.  (not exactly what came out of my mouth).


</venting>


:guitar:

---

### Post by janem on 2009-02-25
> **geirha said:**
> It's very odd that it works in the live session, but not from the installed system. 

Is the cdrom module loaded (in the installed system)?
```
lsmod | grep cdrom
```

Does it detect the cd-rom during boot (of the installed system), at all?
```
dmesg | egrep -C3 'CD|DVD'
```

Also, in the GRUB menu, could you try booting an older kernel and see if the dvd drive works with that kernel?

here is the response from above codes in installed system

jane@jane-laptop:~$ lsmod | grep cdrom
cdrom                  47784  0 
jane@jane-laptop:~$ dmesg | egrep -C3 'CD|DVD'
jane@jane-laptop:~$ 


Hmmm... as to this GRUB and old kernel talk, forgive my ignorance, I have no idea what that means. I am an "absolute beginner" and need step by step instructions:oops:

Jane

---

### Post by janem on 2009-02-25
> **HunkirDowne said:**
>  (you do have a CD in the drive, right?  That will need to be there for the system to see it properly, if indeed it can ever see it properly, which it sounds like it can't...
...properly). 

For whatever reason, your system is only seeing the one hard disk and no other disk devices including, of course, your cd/dvd, and including any usb devices, card devices, etc. 





Yes, have tried various CD's and DVD's in the drive and also checked they all worked first on my Vista System.

Actually it is only the CD/DVD drive it can not see, I have no problems with usb flash drives or SD cards when I plug them in.

Thanks for all your help

Jane

---

### Post by janem on 2009-02-25
> **HunkirDowne said:**
> Guess what I'm having trouble with now?  I can't see my CD drive on our new laptop.  I can see it from Linux, just not Vista.   :lolflag:

Also, I deleted desktop icons in one user account and they were gone for all users accounts.  Interesting.  (not exactly what came out of my mouth).


</venting>


:guitar:

:lolflag: Don't get me started on Vista!!

---

### Post by geirha on 2009-02-25
> **janem said:**
> 
Hmmm... as to this GRUB and old kernel talk, forgive my ignorance, I have no idea what that means. I am an "absolute beginner" and need step by step instructions:oops:

Jane

Right after the BIOS, the boot loader, GRUB, will start. It will either show you a menu of boot options, or show a line like:
```
Press `ESC' to enter the menu...
``` and a counter counting down from 3 seconds. Hit Esc before the time is up to see the menu. At the menu, you should see at least the entry for the latest kernel with a corresponding recovery-mode version. Something like this:
```

Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)

```
Every time a newer kernel comes along in an update, a pair of such entries are added to the top of that menu, making the newest the default. Try selecting the previous regular (i.e. not recovery mode) kernel entry. If the dvd-drive doesn't work with the previous kernel, also try the oldest kernel, which should be the same kernel as the Ubuntu CD uses. If it works with an older kernel, then it must be a bug in the newest kernel that causes your dvd-drive to not get detected.

---

### Post by tarps87 on 2009-02-26
If changing the kernel version as suggested above does not work you can try
```
sudo modprobe cdrom
sudo modprobe sr_mod

```
If this does not work all I can suggest is backing up your data and reinstalling

Edit:
If I remove the cd modules I lose the cd drive form places but running
sudo lshw -C disk
Still shows the cd drive hardware

---

### Post by janem on 2009-02-28
> **geirha said:**
> 
```

Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)

```
Every time a newer kernel comes along in an update, a pair of such entries are added to the top of that menu, making the newest the default. Try selecting the previous regular (i.e. not recovery mode) kernel entry. If the dvd-drive doesn't work with the previous kernel, also try the oldest kernel, which should be the same kernel as the Ubuntu CD uses. If it works with an older kernel, then it must be a bug in the newest kernel that causes your dvd-drive to not get detected.

only found the 2 kernals, no others.

---

### Post by janem on 2009-02-28
> **tarps87 said:**
> If changing the kernel version as suggested above does not work you can try
```
sudo modprobe cdrom
sudo modprobe sr_mod

```
If this does not work all I can suggest is backing up your data and reinstalling

Edit:
If I remove the cd modules I lose the cd drive form places but running
sudo lshw -C disk
Still shows the cd drive hardware

again nothing. so did a reinstall. same problem, still no drive

jane@jane-laptop:~$ sudo lshw -C disk
[sudo] password for jane: 
  *-disk                  
       description: ATA Disk
       product: ST9120822AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.CL
       serial: 5LZ42L5K
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=95f3457a
jane@jane-laptop:~$ 


this is getting so frustrating now. about to say goodbye to ubuntu forever!:mad:

---

### Post by janem on 2009-03-01
ok I found this and need help with it. I am having trouble understanding the "old school" formatting? not quite sure how to do that. If some could decipher these instructions into something an "absolute beginner" could understand that would be great.

[http://www.pcdudes.co.uk/showthread.php?t=1031](http://www.pcdudes.co.uk/showthread.php?t=1031)

Thanks
Jane

---

### Post by ikisham on 2009-03-01
Jane, I'm no expert in these things, but the guide you linked to is very well explained. Since it's for ubuntu and sda1 is the default main partition, I *imagine* that you can type it exactly as in the guide (in respesct to that 'old school' stuff - */dev/sda1 / ext3 defaults,errors=remount-ro 0 1*). If you want to, wait a bit more, but my opinion is that that guide would fit in your case.

---

### Post by prinny42 on 2009-03-01
@ikisham:  While I do agree that the guide seems pretty well explained, I certainly wouldn't have understood it when I had just installed.  Heck, I still don't know what "chroot into the Ubuntu install" means.

@janem:  To make giving step-by-step directions easier, could you please post the contents of the file "/etc/fstab" and the results of the command "df -h" (also, please rap them in code tags [the number sign in the menu above] so that they retain their formatting)?

---

### Post by mc4man on 2009-03-01
The other option (if possible) is that considering you just did a fresh install is to do another one but use the alternate install cd.
I believe there is an option where you can choose your bootloader from either grub or lilo.

---

### Post by janem on 2009-03-02
> **prinny42 said:**
> 

@janem:  To make giving step-by-step directions easier, could you please post the contents of the file "/etc/fstab" and the results of the command "df -h" (also, please rap them in code tags [the number sign in the menu above] so that they retain their formatting)?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=58a4b0d7-e1bb-48a2-883c-891865bd9d1d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=468c2eab-7af4-4ee5-a3a0-aa6dbc29eb91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

```
jane@jane-laptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda6              96G  3.1G   88G   4% /
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M  100K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  2.8M  494M   1% /dev
tmpfs                 496M  768K  496M   1% /dev/shm
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.27-11-generic/volatile

```

thanks
jane

---

### Post by WatchingThePain on 2009-03-02
Yeah it's not like windows where it always has a my cd icon or whatever. Stuff is automounted as needed. Also If you are using a dvd device like me it takes longer to spin up so it takes a while (and a bit of 'whirring') before the icon appears. I'm not sure if theres a way to make it spin up faster, maybe a scsi dvd player would work faster.

---

### Post by prinny42 on 2009-03-02
Sorry, could you also provide the output of:
```
sudo fdisk -l
```

I was just going to use the output of it you posted earlier, but it looks like it would be in conflict with your /etc/fstab, so it's probably changed.  Thanks.

---

### Post by janem on 2009-03-02
> **prinny42 said:**
> Sorry, could you also provide the output of:
```
sudo fdisk -l
```

I was just going to use the output of it you posted earlier, but it looks like it would be in conflict with your /etc/fstab, so it's probably changed.  Thanks.

```
jane@jane-laptop:~$ sudo fdisk -l
[sudo] password for jane: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1203     9663066   83  Linux
/dev/sda2            1204       14593   107555175    5  Extended
/dev/sda5           14224       14593     2971993+  82  Linux swap / Solaris
/dev/sda6            1204       13853   101611062   83  Linux
/dev/sda7           13854       14223     2971993+  82  Linux swap / Solaris

Partition table entries are not in disk order
jane@jane-laptop:~$ 
```

Thanks so much for your help

Jane:P

---

### Post by prinny42 on 2009-03-02
Okay, sorry to keep requesting the output of more commands, but please post the output of
```
blkid /dev/sda1 && blkid /dev/sda2 && blkid /dev/sda5 && blkid /dev/sda6 && blkid /dev/sda7
```

The existence of /dev/sda6 and /dev/sda7, along with the apparent absence of /dev/sda1 from /etc/fstab (though that won't be positive without the output of the above command) are bothering me a lot.

---

### Post by Ben Crisford on 2009-03-02
It should come up on the desktop, if not then it should be in places.

If it isn't then sorry, but I don't know the terminal command :S.

---

### Post by janem on 2009-03-02
> **prinny42 said:**
> Okay, sorry to keep requesting the output of more commands, but please post the output of
```
blkid /dev/sda1 && blkid /dev/sda2 && blkid /dev/sda5 && blkid /dev/sda6 && blkid /dev/sda7
```

The existence of /dev/sda6 and /dev/sda7, along with the apparent absence of /dev/sda1 from /etc/fstab (though that won't be positive without the output of the above command) are bothering me a lot.

```
jane@jane-laptop:~$ blkid /dev/sda1 && blkid /dev/sda2 && blkid /dev/sda5 && blkid /dev/sda6 && blkid /dev/sda7
/dev/sda1: UUID="861e5055-1e97-49ea-a89d-ac978bca02b9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="254d802f-c891-47c7-8aaa-481dd57dc3fc" TYPE="swap" 
/dev/sda6: UUID="58a4b0d7-e1bb-48a2-883c-891865bd9d1d" TYPE="ext3" 
/dev/sda7: UUID="468c2eab-7af4-4ee5-a3a0-aa6dbc29eb91" TYPE="swap" 
jane@jane-laptop:~$ 
```

ooohh I wonder why such strange things are going on with my laptop...lol

regards,
Jane:confused:

---

### Post by janem on 2009-03-02
> **Ben Crisford said:**
> It should come up on the desktop, if not then it should be in places.

If it isn't then sorry, but I don't know the terminal command :S.

Thanks, but if you read the previous 4 pages you will see we have already discussed where it "should" be, but isn't.

Thanks for your input anyway,
Jane:P

---

### Post by janem on 2009-03-02
> **prinny42 said:**
> Sorry, could you also provide the output of:
```
sudo fdisk -l
```

I was just going to use the output of it you posted earlier, but it looks like it would be in conflict with your /etc/fstab, so it's probably changed.  Thanks.

just to clarify...I did do a reinstall, so some of the outputs in the first couple of pages may be different. I installed differently this time. First time I did a "use entire disc" and this time I did a partition to keep my files from last install. 

I am happy to reinstall again differently if needed. Didn't really know what I was doing, just followed prompts.

Regards,
Jane

---

### Post by tarps87 on 2009-03-03
I've had another thought, what happens if you boot from the livecd but select boot from first hard drive instead of install or try Ubuntu?

---

### Post by prinny42 on 2009-03-03
No, I don't think you'll have to reinstall.  I'm a bit confused by /dev/sda1 being the only partition marked for boot when it's /dev/sda6 that is mounted on /, but I don't think that will matter here, in the end.

Anyway, before you do any of the following, just know that I've never done this myself before, so I can't be sure if it works.  It's all based on my (possibly flawed) understanding of that guide.

Also, as for files that you want to keep, I strongly recommend backing up regularly all the time (the rule of thumb is that if it's not backed up you don't have it), but I especially recommend doing so before a major modification like this.

Make sure you have a live CD on hand; you'll need it soon.  Then edit /etc/fstab with your text editor of choice to add a number sign before the first instance of UUID, move the rest of that line down one, and put /dev/sda6 where that UUID once was; it should end up looking like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
#UUID=58a4b0d7-e1bb-48a2-883c-891865bd9d1d
/dev/sda6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=468c2eab-7af4-4ee5-a3a0-aa6dbc29eb91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Now shut down and boot with the live CD.  Open a terminal and enter the following command:
```
sudo parted
```

Once you're in parted:
```
set 6 boot on
quit
```

Back at the regular terminal:
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda6 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev/ /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu /bin/bash
sudo liloconfig
```

When liloconfig asks, you should tell it to install the boot block to /dev/sda6 and to install the MBR to /dev/sda (no number this time); you can probably just answer yes if it asks anything else.

Finally, back at the terminal, enter these commands:
```
sudo lilo -b /dev/sda6
sudo umount /mnt/ubuntu/proc
sudo umount /mnt/ubuntu/dev
sudo umount /mnt/ubuntu
```

Then reboot.  At that point, you should be done.

Good luck.

---

### Post by HunkirDowne on 2009-03-03
> **prinny42 said:**
> I'm a bit confused by /dev/sda1 being the only partition marked for boot when it's /dev/sda6 that is mounted on /, but I don't think that will matter here, in the end.

I've a bit of experience with multiple operating systems (even multiple distros) and do not find it odd that /sda1 isn't in the list.  This happens to me quite often after a second (or third) installation.  It simply means that the partition is not used.

As far as being flagged bootable (or not) GRUB takes the load and the boot flag is rather arbitrary at that point.  Don't know about LILO as I try to avoid LILO unless I'm booting from a floppy (which I haven't done in years).

Pardon me if Jane is using LILO, although I think the default Ubuntu install would be GRUB.  Unless she specifically requested LILO, wouldn't GRUB be her boot manager?

So basically, I'm thinking that while backing up the personal data files is not a bad option, I'm not sure what the rest of the above would accomplish given that the kernel doesn't see the /dev/cdrom.  It would be interesting, though, to "hear" what /etc/mtab, fdisk -l, or df -h would say after booting the LiveCD.

(Any of the following should show the /dev/sdc1 as existing, if not mounted.  '/etc/mtab/' will only show what is currently mounted so it didn't make my list.  There may be more commands, but these are all too familiar, I'm sure.  ;-/

From the LiveCD:
```
df -h
```
or
```
sudo fdisk -l
```


-DH  (I'm feel like being slysdexic today -- too much Bachman Turner Overclock)

---

### Post by prinny42 on 2009-03-03
> I've a bit of experience with multiple operating systems (even multiple distros) and do not find it odd that /sda1 isn't in the list. This happens to me quite often after a second (or third) installation. It simply means that the partition is not used.

As far as being flagged bootable (or not) GRUB takes the load and the boot flag is rather arbitrary at that point. Don't know about LILO as I try to avoid LILO unless I'm booting from a floppy (which I haven't done in years).

I see.  I simply found it confusing because it runs contrary to my (rather minimal) prior experience, not because it conflicted with any positive knowledge of mine.  Thank you.

On the point of the CD-ROM drive, I honestly don't know how installing LILO would help either, but the link janem provided earlier seems to suggest that it could, and I figured trying it couldn't hurt (so long as the appropriate precautions were taken, anyway).

---

### Post by janem on 2009-03-03
> **HunkirDowne said:**
> 
Pardon me if Jane is using LILO, although I think the default Ubuntu install would be GRUB.  Unless she specifically requested LILO, wouldn't GRUB be her boot manager?



I have very minimal knowledge of LILO and GRUB and don't know the difference, therefore have no preference. (I think my brain is about to meltdown). But all the info I have googled has suggested that my particular laptop has a conflict with GRUB which is causing the cd/dvd drive not to show. The link is one of a few I found suggesting that using LILO will work. So worth a try at this point.

All my data is backed up on both external harddrive and my pc, so if I kill my laptop not too concerned.

Will go and try this now and let you all know how it goes.

jane

---

### Post by janem on 2009-03-03
> **tarps87 said:**
> I've had another thought, what happens if you boot from the livecd but select boot from first hard drive instead of install or try Ubuntu?

Tried this and it made no difference that I can see.

Jane

---

### Post by janem on 2009-03-03
prinny42...I wish I could tell you I love you...but not yet arrggg

I get as far as

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda6 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev/ /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu /bin/bash
sudo liloconfig
```

Then I get a message that says

> Warning!
Either your /etc/fstab config file is missing, or it doesn't contain a valid entry for the root filesystem! This generally means your system is very badly broken. Configuration of LILO will be aborted; you should try to repair the situation and then run /usr/sbin/liliconfig again to retry the configuration process.


jane

---

### Post by janem on 2009-03-03
> **HunkirDowne said:**
> .  It would be interesting, though, to "hear" what /etc/mtab, fdisk -l, or df -h would say after booting the LiveCD.



from the LiveCD
```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 496M  2.4M  494M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 496M  2.4M  494M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M   88K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  2.8M  494M   1% /dev
tmpfs                 496M  180K  496M   1% /dev/shm
rootfs                496M   97M  400M  20% /
/dev/scd0             4.4G  4.4G     0 100% /cdrom
/dev/loop0            1.5G  1.5G     0 100% /rofs
tmpfs                 496M   12K  496M   1% /tmp
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1203     9663066   83  Linux
/dev/sda2            1204       14593   107555175    5  Extended
/dev/sda5           14224       14593     2971993+  82  Linux swap / Solaris
/dev/sda6   *        1204       13853   101611062   83  Linux
/dev/sda7           13854       14223     2971993+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
```

jnea;)

---

### Post by POWMS on 2009-03-04
Janem
I'm using a fresh install of Xubuntu and I cannot 'see' my cd drive when a disc is inserted. Nothing under Places and no icon appears on my desktop.
I inserted a 'Device' button on my top panel. When I click this the cdrom0 is listed, but in red as unmounted. When I click on it the cd mounts and an icon appears on my desktop and all is well (for me anyway).
I'm not sure if this will help you but I thought I might throw my 2 cents worth into this discussion.........

---

### Post by janem on 2009-03-04
That's really interesting POWMS. How do I list a "device" button on top panel?

Thanks
Jane

---

### Post by POWMS on 2009-03-04
Jane
right click on a blank space on the panel and click on the + tab. A window will open showing a list of services you can add. I'm not sure what is displayed in Ubuntu, but look for 'devices' and add this to your panel. When you click on this button all devices should be listed, hard drive, usb drives etc, etc.........good luck.
Craig

---

### Post by janem on 2009-03-04
Craig, thanks for the help. I just checked and I I found no "devices" but a button called "disk mounter". I added this but it only lists my partitioned media drive and nothing else:-(.

Thanks anyway,
Jane

---

### Post by bailbath on 2009-03-04
Do you know which dvd/cd drive is in the laptop? If not what is the exact model of laptop you have?
Ian

---

### Post by bailbath on 2009-03-04
Open a terminal and put in the following command
> wodim --devices
Ian
Ps I know is frustrating but you have a unusual problem. I have installed Linux on a lot of Pc's and Laptops and even a PS3 but I have never encountered a problem that I can't get round with the help of other Linux users. However I have never had your problem and am wondering about the dvd drive not being compatible. Do you have an external cd/dvd drive? If you do plug that in and see if it appears in places and then put a cd/dvd in and see if you get a popup. Manufacturers sometimes are reluctent to release hardware info so It can be a pain sometimes with a particular hardware device but in my experience you will get a answer in the end to your problem.

---

### Post by janem on 2009-03-04
Ian,

My laptop is a Lenovo 3000 N200 product ID 0687A31. I have searched through all the documentation and cannot find any info on the drive manufacturer. All the info I have is it is a CD-RW/DVD-+RW Drive.

When googling my laptop it seems other's have had problems with linux and the optical drive not showing, but I have not been able to find an answer. 

Unfortunately I do not have an external cd drive to test.

this is the output from the command you asked for

```
jane@jane-laptop:~$ wodim --devices 
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
jane@jane-laptop:~$ 
```

Anyway, I have always said the best way to learn about computers is when things go wrong and you have to try to solve the problem...I am certainly getting a crash course in ubuntu!!

Jane:D

P.S just wanted to say this forum is fantastic. Never before have I had so many responses with people wanting to help.

---

### Post by bailbath on 2009-03-04
Ok I will do some digging for you on that laptop.I will post back soon.
Ian

---

### Post by bailbath on 2009-03-04
You are not on your own with this 
[http://forums.linuxmint.com/viewtopic.php?f=49&t=9779](http://forums.linuxmint.com/viewtopic.php?f=49&t=9779)

I am still digging around
Ian

---

### Post by bailbath on 2009-03-04
Ok there are some mentions of this being a problem with embedded firmware within windows stopping this being recognized by another operating system (unbelievably disgusting if true) but I'm wondering about how your laptop is setup in your bios which you may know is the control system of your motherboard. I'm reluctant to pursue this online so I am wondering if you have a local LUG or linux user group who may be able to help in person if you do not feel confident of changing settings in your bios (if that helps or not remains to be seen).
Earlier on the command with wodim it mentions check into a readme here is a link.
[http://ai.ms.mff.cuni.cz/cgi-bin/dwww/usr/share/doc/wodim/README.ATAPI.setup](http://ai.ms.mff.cuni.cz/cgi-bin/dwww/usr/share/doc/wodim/README.ATAPI.setup)
Also I'm hoping someone else will pick this up and have more knowledge to help you as I think it is getting to a point where unless you find a specific solution to that drive you will struggle. Also I believe this is a IDE drive and not a sata drive is it possible that this has a bearing with the sata controller and sata hard drive? Which is where my bios question comes in.
So hopefully someone with more knowledge is going to post next!
Not going to abandon you, will keep a eye on this but am at work till 8 tonite. Good luck!
Ian

---

### Post by championboxes on 2009-03-04
> [http://forums.linuxmint.com/viewtopic.php?f=49&t=9779](http://forums.linuxmint.com/viewtopic.php?f=49&t=9779)

not really sure if this will help any but I found in [this]("http://ubuntuforums.org/showthread.php?t=703509&page=2") thread that there may be a setting in the BIOS that changing the setting "SATA mode" (from legacy mode to native mode)

---

### Post by tarps87 on 2009-03-04
Janem using you machine name if have found a solution that is reported to work. It involves installing lilo instead of grub, the default bootloader. I am currently testing installing it myself as I have not installed it separately tried it before (Although I am using it in Slackware).
Someone maybe able to guide you through this, if not I will post back after I have it working.

---

### Post by bailbath on 2009-03-04
> **tarps87 said:**
> Janem using you machine name if have found a solution that is reported to work. It involves installing lilo instead of grub, the default bootloader. I am currently testing installing it myself as I have not installed it separately tried it before (Although I am using it in Slackware).
Someone maybe able to guide you through this, if not I will post back after I have it working.

I think this has been tried earlier in this thread with no solution.
Ian

---

### Post by tarps87 on 2009-03-04
> **bailbath said:**
> I think this has been tried earlier in this thread with no solution.
Ian

I think it was suggested but not tried?

> **championboxes said:**
> not really sure if this will help any but I found in [this]("http://ubuntuforums.org/showthread.php?t=703509&page=2") thread that there may be a setting in the BIOS that changing the setting "SATA mode" (from legacy mode to native mode)

This maybe worth a try, can you post the output of this please
```

ls -l /dev/cdrw

```

---

### Post by bailbath on 2009-03-04
> **tarps87 said:**
> I think it was suggested but not tried?





You are right what difference would this make as a bootloader to using grub? 
Ian

---

### Post by tarps87 on 2009-03-04
The method in which the GNU/Linxu kernal is loaded, I don't know why it should stop the cd drive from being detected. Other users have found that this solves the problem and once installed it will seem to be the same as using grub so it is worth a try.

---

### Post by HunkirDowne on 2009-03-04
> **prinny42 said:**
> On the point of the CD-ROM drive, I honestly don't know how installing LILO would help either, but the link janem provided earlier seems to suggest that it could, and I figured trying it couldn't hurt (so long as the appropriate precautions were taken, anyway).

Absolutely worth a shot, the more I think of it.  LILO is a very basic loader.  I personally prefer GRUB, all things being equal, but LILO (being as basic as it is) may be better at detecting the device especially if (as mentioned elsewhere) there is firmware OS detection.   (Not exactly the same issue, but I recall people having problems with winmodems back in my OS/2 days.  My modems were almost always external, so it wasn't a problem).

Issues like this are what has led me in the past to design (if not build) my own systems.  Although this can be done with laptops, it is a bit more difficult and one must rely on vendor specifications to get the information required to make an informed decision.  Too much to ask of the average person, in my opinion, and even of myself here lately when deciding quickly (48 hours, give or take) on a new laptop for the children's school work.  (clarifier: I'm not average, but not above average.  Just sorta off to the side.  Fringe?  Lunatic?  I am most definitely not insane! ;-)

Still, I get almost a perverse sense of satisfaction out of running systems that I have built or designed but must admit that all things considered, it would be a waste of time to do so unless one was doing this on a more massive scale or at least called it a hobby.

But back to the point at hand, if LILO doesn't work, there is some driver somewhere that does as evidenced by the fact that the LiveCD boots, runs, plays, frolics, whatever.  Despite my years of building systems and running different operating systems, I have never really delved too deeply into the drivers side which is where it would appear this issue lies.  I do find it rather odd (having experienced similar issues myself) that the LiveCD runs differently than the installed system.  I understand partly why this is but truly wish that one of the installation choices was "just like CD" without having to go through all the rigmarole of signing up for different repos and knowing (or guessing?) which software to download from those repos.  One day I'll have to pick the CD apart and make a list.

-HD.

---

### Post by janem on 2009-03-04
> **tarps87 said:**
> I think it was suggested but not tried?

Actually the LILO instead of GRUB was tried, on page 6 of this thread. I got a big fat warning message! Maybe this is another way I haven't tried yet?



here is the output for ls -l /dev/cdrw

```
jane@jane-laptop:~$ ls -l /dev/cdrw
ls: cannot access /dev/cdrw: No such file or directory
jane@jane-laptop:~$ 


```

Haven't had a chance to read through all the last lot of replies here. will have to do that tomorrow. Don't know where you all reside but I am in Australia and it is near to 11pm and my 10 month old is waking for another feed!! 

Thanks so much, I shall leave you all to scratch your heads on this one.

Until tomorrow, Jane:D

---

### Post by prinny42 on 2009-03-04
> Warning!
Either your /etc/fstab config file is missing, or it doesn't contain a valid entry for the root filesystem! This generally means your system is very badly broken. Configuration of LILO will be aborted; you should try to repair the situation and then run /usr/sbin/liliconfig again to retry the configuration process.

Hm, perhaps the guide is wrong on the point of editing /etc/fstab.  Back in your regular install (as opposed to from the live CD) issue this command to restore your /etc/fstab to its former state:
```
sudo cp /etc/fstab~ /etc/fstab
```

After that, try installing LILO again, but skip the part about editing /etc/fstab.  That's all I can think of.

---

### Post by janem on 2009-03-04
> **prinny42 said:**
> Hm, perhaps the guide is wrong on the point of editing /etc/fstab.  Back in your regular install (as opposed to from the live CD) issue this command to restore your /etc/fstab to its former state:
```
sudo cp /etc/fstab~ /etc/fstab
```

After that, try installing LILO again, but skip the part about editing /etc/fstab.  That's all I can think of.

Tried again and get same message.

during the process from LiveCD, after i input 

```
set 6 boot on
quit
```

in parted, i get a message saying /etc/fstab may need to be updated. So maybe there is a step missing in the guide? How do I update the /etc/fstab at this point?

Jane

---

### Post by bailbath on 2009-03-04
I am back from work, well actually detoured via the pub! Hmm let's not get detracted by Lilo I think the problem lie's in sata/ide/bios and some sort of hardware issue. The solution maybe to change the drive as it is not Linux compatible!
Ian
:P

---

### Post by janem on 2009-03-04
> **bailbath said:**
> I am back from work, well actually detoured via the pub! Hmm let's not get detracted by Lilo I think the problem lie's in sata/ide/bios and some sort of hardware issue. The solution maybe to change the drive as it is not Linux compatible!
Ian
:P

That it is not a viable option for me at the moment. I had already decided not to bother upgrading or changing this laptop in any way, it only cost around $450 and is just not worth spending any money on, I will be getting a new one within 6 months. if I was going to buy anything for it, I would have just gotten more RAM so vista wasn't so bloody slow!

Also, I can plug in thumb drives and SD cards if I need to add media or back up files etc. it just seems a shame to have an optical drive sitting there that does not work. 

I guess a lesson learned here is not to buy a Lenovo in future. It is pretty disgraceful that they are made not to work with whatever OS I should choose!

Jane

---

### Post by mc4man on 2009-03-04
If you could get someone to burn you the alternate install cd then it's pretty straightfoward, your given the choice of lilo or grub as a bootloader.
Plus you could square up your partitioning (unless you intended to create it as it is now.

---

### Post by janem on 2009-03-05
> **mc4man said:**
> If you could get someone to burn you the alternate install cd then it's pretty straightfoward, your given the choice of lilo or grub as a bootloader.
Plus you could square up your partitioning (unless you intended to create it as it is now.

I don't know anyone who even knows what LINUX is let alone have a copy of an alternate install cd! is there somewhere I can download it?

Jane

---

### Post by tarps87 on 2009-03-05
you can download it from one of these mirrors
[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors)
It will have alternate in its name. You will have to burn it to a cd to install.

---

### Post by mc4man on 2009-03-05
Like or instance here for Au
[http://mirror.aarnet.edu.au/pub/ubuntu/releases/8.10/](http://mirror.aarnet.edu.au/pub/ubuntu/releases/8.10/)
12th file listed (ubuntu-8.10-alternate-i386.iso

There are a few possible "pitfalls' if you've never used the text based installer

For the keyboard, it's usually better to choose 'no' and pick from a list (or just pay attention when setting up manually.

The alternate install has you enter a 'host' name (this is done automatically for you in the live-cd (the default is 'your username'-desktop or 'your username-laptop'

For example on my live cd install, from a terminal prompt
> [COLOR="Red"]doug[/COLOR]@[COLOR="Blue"]doug-desktop[/COLOR]:~$ 
The red is my user name, the blue is the hostname

The screen will show "ubuntu", either leave as is, add a -desktop, or whatever. (one word) Just don't use the username you intend to use by itself. (in other words, jane as a host name is no good, jane-laptop is good, blah-blah is good, ect.


when you get to the partitioning screen choose 'guided - use entire disk'

After that it will ask for your full name - enter that. Then it will finally ask for the user name, password.

After it install the files you'll get a screen to install grub, use the tab or arrow keys to select 'go back' and from the list choose 'install lilo...' Press enter and let the install finish

(this is from memory so if anyone wants to correct please do so.

---

### Post by bailbath on 2009-03-06
Sounds right to me. Good luck hope it works if you try it.Let us know
Ian

---

### Post by janem on 2009-03-07
thanks so much for the info. I am going to give this a go tomorrow when I get some free time to myself. will let you all know how it goes.

jane:P

---

### Post by mc4man on 2009-03-07
Minor little point
> After that it will ask for your full name - enter that. .....
You don't have to enter your 'full' name, what you enter there will be what you see in far right side of upper panel (probably jane now
It would be alright to use jane or janem or whatever you want to see there

---

### Post by janem on 2009-03-07
Hmmmmm...seems I am having problems at every turn.

I get the following message trying to install LILO from the alternate install cd.

> ¨The LILO package failed to install into /target/. Installing LILO as a boot loader is a required step. The install problem might however be unrelated to LILO, so continuing this installation may be possible.¨

When I continue I get message

> running "/sbin/lilo¨ failed with error code ¨1¨

So after aborting from there I now have another GRUB installation with no cd/dvd drive!

anyone know what I have done wrong here?

Thanks
Jane

---

### Post by bailbath on 2009-03-08
Morning Jane aaaaaaaghhhhhh
Right I feel better now!
Ok here is the problem to anyone who is listening- laptop-Lenovo 3000 N200
Dvd drive- LG GMA 4082N not detected once system installed from the Dvd drive worked fine in windows.
link to someone else who had same problem- [here]("http://forums.linuxmint.com/viewtopic.php?f=49&t=9779").
latest suggestion use Lilo instead of Grub.
Feels like we are going round in circles but hopefully someone else will read this and say 'you fools this is the solution'!
Ian

---

### Post by bailbath on 2009-03-08
Someone has suggested that disabling dvd drive in the bios and that worked.

[https://bugs.launchpad.net/ubuntu/+bug/198319]("https://bugs.launchpad.net/ubuntu/+bug/198319")
read to bottom
Ian

---

### Post by ugm6hr on 2009-03-08
This is an interesting (read frustrating) problem.

Having done a fair amount of googling, it appears that this is some interaction between acpi control, Grub and the DVD drive.

Other than disabling acpi (not recommended on a laptop), Lilo has been consistently reported to solve the problem.

I have never installed Lilo, but if the AlternateCD doesn't work, it is possible to install Lilo after a full install with Grub.  It may require a separate /boot partition (not sure).

[http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)

---

### Post by janem on 2009-03-08
oh I am tired....(sigh)

> **ugm6hr said:**
> T, Lilo has been consistently reported to solve the problem.

I have never installed Lilo, but if the AlternateCD doesn't work, it is possible to install Lilo after a full install with Grub.  It may require a separate /boot partition (not sure).

[http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)

I have tried this before and I could not make it work, kept getting an error message. [http://www.uluga.ubuntuforums.org/showthread.php?t=1070257&page=6](http://www.uluga.ubuntuforums.org/showthread.php?t=1070257&page=6) see post #55.

I can try this again, however, prinny42&#347; instruction would now not work, as I have reformatted again, so /etc/fstab blah blah would all be different again. So would have to work it out myself...as I said...so tired...(sigh...) Will need a few days to psych myself up for the effort.

> **bailbath said:**
> Someone has suggested that disabling dvd drive in the bios and that worked.

[https://bugs.launchpad.net/ubuntu/+bug/198319]("https://bugs.launchpad.net/ubuntu/+bug/198319")
read to bottom
Ian

Ian, I have gone into my laptop BIOS...and it is just confusing me...looks nothing like the BIOS on my PC. More like just a settings menu, with limited stuff I can change and I can not find an option to disable the cd/dvd drive at all...don know what I am doing wrong here...(sigh...again).

I am really so over this problem. Usually I like a bit of a challenge, but this is just getting silly. I think I am about to give up my exploration into LINUX:(

Jane

---

### Post by mc4man on 2009-03-08
Why don't you try one more way, really very easy.
Hopefully your partitioning is squared away and ubuntu is on sda1

If you want to post your fstab before trying. (look at my quotes, it's pretty easy to edit, using gedit in fullscreen makes it easier.

Simple way to switch to lilo

Go into synaptic, search lilo, mark it for for reinstall if installed (should be) or mark for install, and click apply.

Click forward on the pop up, after the install finishes  then close out synaptic.


Edit fstab

I'm going to post 2 quotes, one before editing, one after.

*Don't use mine, just an example of how to edit* 

I used cut and paste to move the lines (basically you just switch positions of the UUID=xxxxxx....... and the /dev/sda[COLOR="Red"]x[/COLOR]
Or post yours for someone to edit for you if still unclear

After editing fstab then run liloconfig
```
sudo liloconfig
```

Answer yes to 'install a partition boot record from /dev/sda[COLOR="Red"]1[/COLOR]', pick bitmap, answer yes on remaining screens, reboot

In other words answer yes to all screens.

Just did on a laptop, took a couple of minutes, boots now with lilo

orig. fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9378638b-03a7-4061-b186-1006b2fc8d3d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f8fb7b55-13cf-4ad8-85ef-9fc69b1aaa53 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



Edited fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# UUID=9378638b-03a7-4061-b186-1006b2fc8d3d
/dev/sda1        /               ext3    relatime,errors=remount-ro 0       1
# UUID=f8fb7b55-13cf-4ad8-85ef-9fc69b1aaa53
/dev/sda5      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



---

### Post by janem on 2009-03-09
okay this is what I get...rebooting computer GRUB still booting. 

```
jane@ubuntu-laptop:~$ sudo liloconfig
LILO version 22.8, Copyright (C) 1992-1998 Werner Almesberger
Development beyond version 21 Copyright (C) 1999-2006 John Coffman
Released 19-Feb-2007, and compiled at 14:08:06 on May 15 2008
Ubuntu

Warning: LBA32 addressing assumed
Reading boot sector from /dev/sda1
Using MENU secondary loader
Calling map_insert_data

Boot image: /vmlinuz -> boot/vmlinuz-2.6.27-7-generic
Mapping RAM disk /initrd.img -> boot/initrd.img-2.6.27-7-generic
Warning: The initial RAM disk is too big to fit between the kernel and
   the 15M-16M memory hole.  It will be loaded in the highest memory as
   though the configuration file specified "large-memory" and it will
   be assumed that the BIOS supports memory moves above 16M.
Added Linux ? *

Skipping /vmlinuz.old
Writing boot sector.
Back up copy of boot sector in /boot/boot.0801
2 warnings were issued.
```

Not sure what went wrong there.

Jane:confused:

---

### Post by bailbath on 2009-03-09
I think that Jane has tried everything we have suggested =D>.
If you are happy to continue without a cd/dvd drive for now maybe sometime in the future you may find a solution. If you can find another Linux user near you or better still a LUG let them have a go and if they do it hurrah, if not at least you will have peace of mind that you tried everything and it's a problem caused by hardware not Linux.
If you know a computer geek who has a external dvd/cd to borrow you will find that 99% of dvd/cd drives are fine. You have had a case of bad luck and you are not on your own with this nasty drive.

All the best
Ian

---

### Post by Playerhas on 2009-03-09
Hi, i have a home built computer, it plays cds fine and recognises a dvd when inserted. When i attempt to play it windows media player come up with an error. I've checked all the drivers are installe dna dworking ok. what can i do?

---

### Post by tarps87 on 2009-03-09
I have found one more possible solution, adding combined_mode=libata to the boot line may solve this.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bck
sudo gedit /boot/grub/menu.lst
```
find the line:
kernel /boot/vmlinux*stuff* root=*hex/stuff* 

and add this to the end combined_mode=libata

kernel /boot/vmlinux*stuff* root=*hex/stuff* combined_mode=libata

(Apologies for vague lines using a vm and copy/paste is broke, will update it tonight(GMT))

I have added the line and the computer still boots so I might be worth a try :)


> **Playerhas said:**
> Hi, i have a home built computer, it plays cds fine and recognises a dvd when inserted. When i attempt to play it windows media player come up with an error. I've checked all the drivers are installe dna dworking ok. what can i do?

Starting a new thread, is this is a windows problem look in the windows support part in the forum

---

### Post by janem on 2009-03-09
this is my /boot/grub menu list. please advice what to change to what?

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dff06020-34d1-4142-a510-647126184b7f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dff06020-34d1-4142-a510-647126184b7f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dff06020-34d1-4142-a510-647126184b7f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dff06020-34d1-4142-a510-647126184b7f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dff06020-34d1-4142-a510-647126184b7f
kernel		/boot/memtest86+.bin
quiet

```

thanks

jane:D

---

### Post by bailbath on 2009-03-10
I think your thread got hijacked Jane so I would ignore the two posts above yours.
Ian

---

### Post by tarps87 on 2009-03-10
> **janem said:**
> this is my /boot/grub menu list. please advice what to change to what?

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dff06020-34d1-4142-a510-647126184b7f
kernel		/boot/vmlinuz-2.6.27-7-generic **root=UUID=dff06020-34d1-4142-a510-647126184b7f ro quiet splash** 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dff06020-34d1-4142-a510-647126184b7f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dff06020-34d1-4142-a510-647126184b7f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dff06020-34d1-4142-a510-647126184b7f
kernel		/boot/memtest86+.bin
quiet

```

thanks

jane:D

root=UUID=dff06020-34d1-4142-a510-647126184b7f ro quiet splash **combined_mode=libata**

Sorry I didn't post back sooner, not had a chance

---

### Post by janem on 2009-03-10
> **tarps87 said:**
> root=UUID=dff06020-34d1-4142-a510-647126184b7f ro quiet splash **combined_mode=libata**

Sorry I didn't post back sooner, not had a chance

no probs. Thanks

I tried this and it does not seem to have made any difference. Still booting in GRUB. 

jane

---

### Post by tarps87 on 2009-03-10
> **janem said:**
> no probs. Thanks

I tried this and it does not seem to have made any difference. Still booting in GRUB. 

jane

That was the only other possible fix I found

About lilo, have you tried the last part of this post?

> **prinny42 said:**
> ...
Back at the regular terminal:
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda6 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev/ /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu /bin/bash
sudo liloconfig
```

When liloconfig asks, you should tell it to install the boot block to /dev/sda6 and to install the MBR to /dev/sda (no number this time); you can probably just answer yes if it asks anything else.

Finally, back at the terminal, enter these commands:
```
sudo lilo -b /dev/sda6
sudo umount /mnt/ubuntu/proc
sudo umount /mnt/ubuntu/dev
sudo umount /mnt/ubuntu
```

Then reboot.  At that point, you should be done.

Good luck.

---

### Post by janem on 2009-03-11
> **tarps87 said:**
> That was the only other possible fix I found

About lilo, have you tried the last part of this post?

Yeah, i got as far as sudo liloconfig and got an error message and it aborted.

> Warning!
Either your /etc/fstab config file is missing, or it doesn't contain a valid entry for the root filesystem! This generally means your system is very badly broken. Configuration of LILO will be aborted; you should try to repair the situation and then run /usr/sbin/liliconfig again to retry the configuration process.

jane

---

### Post by mc4man on 2009-03-12
Probably beating a dead horse but in regards to the guide you first followed you may want to try it again and follow it *exactly *starting at 'step' 4. (using "set 1 boot on", "sudo mount /dev/sda1 /mnt/ubuntu/", "lilo -b /dev/sda1" - you should be on sda1 now.

I'm not too sure your fstab was edited properly the first time around.
Does it look similar to the 'edited' one I posted? (if unsure post your fstab and sudo fdisk -l

I'd do an update before trying, 8.10 is on kernel ...11, your still using ....7


searching the memory hole error doesn't lead to any thing positive in relation to your situation

---

### Post by janem on 2009-03-12
okay will do an update and try again, probably tomorrow. I was up to date on one of my installs, but at each new install I haven't bothered as I only have so much download limit for the month!!

Jane

---

### Post by janem on 2009-03-12
> **mc4man said:**
> Probably beating a dead horse but in regards to the guide you first followed you may want to try it again and follow it *exactly *starting at 'step' 4. (using "set 1 boot on", "sudo mount /dev/sda1 /mnt/ubuntu/", "lilo -b /dev/sda1" - you should be on sda1 now.

I'm not too sure your fstab was edited properly the first time around.
Does it look similar to the 'edited' one I posted? (if unsure post your fstab and sudo fdisk -l


okay, do you mean this guide, [http://www.pcdudes.co.uk/showthread.php?t=1031](http://www.pcdudes.co.uk/showthread.php?t=1031), and only do from step 4? so I don't have to install LILO and edit fstab? i do have a fresh new install now, after we had all given up i reinstalled from the LIVECD, as I wasn't sure if all my settings were right and my keyboard setup was a bit wrong etc. So yes I am on sda1 now but have done nothing about trying to install LILO again...So starting from scratch.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18d0be4c-f0ca-430e-851d-1f8edba8ed6a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=01e3be2f-bf29-41ea-b46b-9b9c58ea6876 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

and

```
jane@jane-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14223   114246216   83  Linux
/dev/sda2           14224       14593     2972025    5  Extended
/dev/sda5           14224       14593     2971993+  82  Linux swap / Solaris
jane@jane-laptop:~$ 

```

Jane:D

---

### Post by mc4man on 2009-03-13
Go ahead like just like last time, search in synaptic for lilo, install or if already installed then *reinstall*. (this adds some files to /boot

Then....

Your fstab is still wrong, should be as below. (fix, then try again with instr.'s
(make sure each line in fstab starts at far left if you don't do a copy and paste (replace

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# UUID=18d0be4c-f0ca-430e-851d-1f8edba8ed6a
/dev/sda1       /               ext3    relatime,errors=remount-ro 0       1
# UUID=01e3be2f-bf29-41ea-b46b-9b9c58ea6876
/dev/sda5      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Is there anything unclear about the instr.'s 4 - 8 or Post 50? It gives you all the commands. Just use 1 instead of 6 where it occurs. (set 1 boot on), (sudo mount /dev/sda1 /mnt/ubuntu) (sudo lilo -b /dev/sda1)

Start with (using post 50), after the above stuff
"Now shut down and boot with the live CD. ........"

---

### Post by humphreybc on 2009-03-13
> cd/dvd drive? where is it?

They're normally found on the left or right-hand side of the laptop, although some laptops (such as this one [here]("http://www.ruggedpcreview.com/images/pana_w7_open.jpg")) have a flip open disk drive on the front of the laptop, in the palm rest.


hehe.

---

### Post by nelskurian on 2009-03-13
Do you get the cd drive icon listed in the Places dropdown menu?If you have it,just put a disc and click on the icon.what error message do you got?if its permission issue or something...Do the drive led blinking continuesly after entering the disc.that means it reads..
 check whether the cdrom working properly by simply insert the ubuntu installation disc and wait for 30secs.needs your reply...

---

### Post by bailbath on 2009-03-13
Jane one thing that I thought to ask you to try was boot Ubuntu with a disc already in see if it picks it up then. Try a music cd or dvd rather than the ububtu cd. Ian

---

### Post by col48 on 2009-03-16
Jane - I think you're a heroine to be so persistent with this.  And you guys who have been beavering away - the same.  I just wish I knew enough to help out.  I hope a definitive answer can be found one way or another.

---

### Post by janem on 2009-03-16
> **mc4man said:**
> Go ahead like just like last time, search in synaptic for lilo, install or if already installed then *reinstall*. (this adds some files to /boot

Then....

Your fstab is still wrong, should be as below. (fix, then try again with instr.'s
(make sure each line in fstab starts at far left if you don't do a copy and paste (replace

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# UUID=18d0be4c-f0ca-430e-851d-1f8edba8ed6a
/dev/sda1       /               ext3    relatime,errors=remount-ro 0       1
# UUID=01e3be2f-bf29-41ea-b46b-9b9c58ea6876
/dev/sda5      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Is there anything unclear about the instr.'s 4 - 8 or Post 50? It gives you all the commands. Just use 1 instead of 6 where it occurs. (set 1 boot on), (sudo mount /dev/sda1 /mnt/ubuntu) (sudo lilo -b /dev/sda1)

Start with (using post 50), after the above stuff
"Now shut down and boot with the live CD. ........"

okay so tried again and got a bit further this time...yay...but still got problems...

which bitmap am i supposed to pick? I picked the debianlilo one and got error message...> no such file or directory exists. Also got,
> warning: unable to determine video adaptor in use in present system

other errors i got were....

> sudo: unable to resolve host ubuntu...this came up after sudo liloconfig. but then it just started to do the install thingy anyway...

oh and at the very beggining, after the set 1 boot on bit, it says > you may need to update /etc/fstab...is this why it is going wrong? what am i meant to do here?

Okay, sorry i have written these error messages all over the shop and not in the order they occured...if you need more info let me know.

Jane

---

### Post by mc4man on 2009-03-17
Hi janem, I don't know
I never tried the method in post 50 (used the way in post 91
I'm going to try now, though because post 91 way worked I'd expect post 50 to also (worth checking anyway

As far as 
> no such file or directory exists
Did you reinstall lilo from synaptic *before starting with the live cd?*
Look in computer -> filesystem -> boot. You should see several .bmp including "debianlilo one"

> you may need to update /etc/fstab 
normal, can be ignored. I'd think your fstab is correct now, it you want to post to d. check do so.

I'll let you know if doing post 50 way shows any other errors like yours.

You could try post 91 way again, won't hurt,  should only take a few minutes



Edit:
Did post 50 exactly

What's interesting is I got all the lines you quoted plus the memory hole lines which i didn't see in the post 91 method (they only line i didn't get was about the .bmp because I'd reinstalled lilo first before the live cd.

when I ran this line

I got the unable to resolve host ubuntu
> sudo chroot /mnt/ubuntu /bin/bash


The final 3 lines after "sudo lilo -b /dev/sda1"  don't do anything so just exited the live cd and rebooted

In any event upon rebooting I had lilo as bootloader.

You should try again one more time, either post 91 or post 50 after *reinstalling lilo in synaptic*

Make sure if you use 50 to change sda6 to sda1 the 2 times it occurs
Also make sure to answer yes to every prompt in liloconfig

Or use the how to in your link which has sda1 in the lines already so you can just copy and paste without worry.


re edit 
If you do get this going be aware that a kernel upgrade will probably 'break' lilo. (you'll boot to a kernel panic
Pretty easy to fix, let's see if that's even a concern (hopefully is

---

### Post by janem on 2009-03-17
> **mc4man said:**
> 

Did you reinstall lilo from synaptic *before starting with the live cd?*

d'oh!!! knew i forgot something...trying again!!


YAY...ok it worked and I am finally booting with LILO and **[SIZE="3"][SIZE="5"]YES[/SIZE][/SIZE]** I now can see and access my cd/dvd drive!!

Thank you so much to everyone who helped. Love you all!!! Kiss kiss!!

> **mc4man said:**
> 
re edit 
If you do get this going be aware that a kernel upgrade will probably 'break' lilo. (you'll boot to a kernel panic
Pretty easy to fix, let's see if that's even a concern (hopefully is

So if the above happens what do I do? 

Jane:D:popcorn:\\:D/=D>:guitar:

P.S ended up using post 91 instructions

---

### Post by mc4man on 2009-03-17
Janem - great
I think your problems were that fstab was never edited properly and you didn't do a reinstall of lilo first.
Now i'm sure your clear on that so if for so reason you need to do a complete reinstall.

> kernel upgrade will probably 'break' lilo

That's why I had you update first

You could from here on not update the kernel or I tested this last night before reverting back to grub

I updated the kernel and rebooting failed with a kernel panic.

**What needs to be done is to just run  liloconfig again.** (nothing else

I  couldn't figure a way to drop to a root shell with lilo as bootloader - maybe someone knows how, that would be easiest way.

What worked was this (bit of a pita, but easy, just repeating a section of the linked method

Boot up to your live cd and open a terminal
run these commands

```
sudo mkdir /mnt/ubuntu
```
```
sudo mount /dev/sda1 /mnt/ubuntu
```
```
sudo mount -t proc none /mnt/ubuntu/proc
```
```
sudo mount -o bind /dev/ /mnt/ubuntu/dev

```
```
sudo chroot /mnt/ubuntu /bin/bash
```
```
sudo liloconfig
```

Answer yes to all and then exit out and reboot
I don't think this was needed before exiting but maybe keep in mind
```
lilo -b /dev/sda1
```

I'm sure there's a quicker way, you just need to run liloconfig.
What I didn't try (and too late now) was to run liloconfig after updating kernel, but before rebooting...?

The point is if this happens (a kernel update and reboot to kernel panic) don't freak out,, there is a solution

---

### Post by janem on 2009-03-18
awesome. Thanks so much.

I guess we can officially close this thread now and mark it as SOLVED.

Thank you for everyone who helped out, you have all been very patient with me. 

Jane

---

### Post by bailbath on 2009-03-19
I think you have been very patient with us!
Glad you got somewhere in the end!
Ian

---


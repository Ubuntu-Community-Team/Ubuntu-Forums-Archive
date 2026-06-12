---
title: "ubuntu 8.10 newbie with problems"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by newtel on 2009-02-16
Very keen to install ubuntu. Tried to install on my vista laptop which already had one drive partitioned into two both used by vista.  Loaded the disk and selected install ubuntu. Everything seemed to go well, another partition made for ubuntu (30 gig) and it seemed to install OK. I then launched Ubuntu and had a look around.  Then I shut down and rebooted. I was presented with what I assumed was the dual boot option. there seemed to be two options for windows longhorn.  I selected one and then got the error "grub loading stage 1.5. grub loading please wait error 22"
I must admit panic set in.  I inserted my recovery disk for vista (probably prematurely) and recovered my vista system. 
However now my laptop boots into vista OK but no dual boot option so cannot load ubuntu. I assume it is still there as in vista the sum of my two vista partitions is about 40 gig less than the total hard drive.  Being an absolute ubuntu newbie and at a loss with dos can anyone help me to (if my previous assumptions are correct) dual boot.  I have heard of a piece of software called easybcd but am petrified that if I tried this without guidance I will lose my system again. 

Thanks in anticipation for any help.

---

### Post by halovivek on 2009-02-16
welcome to ubuntu forums.
please check this [thread]("http://ubuntuforums.org/showthread.php?t=1066273") you can get some help

---

### Post by muteXe on 2009-02-16
> **halovivek said:**
> welcome to ubuntu forums.
please check this [thread]("http://ubuntuforums.org/showthread.php?t=1066273") you can get some help

That's an excellent thread for solving this kinda thing.
Also take a look at [http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

I've used the Super Grub disk in the past, it helps a lot in certain situations.

---

### Post by muteXe on 2009-02-16
I was replying to original poster.

---

### Post by caljohnsmith on 2009-02-16
Newtel, if you decide to give the Super Grub Disk a try and it doesn't work for you, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Live CD Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by caljohnsmith on 2009-02-16
> **chris_baller said:**
> sorry but can anyone help my situation or maybe want to help
Your problem is completely unrelated to Newtel's problem, so please start your own thread and I think you will have a much better chance of getting support. :)

---

### Post by stalkingwolf on 2009-02-16
chris_baller

try using the recovery mode.  When grub first starts hit ESC.  this will bring up the boot menu.  Select the recovery option and enter.  recovery will run, when finished you will be presented with a window with several options.  Select "fix broken packages".  hit enter.  when it is finished reboot.

---

### Post by newtel on 2009-02-16
> **caljohnsmith said:**
> Newtel, if you decide to give the Super Grub Disk a try and it doesn't work for you, how about 


Thanks caljohnsmith for your input. I will try both your suggestions.  But I am still concerned that now I have vista accessible to me will I create another problem for myself. Remember I am a complete newbie where ubuntu is concerned and all I want to do is recover my dual boot not loose vista again.  It took me a weekend of recovery and installations. Just glad it wasn't on my desktop computer. Is there a step by step guide for a very nervous user.

---

### Post by perlluver on 2009-02-16
To fix the error dpkg interrupted, ```
sudo dpkg --configure -a
``` in a terminal, Applications>Accessories>Terminal.  Also check out the Ubuntu Guide in my signature.

---

### Post by caljohnsmith on 2009-02-16
> **newtel said:**
> Thanks caljohnsmith for your input. I will try both your suggestions.  But I am still concerned that now I have vista accessible to me will I create another problem for myself. Remember I am a complete newbie where ubuntu is concerned and all I want to do is recover my dual boot not loose vista again.  It took me a weekend of recovery and installations. Just glad it wasn't on my desktop computer. Is there a step by step guide for a very nervous user.
Since you want to be extra careful, how about instead of trying to use the Super Grub Disk, run that script that I linked to in my previous post and post the output. That script certainly won't make any changes or do any harm to your system, and it will most likely give us enough info to diagnose the true cause of your problem. :)

---

### Post by newtel on 2009-02-17
> **caljohnsmith said:**
> Since you want to be extra careful, how about instead of trying to use the Super Grub Disk, run that script that I linked to in my previous post and post the output. That script certainly won't make any changes or do any harm to your system, and it will most likely give us enough info to diagnose the true cause of your problem. :)

Hi, Thanks for reply,

Just to get this clear in my mind you suggest the following.  As I can only boot to vista now I should insert the ubuntu 8.10 cd and run it within windows as a trial from the cd.   Then download boot info script whilst in ubuntu and go to applications/ accessories /terminal/
then enter the following :    sudo bash ~/Desktop/boot_info_script*.sh

Then follow your last paragraph. But.  Do I launch the boot info script or does accessing terminal do that for me?  I feel sure I'm misunderstanding something but I hope you will correct me.

Thanks

---

### Post by caljohnsmith on 2009-02-17
> **newtel said:**
> Hi, Thanks for reply,

Just to get this clear in my mind you suggest the following.  As I can only boot to vista now I should insert the ubuntu 8.10 cd and run it within windows as a trial from the cd. 
I'm not sure what you mean about running the CD within Windows, because you need to somehow boot the CD--is that what you mean? When you installed Ubuntu, how exactly did you do it? I had assumed you burned the Ubuntu Live ISO to a CD and had booted that on start up. Did you do it differently?
> **newtel said:**
> 
 Then download boot info script whilst in ubuntu and go to applications/ accessories /terminal/
then enter the following :    sudo bash ~/Desktop/boot_info_script*.sh

Then follow your last paragraph. But.  Do I launch the boot info script or does accessing terminal do that for me?  
Basically the bottom line is to boot into a Ubuntu desktop where you can download the script, and then run it from the terminal; doing that command in the terminal is all you need to do to run the script, you don't have to launch the script in some other manner. Let me know how that goes or if you run into problems.

---

### Post by stalkingwolf on 2009-02-17
let me try and clear things up a bit.
Put your Live cd in and reboot.
first you get a page to select a language (english is the default)
hit enter.
Next you get the choice of how to boot ( try Ubuntu with no changes is default) hit enter
Your system will now boot to the desk top with a fully functional system.

At this point your HDD is not even mounted (in use).  You are running completely from your  CD Rom and RAM.

Now that you have this fully functional battle station running go to
Applications > Accessories > Terminal and click on terminal.  when it
opens copy and paste the command/script into it.
hit enter.
bobs your uncle.

---

### Post by newtel on 2009-02-17
> **caljohnsmith said:**
> I'm not sure what you mean about running the CD within Windows, 


Thanks caljohnsmith and stalkingwolf

I did not explain myself very well.  I did originally boot from CD and installed ubuntu I did not mean from within windows.  What I will do now is follow instructions and come back.

Thanks

---

### Post by newtel on 2009-02-17
> **caljohnsmith said:**
> 
Basically the bottom line is to boot into a Ubuntu desktop where you can download the script, and then run it from the terminal; doing that command in the terminal is all you need to do to run the script, you don't have to launch the script in some other manner. Let me know how that goes or if you run into problems.

Hi
I finally got there.  This is the result



=```
> Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd1a0e96

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,467,135    21,465,088  27 Hidden HPFS/NTFS
/dev/sda2    *     21,467,136   231,841,102   210,373,967   7 HPFS/NTFS
/dev/sda3         231,850,080   488,392,064   256,541,985   f W95 Ext d (LBA)
/dev/sda5         295,226,568   488,392,064   193,165,497   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9C56A53156A50D58" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="648076D88076B062" TYPE="ntfs" 
/dev/sda5: UUID="01C96452189A21A0" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda5

00000000  46 49 4c 45 30 00 03 00  58 59 35 04 00 00 00 00  |FILE0...XY5.....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  04 00 00 00 00 00 00 00  |................|
00000030  09 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  a0 21 9a 18 52 64 c9 01  a0 21 9a 18 52 64 c9 01  |.!..Rd...!..Rd..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 02 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  a0 21 9a 18 52 64 c9 01  |.........!..Rd..|
000000c0  a0 21 9a 18 52 64 c9 01  a0 21 9a 18 52 64 c9 01  |.!..Rd...!..Rd..|
000000d0  a0 21 9a 18 52 64 c9 01  00 70 00 00 00 00 00 00  |.!..Rd...p......|
000000e0  00 70 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.p..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  df 00 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 0e 00 00 00 00 00  |@...............|
00000130  00 00 0e 00 00 00 00 00  00 00 0e 00 00 00 00 00  |................|
00000140  12 dd 00 03 31 03 96 63  0d 00 01 00 00 c0 d4 8d  |....1..c........|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 03 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
00000180  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
00000190  11 01 02 31 01 c6 2b 01  00 00 01 00 00 90 cd 8d  |...1..+.........|
000001a0  ff ff ff ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 09 00  |................|
00000200

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo/Log1: No such file or directory

```



Hope you understand it.

---

### Post by caljohnsmith on 2009-02-17
OK, so it looks like your Vista installation is OK as we expect, but there is of course no sign of Ubuntu now since you did the Vista restore. Your main Vista partition is sda2, but you also have another NTFS partition sda5. Do you know what is on that partition? Is it just a data partition? While you are on the Ubuntu Live CD, how about posting the output of the following command (do this in the terminal again):
```
sudo mount /dev/sda5 /mnt && ls -l /mnt
```
That will give us an idea what's on that partition (if anything). Also, do you want to keep that sda5 NTFS partition? In other words, you could shrink that partition to make room for Ubuntu, or you could delete it altogether to make room. Let us know what you would ideally like, and we can work from there.

---

### Post by newtel on 2009-02-17
> **caljohnsmith said:**
>  Let us know what you would ideally like, and we can work from there.

I did fully install ubuntu at the outset and browsed. Do you think I have deleted it by recovering vista?
Still very twitchy about changes to the system as I now have vista back.

However here are the results of the query


```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && ls -l /mnt
total 16
drwxrwxrwx 1 root root 4096 2009-02-15 12:22 Documents
drwxrwxrwx 1 root root    0 2009-02-15 11:52 MSOCache
drwxrwxrwx 1 root root 4096 2009-02-14 16:29 $RECYCLE.BIN
drwxrwxrwx 1 root root 8192 2009-02-16 16:20 System Volume Information
ubuntu@ubuntu:~$ 
```

Am I correct in assuming that in recovering vista I have managed to loose about 40 gig of my 250 gig drive.  I had thought ubuntu was still there but not accessible. I would like to use the additional space if I  could recover it but still very twitchy!!
Thanks for all your help so far.

---

### Post by newtel on 2009-02-17
> **newtel said:**
> I did fully install ubuntu at the outset and browsed. Do you think I have deleted it by recovering vista?
Still very twitchy about changes to the system as I now have vista back.

However here are the results of the query


```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && ls -l /mnt
total 16
drwxrwxrwx 1 root root 4096 2009-02-15 12:22 Documents
drwxrwxrwx 1 root root    0 2009-02-15 11:52 MSOCache
drwxrwxrwx 1 root root 4096 2009-02-14 16:29 $RECYCLE.BIN
drwxrwxrwx 1 root root 8192 2009-02-16 16:20 System Volume Information
ubuntu@ubuntu:~$ 
```

Am I correct in assuming that in recovering vista I have managed to loose about 40 gig of my 250 gig drive.  I had thought ubuntu was still there but not accessible. I would like to use the additional space if I  could recover it but still very twitchy!!
Thanks for all your help so far.

ps.  I forgot to say that I have two vista partitions. One with my data on. Is that sda5?

---

### Post by cptr13 on 2009-02-17
I would also like to reccomend iinstalling Ubuntu through WUBI.  That is the safest way for first timers to install and get comfortable with Ubuntu.  It installs inside windows and does no partitioning at all.  When finished, you can simply remove it through the add/remove programs in windows, jsut like any other software.  The preformance is a little slower however, but it''s completely safe for those folks that can't afford to take chances.

To install inside windows, simply put your ubuntu install disc in while running windows and click "install inside windows"

Hope this helps

---

### Post by caljohnsmith on 2009-02-17
When you restored Vista to your HDD, if your Vista CDs/DVDs are OEM (Original Equipment Manufacturer) instead of a genuine Microsoft Vista Install CD, then usually OEM recovery CDs reformat your HDD and reinstall Vista from scratch. It looks to me like that is probably your case. Also, after looking over your partition table more carefully, I see what you mean in that you have about ~30 GB of unused space between your sda2 Vista partition and the sda5 data partition. Instead of trying to recover your lost Ubuntu partitions, I would recommend doing a fresh Ubuntu install to that 30 GB of free space. Or if you want, you could do as cptr13 suggests and just install Ubuntu inside of Windows, otherwise known as a Wubi install. Sometimes Wubi installs have problems that a standard install doesn't, but you might want to try it first until you are more comfortable with Ubuntu; then you could do a standard install of Ubuntu to its own partition when you are ready. So which do you want to try, a Wubi install inside Windows or a standard install to a partition?

---

### Post by newtel on 2009-02-17
> **caljohnsmith said:**
>  So which do you want to try, a Wubi install inside Windows or a standard install to a partition?


The recovery disks I used were the ones I created when I bought the laptop.  They rarely provide disks when buying in the UK. When I installed ubuntu I believe that I created a 30 gig partition for it. Are these the missing gigabytes?   I would like to install as standard to a partition but I don't want to loose what I have. What danger of that?
If you will talk me through it with some instructions I would like to do it.   Have to go out now so am signing off.  Thanks for all your help so far.  Also did you catch my comment about the other partition being my data?

---

### Post by caljohnsmith on 2009-02-17
> **newtel said:**
> The recovery disks I used were the ones I created when I bought the laptop.  They rarely provide disks when buying in the UK. When I installed ubuntu I believe that I created a 30 gig partition for it. Are these the missing gigabytes?   I would like to install as standard to a partition but I don't want to loose what I have. What danger of that?
If you will talk me through it with some instructions I would like to do it.   Have to go out now so am signing off.  Thanks for all your help so far.  Also did you catch my comment about the other partition being my data?
Yes, I definitely took note about the sda5 NTFS partition being your data partition. And yes, the 30 GB of unallocated space must be your missing gigabytes. I would suggest taking a look at this Ubuntu installation tutorial, because I think it has everything you need:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p24.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p24.html)

How about giving that try, and if you run into any problems or have questions, post back here.

---

### Post by newtel on 2009-02-18
> **caljohnsmith said:**
> 

How about giving that try, and if you run into any problems or have questions, post back here.


Hi
Haven't been brave enough yet to try installation but have read your link.  When I pluck up the courage this is how I think I will proceed.  Your comments would be gratefully received.

1) Run ubuntu from live cd.
2) Make copy of existing MBR as suggested to USB stick.
3) Install ubuntu.
4) When the process reaches the partition checking step I should see the missing 30 gig partition. Two questions. How can I force ubuntu to install to that particular partition?  Can I cancel all of the install process at this step if necessary?
5) Continue rest of install process (depending on your answer to the above questions). 
6) Either I will have dual boot functionality now or my original problem.
7) If a problem then boot using live cd and restore original MBR as suggested by your link.

Am I thinking along the right lines?  

Thanks in anticipation.

---

### Post by stalkingwolf on 2009-02-18
> 4) When the process reaches the partition checking step I should see the missing 30 gig partition. Two questions. How can I force ubuntu to install to that particular partition? Can I cancel all of the install process at this step if necessary?

You can cancel the install with no negative effects at any point up to
the time you click install (pg 7).

When you get to the partitioning stage select "Manual".
This should show you all of your available partitions.
Select/highlight the 30gb unallocated partition.  Select NEW.
It should show you have about 30720 mb ( maybe a bit less).
reduce this amount by about 1000mb.
On the right side select primary as type of partition.
EXT3 (or which ever you like ext2 or the new ext4 if avail.)
for mount point select /.
click ok.
this will leave you with 1000mb unallocated.
again highlight it  and select new.  Go to mount point and select
Linux Swap.  Click ok
after the partitioner finishes scanning your drive it will show you your 
new partition set up.  click next and you are on your way.

---

### Post by newtel on 2009-02-18
> **stalkingwolf said:**
> 
 click next and you are on your way.


thanks,

Will try.

---

### Post by newtel on 2009-02-18
> **stalkingwolf said:**
> 
  click next and you are on your way.


Hi stalkingwolf

Well I tried it.

I backed up my MBR.  Then started install.  When I got to using the free space to create a new partition it created OK. But when I tried to allocate the remaining space for Linux swap the option for new was not available it was greyed out and the remaining space was 'unusable'.  I tried again allowing a larger remaining space but still with the same result??.   Any ideas?

---

### Post by caljohnsmith on 2009-02-18
Instead of using the Ubuntu installer to create your partitions, how about using the Ubuntu partition editor (System > Admin > Partition Editor). Use that to create two logical partitions within your sda3 extended partition: one for your main Ubuntu install (formatted as ext3), and one for swap (formatted as swap). Once you have those two partitions set up, you can go through the Ubuntu installer and choose "manual" again for the partitioning method, and then simply use the partitions you set up. Let us know if that works OK.

---

### Post by newtel on 2009-02-19
> **caljohnsmith said:**
> Instead of using the Ubuntu installer to create your partitions, how about using the Ubuntu partition editor (System > Admin > Partition Editor). Use that to create two logical partitions within your sda3 extended partition: one for your main Ubuntu install (formatted as ext3), and one for swap (formatted as swap). Once you have those two partitions set up, you can go through the Ubuntu installer and choose "manual" again for the partitioning method, and then simply use the partitions you set up. Let us know if that works OK.

Hi

I've created the new partitions but not tried installing yet. I can still boot into vista. I have shown below the new results of 'boot info'.  They were not quite what i was expecting.





```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd1a0e96

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,467,135    21,465,088  27 Hidden HPFS/NTFS
/dev/sda2    *     21,467,136   231,841,102   210,373,967   7 HPFS/NTFS
/dev/sda3         231,850,080   488,392,064   256,541,985   f W95 Ext d (LBA)
/dev/sda5         295,226,568   488,392,064   193,165,497   7 HPFS/NTFS
/dev/sda6         231,850,206   291,242,384    59,392,179  83 Linux
/dev/sda7         291,242,448   295,226,504     3,984,057  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9C56A53156A50D58" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="648076D88076B062" TYPE="ntfs" 
/dev/sda5: UUID="01C96452189A21A0" TYPE="ntfs" 
/dev/sda6: UUID="0f93bc17-866e-45c1-933f-87210313c167" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="1be8ab57-9cce-4344-9910-0bf153918a2a" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda5

00000000  46 49 4c 45 30 00 03 00  58 59 35 04 00 00 00 00  |FILE0...XY5.....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  04 00 00 00 00 00 00 00  |................|
00000030  09 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  a0 21 9a 18 52 64 c9 01  a0 21 9a 18 52 64 c9 01  |.!..Rd...!..Rd..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 02 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  a0 21 9a 18 52 64 c9 01  |.........!..Rd..|
000000c0  a0 21 9a 18 52 64 c9 01  a0 21 9a 18 52 64 c9 01  |.!..Rd...!..Rd..|
000000d0  a0 21 9a 18 52 64 c9 01  00 70 00 00 00 00 00 00  |.!..Rd...p......|
000000e0  00 70 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.p..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  df 00 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 0e 00 00 00 00 00  |@...............|
00000130  00 00 0e 00 00 00 00 00  00 00 0e 00 00 00 00 00  |................|
00000140  12 dd 00 03 31 03 96 63  0d 00 01 00 00 c0 d4 8d  |....1..c........|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 03 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
00000180  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
00000190  11 01 02 31 01 c6 2b 01  00 00 01 00 00 90 cd 8d  |...1..+.........|
000001a0  ff ff ff ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 09 00  |................|
00000200
Unknown BootLoader  on sda7

00000000  11 11 11 11 11 11 11 11  11 11 11 11 11 11 11 11  |................|
00000010  11 11 11 11 11 70 00 11  11 11 11 11 11 11 11 11  |.....p..........|
00000020  11 00 01 11 11 11 11 11  11 11 11 11 10 03 33 01  |..............3.|
00000030  11 11 11 11 11 11 11 11  00 77 70 11 11 11 11 11  |.........wp.....|
00000040  11 11 11 11 03 38 83 30  11 11 11 11 11 11 11 10  |.....8.0........|
00000050  33 33 33 01 11 11 11 11  11 11 11 11 33 bb b8 33  |333.........3..3|
00000060  01 11 11 11 11 11 11 03  38 ff b3 01 11 11 11 11  |........8.......|
00000070  11 11 11 11 33 fb bb 83  30 01 11 11 11 11 10 33  |....3...0......3|
00000080  8f fb b3 01 11 11 11 11  11 11 11 11 33 ff bb b8  |............3...|
00000090  33 30 11 11 11 11 03 38  ff bb b3 01 11 11 11 11  |30.....8........|
000000a0  11 11 11 11 13 8f bb bb  83 33 01 11 11 10 33 8f  |.........3....3.|
000000b0  fb bb 33 01 11 11 11 11  11 11 11 11 13 3f fb bb  |..3..........?..|
000000c0  b8 33 30 11 11 03 38 ff  bb bb 30 11 11 11 11 11  |.30...8...0.....|
000000d0  11 11 11 11 11 38 fb bb  bb 83 33 01 10 33 ff fb  |.....8....3..3..|
000000e0  bb b3 30 11 11 11 11 11  11 11 11 11 11 33 ff bb  |..0..........3..|
000000f0  bb b8 33 30 03 3f fb bb  bb b3 31 11 11 11 11 11  |..30.?....1.....|
00000100  11 11 11 11 11 13 8f bb  bb bb 88 33 3b ff bf bb  |...........3;...|
00000110  bb b3 01 11 11 11 11 11  11 11 11 11 11 13 3f bb  |..............?.|
00000120  bb bb b8 83 8f ff fb fb  bb 33 01 11 11 11 11 11  |.........3......|
00000130  11 11 11 11 11 13 3f fb  bb bb bb 88 ff ff ff bb  |......?.........|
00000140  bb 30 11 11 11 11 11 11  11 11 11 11 11 11 38 fb  |.0............8.|
00000150  bb bb bb bb fb ff fb fb  b3 30 11 11 11 11 11 11  |.........0......|
00000160  11 11 11 11 11 11 33 ff  bb bb bb bb bf ff ff bb  |......3.........|
00000170  b3 31 11 11 11 11 11 11  11 11 11 11 11 11 13 ff  |.1..............|
00000180  bb bb bb bb fb fb fb fb  b3 01 11 11 11 11 11 11  |................|
00000190  11 11 11 11 11 11 13 8f  bb bb bb bb bf bf bf bb  |................|
000001a0  73 01 11 11 11 11 11 11  11 11 11 11 11 11 03 3f  |s..............?|
000001b0  bb bb bb bb bb fb fb fb  33 30 11 11 11 11 11 11  |........30......|
000001c0  11 11 11 11 11 00 03 3b  bb bb bb bb bf bf bf bf  |.......;........|
000001d0  83 33 01 11 11 11 11 11  11 11 11 11 10 03 3b bb  |.3............;.|
000001e0  bb bb bb bb bb fb fb fb  bb 33 30 11 11 11 11 11  |.........30.....|
000001f0  11 11 11 10 03 33 bb fb  bb bb bb bb bb bf bf bf  |.....3..........|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo/Log1: No such file or directory
```



I seem to have created sda6 and 7 for Linux and still have sda3 as extended but unallocated?   Can I still go ahead and try an install?

---

### Post by caljohnsmith on 2009-02-19
> **newtel said:**
> 
I seem to have created sda6 and 7 for Linux and still have sda3 as extended but unallocated?   Can I still go ahead and try an install?
It looks like you did a great job setting up the Ubuntu partitions; sda3 is the extended partition, and an extended partition is just a "container" for the all the logical partitions. So sda3 is not unallocated space, in fact it is completely full now with all three of your logical partitions. So bottom line, I would go ahead and try installing. :)

---

### Post by newtel on 2009-02-19
> **caljohnsmith said:**
> It looks like you did a great job setting up the Ubuntu partitions; sda3 is the extended partition, and an extended partition is just a "container" for the all the logical partitions. So sda3 is not unallocated space, in fact it is completely full now with all three of your logical partitions. So bottom line, I would go ahead and try installing. :)


I am at the install for manual partitioning.  There are a number of options.

I can highlight sda6 which is the partition I require. But do I edit partition or click on forward?   How do I tell the partitioner that sda3 is the one for installing linux?

Help!

---

### Post by caljohnsmith on 2009-02-19
> **newtel said:**
> I am at the install for manual partitioning.  There are a number of options.

I can highlight sda6 which is the partition I require. But do I edit partition or click on forward?   How do I tell the partitioner that sda3 is the one for installing linux?

Help!
You don't need to do anything with the sda3 extended partition, because it is not a "real" partition; it is just a conceptual container around your logical partitions. Therefore, just click on the sda6 partition, choose "edit", set the mount point as "/", and you don't have to check the format box. Then click your sda7 swap partition, click "edit", and then set its mount point as "swap". Finally, click proceed/forward.

---

### Post by newtel on 2009-02-19
> **caljohnsmith said:**
> You don't need to do anything with the sda3 extended partition, because it is not a "real" partition; it is just a conceptual container around your logical partitions. Therefore, just click on the sda6 partition, choose "edit", set the mount point as "/", and you don't have to check the format box. Then click your sda7 swap partition, click "edit", and then set its mount point as "swap". Finally, click proceed/forward.


After selecting edit and above mount point there is another option for 'use as'

What should I put in there as I can't select mount point till I make a decision.?

---

### Post by caljohnsmith on 2009-02-19
Specify "ext3" under "use as".

---

### Post by stalkingwolf on 2009-02-19
for SDA6 you want to "use as" /
for SDA7  "   '    "    "    swap

---

### Post by newtel on 2009-02-19
> **caljohnsmith said:**
> Specify "ext3" under "use as".

Apologies but,

sda6 type ext3 is now OK

But selecting sda7 type swap and clicking edit allows me to have swap area in the use as box but I cannot enter anything in the mount point?

---

### Post by sonu 1807 on 2009-02-19
there is no mount point for swap area,i.e. perfectly OK

---

### Post by newtel on 2009-02-19
> **sonu 1807 said:**
> there is no mount point for swap area,i.e. perfectly OK


Oh Dear.


Ubuntu 8.10 installed OK.   I shut down and turned on and selected windows/Longhorn.  Windows started to load but loaded recovery tools in what seems to be basic graphics??

I think this happened before and I then had to recover my vista back to factory settings.  Any ideas before I stop doing this?

I seemed to get two entries for windows longhorn. I click the first. Does that make a difference?

---

### Post by newtel on 2009-02-19
I am typing this on my  laptop using the live cd. Trying to boot this laptop gives me error 22 again. also I have done a boot info script again even though my keyboard seems to be screwed particulary the ~ key? 

I have posted the report below.  Any ideas before I recover vista using my recovery cd's and forget  ubuntu!!


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd1a0e96

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,467,135    21,465,088  27 Hidden HPFS/NTFS
/dev/sda2    *     21,467,136   231,841,102   210,373,967   7 HPFS/NTFS
/dev/sda3         231,850,080   488,392,064   256,541,985   f W95 Ext d (LBA)
/dev/sda5         295,226,568   488,392,064   193,165,497   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9C56A53156A50D58" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="648076D88076B062" TYPE="ntfs" 
/dev/sda5: UUID="01C96452189A21A0" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda5

00000000  46 49 4c 45 30 00 03 00  58 59 35 04 00 00 00 00  |FILE0...XY5.....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  04 00 00 00 00 00 00 00  |................|
00000030  09 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  a0 21 9a 18 52 64 c9 01  a0 21 9a 18 52 64 c9 01  |.!..Rd...!..Rd..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 02 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  a0 21 9a 18 52 64 c9 01  |.........!..Rd..|
000000c0  a0 21 9a 18 52 64 c9 01  a0 21 9a 18 52 64 c9 01  |.!..Rd...!..Rd..|
000000d0  a0 21 9a 18 52 64 c9 01  00 70 00 00 00 00 00 00  |.!..Rd...p......|
000000e0  00 70 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.p..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  df 00 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 0e 00 00 00 00 00  |@...............|
00000130  00 00 0e 00 00 00 00 00  00 00 0e 00 00 00 00 00  |................|
00000140  12 dd 00 03 31 03 96 63  0d 00 01 00 00 c0 d4 8d  |....1..c........|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 03 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
00000180  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
00000190  11 01 02 31 01 c6 2b 01  00 00 01 00 00 90 cd 8d  |...1..+.........|
000001a0  ff ff ff ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 09 00  |................|
00000200

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo/Log1: No such file or directory
```

---

### Post by newtel on 2009-02-19
Also if I go to computer from the live CD I can see and open the two drives with vista and my documents.  There surely must be a way of recovering without going back to the beginning?

---

### Post by sonu 1807 on 2009-02-19
I am using a HP lappy with Vista pre-installed. I was so fed up with vista that I just plunged into Ubuntu, without knowing what lies ahead. You at least have this forum to help. When I installed Ubuntu I was not aware that this forum existed. If nothing works... reinstall Vista using recovery CD... then under ubuntu use guided partitioning. One more thing, I suggest you to install ubuntu.kubuntu 8.04 (hardy) 32-bit (if you don't have over 4GB ram).

---

### Post by newtel on 2009-02-20
> **caljohnsmith said:**
> Specify "ext3" under "use as".


Well I am typing this on my laptop using vista.  Managed to fix boot problem by inserting windows recovery disk and using command line to 'bootrec.exe/fixmbr' and 'bootrec.exe/fixboot'.

The problem seems to be with grub. It doesn't like my vista configuration!

For now I am sticking with vista even though I have lost 30 gig of my hard drive to ubuntu which I cannot boot into.

Unless you know of a simple way to boot into ubuntu without causing my previous problems, mainly grub error 22.

Thanks to caljohnsmith and stalkingwolf and all for trying to help.

---


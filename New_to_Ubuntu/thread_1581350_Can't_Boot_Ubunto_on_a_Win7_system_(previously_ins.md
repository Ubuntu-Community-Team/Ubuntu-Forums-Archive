---
title: "Can't Boot Ubunto on a Win7 system (previously installed)"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by LinuxNow on 2010-09-24
Hi guys,
I'm new here and totally new with Linux.
I've been all day searching over the internet how to make my linux work.

I downloaded the liveCd and installed Ubuntu on a new IDE drive I had resting on my desk.
My pc was is running Win7 and dual booting with another XP os I had installed on the same disk.
Well, after I installed I rebooted as instructed and nothing happened. I got the same win7 dual boot screen to boot Win7 and XP but no Linux anywhere.
I've been reading and now I know that I had to install grub on the disk where win7 is running. But I didn't and I think it's better I didn't because **I want the Win7 to manage my booting options**. Is that possible??

I've tried everything. Downloaded EasyBCd and created a Linux entry and nothing happened. When I chose Linux boot then it restarted right away.

I've done the thing with the dd command and the bcdedit command and still nothing.

Can anybody help me having the Linux OS appear on the win7 booting options and that it actually runs??

Thanks!

---

### Post by mp035 on 2010-09-24
IIRC Windows bootloaders are a PITA in that they only boot microsoft operating systems.  The linux kernel needs a bootloader (grub or lilo) for the system to start.   The only option I can think of if you don't want grub to manage your booting is to specify the second hard disk as the first boot device in your bios.  You will have to change the boot options each time you want to boot a different os though.

BTW grub is quite good at managing boots, I use it even on windows only systems.  why do you want win7 to manage booting?

---

### Post by LinuxNow on 2010-09-24
Thanks for your reply.

Well, how do I make the grub to manage my booting?
But I still want to load the win7 by default after 5 seconds. Is that possible?

---

### Post by waynefoutz on 2010-09-24
> **LinuxNow said:**
> Thanks for your reply.

Well, how do I make the grub to manage my booting?
But I still want to load the win7 by default after 5 seconds. Is that possible?

yes it's possible. Boot up Ubuntu, click on System/Administration/Startup Manager. You can use this program to configure Grub any way you want.

You are going to have to install Grub first though. 
here's a guide.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

---

### Post by IcewindDale on 2010-09-25
Also, make sure you install it in the MBR - Master Boot Record - usually /dev/sda like stated in the guide waynefoutz linked and not inside any partition like /dev/sda1, /dev/sda2, etc.

---

### Post by LinuxNow on 2010-09-25
Ok guys thanks fortaking the time to help me :)
But please remember I'm completely new to Linux. I've been a Windows user all my life but I decided to try and learn the Linux world.
@IcewinDale: You mean I have to install Grub at the windows MBR? Would that affect the boot of win7 if for some reason I decide to uninstall Ubuntu?

My Ubuntu is installed on /dev/sda (sda1 actually) but the win7 is installed in /dev/sdb so where should I install it? I guess it's on /dev/sdb right?

---

### Post by LinuxNow on 2010-09-25
Now I have a bigger problem I think.

I started Ubuntu with the LiveCd and now there seem to be a problem with  the drive I have it installed. It-s not showing as a valid filesystem  or something :(
But yesterday I was able to see it when I started with liveCd.

I ran a script I found in another thread and here-s the resut on the file it generates.
Why so many errors? Please help me. I don't want to intall linux again, it took me almost two hours the first time :(

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   358,056,719   358,056,657   7 HPFS/NTFS
/dev/sdc2         358,056,720   625,137,344   267,080,625   f W95 Ext d (LBA)
/dev/sdc5         358,056,783   625,137,344   267,080,562   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        01C9E4345018BA80                       ntfs       INFORMACION                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6014638C1463644E                       ntfs       WIN XP                        
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        3A406A40406A02CD                       ntfs       WIN 7                         
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        62D4-EFCC                              vfat       NANDO                         
/dev/sdd: PTTYPE="dos" 
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/NANDO             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sdc1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda2: Input/output error
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

```

PS> btw, the Win7 is installed on /dev/sdc and not sdb :)

---

### Post by Mark Phelps on 2010-09-25
Piece of future advice you would do well to heed ...

Next time you want some MS Windows advice, go to the proper forum.

This is NOT an MS Windows forum; it is the Ubuntu forums.

Folks here will tell you how to use GRUB to boot different OS's -- which is fine if that is what you want to do.

If you want to use MS Windows to boot different OSs (and you CAN do that despite what folks here will tell you), then go to the Neo Smart Technology forums and read up on EasyBCD.  It is a free app they provide that allows you to modify the Windows boot loader configuration to add other OSs.  They also have some tutorials on how to do that.

---

### Post by LinuxNow on 2010-09-25
> **Mark Phelps said:**
> Piece of future advice you would do well to heed ...

Next time you want some MS Windows advice, go to the proper forum.

This is NOT an MS Windows forum; it is the Ubuntu forums.

Folks here will tell you how to use GRUB to boot different OS's -- which is fine if that is what you want to do.

If you want to use MS Windows to boot different OSs (and you CAN do that despite what folks here will tell you), then go to the Neo Smart Technology forums and read up on EasyBCD.  It is a free app they provide that allows you to modify the Windows boot loader configuration to add other OSs.  They also have some tutorials on how to do that.

Mark, I know where I am and I know exactly why I registered on this forum.
I'm not asking for windows advice. I came to a Ubuntu forum to ask for help on how to start up my ubuntu installation (which I wasn't able to do it)
Did you even read all the posts before you replied? I think in my second post after the reply from mp035 I decided to go with Grub and after that we were discussing How to install it and make it work on my desktop with a previously installed Win7.

You are right that people here will help me on GRUB and that's why they sent me to a manual to install GRUB and I was trying to do that but I found some problems while doing that so I came back for help.

I also said on my initial post that I already tried the EasyBCD thing and it wasn't working. Every time I tried to boot with the added boot option for Linux it just restarted.

I appreciate you took the time to read the thread and I would do it more if you can help a little here :)

---

### Post by LinuxNow on 2010-09-25
Anyways, last error I reported was because for some reason the BIOS did not recognized my Linux Disk when booting.
I had to open the pc and check the IDE and power cables to make sure it works.
Right now I just booted on the liveCd and will be doing the Grub installation.
I hope everything goes well and I will let you know how this ends.

If I finally manage to boot my linux installation I will be around while I lear everything about running a linux desktop :)

---

### Post by LinuxNow on 2010-09-25
Ok. Last update on my difficult task to make it.

I'm having problems starting my LiveCd.
It boots and then takes 20 minutes to show the system. I think it is supposed to show me the screen where I decide if I want to install or just try Ubuntu, but that never happens, it goes directly to the Ubuntu desktop after 20 minutes.

When the desktop starts it shows a crash report detected that says: "Sorry, the program "ubiquity-dm" closed unexpectedly.

I just close this. But when I want to see my drives it says I an not mount any of them :(
It gives me an error saying: "Unable to mount ...." "Not Authorized"
this happens with every drive.

When I go to the terminal and try to mount from there, the system blocks and shows a login screen asking for a password which I have no idea what it is :(
After that I can't do anything more than just restart the pc.

Anyone had this same problem or know why is this happening?

Before that happened I did the following in case it has some relation.

1) I opened my cpu and disconnected IDe cable and connected again. I changed the location of my SATA disks on the motherboard but after I started the pc I turned it off and changed them back as they were initially.  

2) then I tried to start the linux installation by changing the boot order on the BIOS and placing the drive with linux as the first booting device. It didn't worked by the way. Didn't boot. It showed the GRUB starting options but when I chose Linux it found some error and never started :(

What to do??? I'm really lost here.

---

### Post by Mark Phelps on 2010-09-27
You have my apologies, really.  I misread your posts (obviously) and was only trying to prevent you from getting bad info.

I'm not saying folks here intend to harm anyone, quite the contrary.  But I've seen more than one post regarding EasyBCD where the folks here provided bad info that only made the situation worse.

But ... glad to see you got it working anyway.

---

### Post by LinuxNow on 2010-09-27
Thanks Mark.

Well I indeed solved my problem by having to reinstall Ubuntu again and placing the Grub boot on the win7 disk so it took control of the booting process.

Right now I just don't know where to edit Grub options to lower the time to autoboot the default option and how to make the win7 the default option.
:(

---

### Post by IcewindDale on 2010-09-27
Grub's settings are now in /etc/default/grub. Edit that file, specifically the "GRUB_TIMEOUT=X" where X is the number of seconds you want to wait till it autoboots and "GRUB_DEFAULT=X" where X is the default choice when you enter grub's screen (if Windows is in the 4th position from the top then X=4). After that run "sudo update-grub" and you're done.

Alternatively you can install "startup-manager" (sudo apt-get install startupmanager) and in the menu under System->Administration you'll have a graphical tool for this called StartUp-Manager. Not sure this comes in the default installation or if you have to install it yourself, check the menu before trying to install it.

---

### Post by LinuxNow on 2010-09-28
Thanks!
I will do that ASAP :)

Once I get the booting done I'll start searching the forums to begin my learning on Ubuntu and Linux in general.

Would you recommend any place specifically to begin with?

Do you know of any good beginner book or e-book for Ubuntu or Linux?

---

### Post by LinuxNow on 2010-09-28
Never mind!

I just saw the sticky thread about being new to Ubuntu. 
I'll start eating all that material :D

---

### Post by mcgama88 on 2010-09-30
hi from wa state.
 
I also am new to the linux state of the art but I have a suggestion.  I also have begun to become used to linux.  I am using the knoppix disc to begin.  This works very well in the windows environment because:
 
The disk boots without any interfereence with the windows environment.
 
You can easily return to windows with close.
 
I am in a similar condition as yourself in that I am neww to the install of commands and files that will better interface the multiple os.

---


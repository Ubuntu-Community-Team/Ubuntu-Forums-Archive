---
title: "Error 15: File Not Found"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Grendel336 on 2009-03-05
I have a dual boot set up. Windows Vista and Ubuntu 8.10. 

Dell Inspiron E1505 laptop. Basic model. 

Here's the message I get when I try to boot into Ubuntu:

> Find --set-root--ignore-floppies  /ubuntu/install/boot/grub/menu.lst

Error 15: file not found

I am a serious novice with all this. I have the original boot disk I burnt over a year ago. It's the 8.02 version. I hate the idea of re-installing, and I'm sure there's a way to fix this issue but I don't know how. 

I'd appreciate some help, and I apologize before hand for my lack of working knowledge. I may ask many questions once somebody responds.

---

### Post by cariboo on 2009-03-05
Its seem that something overwrote your master boot record. Follow this [thread=224351]howto[/thread] to repair your problem.

Jim

---

### Post by Grendel336 on 2009-03-05
Thanks. I went to the thread you linked and followed the instructions in the first post of that thread. 

I booted to my install disk. Opened a terminal, and typed in the commands as they were posted. 

I kept getting the Error 15: file not found message.

Or simply the "file not found" message depending on which command I typed. 

Bottom line is nothing from the first post worked for me. 

That thread is almost 100 pages long. 

Not sure what to do now. Any ideas?

---

### Post by louieb on 2009-03-05
Did you install using WUBI? (inside windows). If you can - boot to the Ubuntu live CD download this script  [SourceForge.net: Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") to your desktop.

then from a terminal window run.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Ubuntu.

The script was written by a couple of regulars in the forum.

---

### Post by Grendel336 on 2009-03-07
Thanks. I shall give it a try. I've not had success in the past getting connected to internet from boot disk.

---

### Post by louieb on 2009-03-07
If the information in the file doesn't help you figure it out. You can copy the RESULTS.txt file to a USB stick. And post it from a computer with internet access. Good Luck.

---

### Post by Grendel336 on 2009-03-07
Alright....from Windows to USB stick, to Ubuntu CD boot, to desktop, to Terminal, back to USB stick, and now back to Windows....

> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,084,160   230,244,351   209,160,192   7 HPFS/NTFS
/dev/sda4         230,244,352   234,438,655     4,194,304   f W95 Ext d (LBA)
/dev/sda5         230,246,400   234,438,655     4,192,256  dd 

/dev/sda4 ends after the last cylinder of /dev/sda
/dev/sda5 ends after the last cylinder of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,935,999     7,927,936   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0510" TYPE="vfat" 
/dev/sda2: UUID="12BA6165BA614677" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="863864E53864D629" LABEL="OS" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="A269-15ED" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="A8E6-39B6" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


======================== sda3/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

================================ sda5/BOOT.INI: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768



You people are the greatest. Thanks.

---

### Post by louieb on 2009-03-09
Looks like you have a wubi install. Also looks like your dual booting XP and Vista. was Ubuntu installed inside XP or Vista?  

Anyway there might be something on repairing your boot problem in the [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I'm not going to be able to help.So heres a bump. Maybe some one whos done a WUBI install will come along.

---

### Post by Grendel336 on 2009-03-09
As it was explained to me in the past, I do not have a WUBI install. 

I have a dual boot system. 

Window's Vista is other OS. 

When I first turn on laptop I get a boot screen where I can pick either a Vista boot, or Ubuntu boot.

---

### Post by davidryder on 2009-03-09
You have a Wubi install if you installed Ubuntu from inside of Windows.

---

### Post by Grendel336 on 2009-03-09
I shall look through the WUBI repair instructions when I get home and can access my laptop. 


Worst comes to worst, I'll do a reinstall again...I just hate having to do that, but I'd rather run Ubuntu than Vista any day.

Thanks guys....

---

### Post by davidryder on 2009-03-09
To be honest - in my humble opinion - Wubi is a less optimal installation. It is a bit slower than running it natively on its own filesystem and if something happens to your Windows install then you are going to be faced with problems wtih your Ubuntu install. 

In a perfect world (if I had a dual-boot system) Ubuntu would go on a 80gb drive, Windows would go on a second 80gb drive, and they would both share files (music, pictures, documents, etc) on a third 500gb+ drive. :D

---

### Post by Grendel336 on 2009-03-09
Yes. I fully believe my problems have to do with Windows moving some file, or files without my knowing it, and without my prompting it. 

Why would Ubuntu run perfectly for months on end, booting and shutting down every single day without problems, only to one day have a boot-up problem of this nature? 

Hopefully the WUBI repair suggestions can help me. 

One day soon I shall have a laptop with it's one and only OS being Ubuntu. That will be a great day in my opinion.

---

### Post by Ravernomina on 2009-03-09
If i were u my friend, do it now. You can simply just emulate Windows Vista/XP in virtual Box when ever you need a Windows machine needed. I'm glad ur problem is also sloved

      Ravernomina

P.S. This is my favorite quote "A computer is like an air conditioner, Everything runs fine till you open Windows....":lolflag::lolflag::lolflag:

---

### Post by Grendel336 on 2009-03-09
I ran chkdsk and nothing changed. I restored to a point when I know Ubuntu was running fine and nothing has changed. 

When I try to boot into Ubuntu I get the Error 15 message I posted earlier. 

then there's a prompt to hit any key...when I do that a screen pops up that says:

> Grub4DOS 0.4.3 2008-04-22 Memory: 636k / 2045M, CodeEnd: 0x41228

(then I have 8 choices I can make by using the up or down arrow keys)

Find /ubuntu/disks/boot/grub/menu.lst
Find /ubuntu/install/boot/grub/menu.lst
Find /menu.lst
Find /boot/grub/menu.lst
Find /grub/menu.lst
Command Line
Reboot
Halt


When I pick and of the "Find..." options I end up back at the Error 15 screen. 

Can I search the Live CD for any of those files and simply copy those to my Ubuntu directory?

---


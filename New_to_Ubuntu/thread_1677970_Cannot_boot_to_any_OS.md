---
title: "Cannot boot to any OS"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by Indev on 2011-01-29
Hello everyone, I'm new to ubuntu and barely installed it 2 days ago. The first time I did this it was working fine, I used a wubi installer, but then noticed that I partitioned a small amount of memory for Ubuntu, 17 GB. Thus, I unistalled it and reinstalled to the maximum I could have selected, 30 GB. Upon doing that I was asked to update Ubuntu, so I did, and when I asked my to restart my computer I was sent to the grub rescue prompt:
 
error: no such device: 205e953e-f148-4fe0-b798-46bad950364a
grub rescue>
 
I tried the ls command and only recived (hd0). Having already looked through the forums I've been able to understand that this might be a disk error problem and the MegaThread for Wubi and grub rescue could not help me.
 
I can't access any OS system. I installed Ubuntu via Window XP. I have an Asus Eee 1005HA. I have a LiveUSB but since I can't even access Ubuntu I can't try and reinstall GRUB. 
 
Any help would be much appreciated. Thanks.

---

### Post by sikander3786 on 2011-01-29
Welcome to the forums :-)

Please see problem # 1 here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Once you are done, apply the Permanent Fix from that page to save you troubles later.

---

### Post by Indev on 2011-01-29
I have a LiveUSB but since I'm stuck at the grub rescue prompt I can't actually run the program on it since I can't access the Ubuntu terminal. Is my only option to try and get my hands on a Windows CD, I don't have one so that is why I'm trying to use the LiveUSB.

---

### Post by sikander3786 on 2011-01-29
> **Indev said:**
> I have a LiveUSB but since I'm stuck at the grub rescue prompt I can't actually run the program on it since I can't access the Ubuntu terminal. Is my only option to try and get my hands on a Windows CD, I don't have one so that is why I'm trying to use the LiveUSB.
Are you sure you chose your Live USB as the first boot device in Bios menu or Quick boot menu?

---

### Post by Indev on 2011-01-29
Honestly, I do know which one I did. When I was at the Wubi forum, the same one you a first told me to go to, it said that I might need a LiveUSB so I followed the link at obtained the file and put it onto my USB but that's as far as I go/know. If there is some additional stuff I need do do can you tell me what that is? 
 
I'm very much new to all of this so my understanding is fairly low.

---

### Post by sikander3786 on 2011-01-29
> **Indev said:**
> Honestly, I do know which one I did. When I was at the Wubi forum, the same one you a first told me to go to, it said that I might need a LiveUSB so I followed the link at obtained the file and put it onto my USB but that's as far as I go/know. If there is some additional stuff I need do do can you tell me what that is? 
 
I'm very much new to all of this so my understanding is fairly low.
How was the USB prepared? I would recommend to use UNetbootin. Follow the link below for instructions please.

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

---

### Post by Indev on 2011-01-29
Alright, I'm doing as you advised. Once I have the USB ready what do I do with it, connect it to my laptop and see if it runs while the grub rescue prompt is still up?

---

### Post by sikander3786 on 2011-01-29
> **Indev said:**
> Alright, I'm doing as you advised. Once I have the USB ready what do I do with it, connect it to my laptop and see if it runs while the grub rescue prompt is still up?
Once the USB is prepared, plug it in and from Bios menu or Quick Boot menu, choose your USB device as the first boot device. Then, if you boot successfully from the USB drive, you won't see the Grub rescue prompt. Instead, it would boot to a Live Session of Ubuntu running directly from the USB drive. Then you can follow the commands in the link in my above post.

---

### Post by Indev on 2011-01-29
> **sikander3786 said:**
> Once the USB is prepared, plug it in and from Bios menu or Quick Boot menu, choose your USB device as the first boot device. Then, if you boot successfully from the USB drive, you won't see the Grub rescue prompt. Instead, it would boot to a Live Session of Ubuntu running directly from the USB drive. Then you can follow the commands in the link in my above post.
 
Ok I understand that but how do I access the Bios menu or the Quick boot menu if the laptop in question won't go past the grub rescue prompt. Is there a set of commands that I have to input in order for the computer to boot. (Just in case the computer that I am using right now is not the one with the issue. That one won't enter into any OS.)

---

### Post by sikander3786 on 2011-01-29
Bios screen comes before the grub rescue prompt. As soon as you press the power button, the computer boots to Bios and then to Grub (in your case). There would be a shortcut key for accessing the Bios menu or Quick boot menu. It might be F2, F10, Del, Enter or some other. You need to refer to your Laptops manual for more details.

Or let us know which make/model is it and we might be able to find it out for you.

Once you find out the key, power on or reboot your Laptop and keep on tapping that specific key until you get to the Bios menu. It has nothing to do with Grub rescure prompt.

---

### Post by Indev on 2011-01-29
> **sikander3786 said:**
> Bios screen comes before the grub rescue prompt. As soon as you press the power button, the computer boots to Bios and then to Grub (in your case). There would be a shortcut key for accessing the Bios menu or Quick boot menu. It might be F2, F10, Del, Enter or some other. You need to refer to your Laptops manual for more details.

Or let us know which make/model is it and we might be able to find it out for you.

Once you find out the key, power on or reboot your Laptop and keep on tapping that specific key until you get to the Bios menu. It has nothing to do with Grub rescure prompt.

Ok I'm actually on the laptop that had the problem. Used the LiveUSB and the instructions of the website given to actually be able to run the bootloader. Ok, now that I'm in Ubuntu, I seem to not actually be the administrator and am just viewing my own page as a guest or something. What do I do to make sure that the bootloader is completely in the system and that this won't happen again?

---

### Post by sikander3786 on 2011-01-30
For the files that are owned by 'root', you'll not be able to access them without sudo. sudo gives you root privileges for time being. All files in your /home directory are owned by you and you can access them without sudo.

You need to be careful with sudo thing and make sure you don't delete or modify any files accidently or you might do some damage to your system. If you want to access some root files/directories, press Alt + F2 and type

```
gksudo nautilus
```

It would ask for your password and you'll gain root privileges. For more info, see here.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Indev on 2011-01-30
> **sikander3786 said:**
> For the files that are owned by 'root', you'll not be able to access them without sudo. sudo gives you root privileges for time being. All files in your /home directory are owned by you and you can access them without sudo.

You need to be careful with sudo thing and make sure you don't delete or modify any files accidently or you might do some damage to your system. If you want to access some root files/directories, press Alt + F2 and type

```
gksudo nautilus
```It would ask for your password and you'll gain root privileges. For more info, see here.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ok I see what the root is but I mean I have a profile in Ubuntu before all of this happened and now when I enter the terminal I get ubuntu@ubuntu rather than my own profile name. How do I go back and be able to access that account. 

I tried restarting my computer and the only way I wouldn't get to the grub rescue prompt was using the LiveUSB so again, soory if I'm sounding repetitive, how do I fix Ubuntu with the grub bootloader. 

Also, when I restarted I wasn't given a choice on which OS I wanted to start. How can I get the choice back because I feel like this whole grub affair is because of GRUB2 being in beta and I'd simply rather go to the previous version just so that I can learn about Linux rather than having to deal with problems like this. I want to try and access my Windows OS so I can unistall Ubuntu and then get an older version.

---

### Post by wilee-nilee on 2011-01-31
So you ran the lilo install correct?

If so it sounds like you installed lilo to the thumb, Do you get the MS bootloader gui to choose XP or Ubuntu?

Grub is not the problem other then you allowed a upgrade of it in wubi this overwrote the ms bootloader.

When you did the lilo install did you run the 
sudo fdisk -l
command to confirm the HD letter, for example sda, or sdb? When you boot from a thumb sometimes the third letter gets reversed=sd**a**, or sd**b**

---

### Post by Rubi1200 on 2011-01-31
Indev,

Wubi installs cannot be booted from a grub rescue prompt.

Do NOT try and install GRUB to the MBR; Wubi installs cannot be booted from the MBR.

With so many changes going on, I recommend you do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we see the results it will be a lot easier to help you.

---

### Post by Indev on 2011-01-31
@Rubi1200

I did as you asked and here is the RESULTS.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   151,123,454   151,123,392   7 HPFS/NTFS
/dev/sda2         151,123,455   302,230,844   151,107,390   7 HPFS/NTFS
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       205e953e-f148-4fe0-b798-46bad950364a   ext4                                     
/dev/sda1        4A30C94A30C93E27                       ntfs                                     
/dev/sda2        A000B2F200B2CF12                       ntfs                                     
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A973-6E52                              vfat       USB Disk                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu"
```

---

### Post by theozzlives on 2011-01-31
If your running WUBI via Windows XP, you should be able to boot your Windows CD; goto recovery mode; and do:
```
fixmbr
fixboot
```
your boot.ini shouldn't be affected as that's where the Ubuntu option is.

There's a problem updating GRUB within WUBI.

---

### Post by Indev on 2011-01-31
> **theozzlives said:**
> If your running WUBI via Windows XP, you should be able to boot your Windows CD; goto recovery mode; and do:
```
fixmbr
fixboot
```your boot.ini shouldn't be affected as that's where the Ubuntu option is.

There's a problem updating GRUB within WUBI.

I don't have a Windows Recovery CD. At this point I just want to uninstall Ubuntu and just go back to Windows so I can get a more stable version of Ubuntu.

---

### Post by mastablasta on 2011-01-31
> **Indev said:**
> Ok I see what the root is but I mean I have a profile in Ubuntu before all of this happened and now when I enter the terminal I get ubuntu@ubuntu rather than my own profile name. How do I go back and be able to access that account. 
 

 
that is OK. This happens when you run live session. You see, in live session everyhting loads to RAM so it doesn't affect anything that is already on your hard disk. it's like a separate operating system that is only living in RAM. when you turn it off all changes made will be gone. unless you fiddle with any files on your hard disk.
Which is exactly what needs to be done in your case and you were already told this.:
[http://ubuntuforums.org/showpost.php?p=10409599&postcount=2](http://ubuntuforums.org/showpost.php?p=10409599&postcount=2)
 
 
If you manage to fix this issue i would suggest a propper install to separate disk partition (not virtual file like wubi) as it will likely have far less issues.
 
I wonder why instal porcedure for wubi doesn't atomaticly disable grub updates if they tend to mess it all up for users who want to try the OS and play arround with it?

---

### Post by theozzlives on 2011-01-31
> **Indev said:**
> I don't have a Windows Recovery CD. At this point I just want to uninstall Ubuntu and just go back to Windows so I can get a more stable version of Ubuntu.

Here's a Recovery Console to run the above commands.

 
[http://www.webtree.ca/windowsxp/repair_xp.htm]("http://www.webtree.ca/windowsxp/repair_xp.htm")

---

### Post by runeh76 on 2011-01-31
Can u now when u are here, download example ubuntu 10.10 to ur usb? Burn it and u can make a nice new clean install.

---

### Post by Rubi1200 on 2011-01-31
Indev,
the problem is this:
> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

Wubi installs cannot be booted from the MBR; it will fail.

The solution, as theozzlives already indicated, is to restore the Windows bootloader.

If you are unable to get hold of a Windows CD, there is a fix that can be done from the Ubuntu LiveCD.

To restore a Windows-like bootloader:

```
sudo apt-get install lilo

sudo lilo -M /dev/sda mbr
```

You may have to enable the repositories first using ```
sudo apt-get update
``` before running the commands above.

When you do run them, ignore any warnings because we just want lilo installed in the MBR.

Once you can boot Windows again, we need to take care of the other problem:

The failed mount on sda2 and sda4.

If you need more help, let me know.

---

### Post by Indev on 2011-01-31
Ok taking all of the things said I have FINALLY been able to get the lilo bootloader up and am now in windows. I still want to try Linux however so, hopefully my last questions, which version of Ubuntu would have a stable, basically GRUB legacy or the like, bootloader/not GRUB2.

---

### Post by Rubi1200 on 2011-01-31
Excellent! I am really glad you got up and running again :-)

GRUB2 is not a problem, per se, nor is Wubi. The issue, or part of it, that you experienced has to do with Wubi installs being affected by GRUB updates despite the fact that Wubi does not rely on GRUB.

In my opinion, you have 2 options:

1. install Wubi and lock the grub packages to prevent this happening

2. do a proper install to the hard-drive; all versions of Ubuntu from 9.10 onwards use GRUB2

---

### Post by Indev on 2011-01-31
> **Rubi1200 said:**
> Excellent! I am really glad you got up and running again :-)

GRUB2 is not a problem, per se, nor is Wubi. The issue, or part of it, that you experienced has to do with Wubi installs being affected by GRUB updates despite the fact that Wubi does not rely on GRUB.

In my opinion, you have 2 options:

1. install Wubi and lock the grub packages to prevent this happening

2. do a proper install to the hard-drive; all versions of Ubuntu from 9.10 onwards use GRUB2

Alright well thanks to everyone for their input. I re-installed Ubuntu 10.4 (the one that was giving me problems) but took the advice and turned off the update. I will work with this and if it doesn't mess up again then I'm sticking with it. If not then I'll just go to a version lower than 9.10. 

THANKS!!!

---


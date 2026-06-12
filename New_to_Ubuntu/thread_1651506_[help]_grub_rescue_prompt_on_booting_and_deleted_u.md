---
title: "[help] grub rescue prompt on booting and deleted ubuntu folder"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by grubrescue on 2010-12-23
hi everyone,
i am an absolute beginner on ubuntu. i m a windows user. now here is my problem:

i was using windows 7 64-bit when one of my friends gave me an ubuntu 10.04 cd to try it out. i installed ubuntu 10.04 from within my windows 7 on my E: drive(win7 was in C: drive). 

After complete installation of ubuntu an UPDATE MANAGER window opened up and told me to update my 'packages'. i clicked on Install updates... around 250mb of packages got downloaded and started installing on my machine. During the installation a window opened up asking me whether to install  GRUB-PC ? i installed GRUB-PC and checked some device that it showed in the wizard. After installation completed i restarted my laptop and on restarting i am getting grub-rescue prompt :( 

i am new to ubuntu and did not knew what to do and there was no option coming up except that grub rescue> prompt. I was taken aback and so i again put in the ubuntu 10.04 cd and clicked on TRY UBUNTU...it worked... so i THOUGHT THAT DELETING THE UBUNTU FOLDER IN MY E: DRIVE MIGHT SOLVE MY PROBLEM. so i deleted the ubuntu folder from my E: drive and restarted but nothing better happened and i am still stuck on grub rescue prompt. I even tried repairing using the windows7 dvd but nothing is happening. Please help me guys there are a lot of data and applications installed on my windows 7... i dont care about the ubuntu... i just want to run my windows 7 as before without the risk of formatting :( :( can anybody help? i'm getting very tense :( i also tried searching in the forum but nobody seems to have DELETED THE UBUNTU FOLDER... on trying the ls command on grub-rescue i get something like (hd,0) and nothing else. no other command i know works on that damn grub rescue prompt. Please some1 help me out. I just want to run my windows 7 again properly and i am a beginner in ubuntu so please talk in some general terms so that i can understand... HELP!

---

### Post by Hippytaff on 2010-12-23
Hi and welcome. For wubi troubleshooting this is the best resource - if you get stuck post there and Rubi1200 et al will assist :-)
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
Edit -> actually, before that I should check you have a wubi install. Can you boot from liveCD, select try ubuntu and download and run the script from here -http://sourceforge.net/projects/bootinfoscript/
Then can you post the results.txt so we know exactly whats gonig on :-)
 
but the most likely explanation is probably down to the fact that grub updates don't sit well with Wubi.

---

### Post by Elfy on 2010-12-23
> **Hippytaff said:**
> Hi and welcome. For wubi troubleshooting this is the best resource - if you get stuck post there and Rubi1200 et al will assist :-)
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
Edit -> actually, before that I should check you have a wubi install. Can you boot from liveCD, select try ubuntu and download and run the script from here -http://sourceforge.net/projects/bootinfoscript/
Then can you post the results.txt so we know exactly whats gonig on :-)



> so i THOUGHT THAT DELETING THE UBUNTU FOLDER IN MY E: DRIVE MIGHT SOLVE MY PROBLEM. so i deleted the ubuntu folder from my E: drive 

would imply that it's gone.

@grubrescue - you need to reinstall your windows bootloader - however that is achieved nowadays.

Unless you've deleted things you shouldn't have your data is still there.

[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

at the end of that post - recovering win7 bootloader

---

### Post by grubrescue on 2010-12-23
thanks for replying...

i would like to remind that i have DELETED MY UBUNTU FOLDER so these might b the values from the ubuntu live cd? excuse me if that sounds stupid..

HERE IS THE CONTENT OF THE RESULTS.txt

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   628,152,319   627,742,720   7 HPFS/NTFS
/dev/sda3         628,152,320 1,250,050,047   621,897,728   f W95 Ext d (LBA)
/dev/sda5         628,154,368   837,869,567   209,715,200   7 HPFS/NTFS
/dev/sda6         837,871,616 1,047,586,815   209,715,200   7 HPFS/NTFS
/dev/sda7       1,047,588,864 1,250,050,047   202,461,184   7 HPFS/NTFS
/dev/sda4       1,250,050,048 1,250,261,679       211,632   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2E2E4FD72E4F972D                       ntfs       SYSTEM                        
/dev/sda2        3018E39B18E35E7A                       ntfs       FUN                           
/dev/sda3: PTTYPE="dos" 
/dev/sda4        3E25-563B                              vfat       HP_TOOLS                      
/dev/sda5        869ACE5F9ACE4AFF                       ntfs       DATA                          
/dev/sda6        208C05B68C05880C                       ntfs       STUDIES                       
/dev/sda7        505826105825F57E                       ntfs       GAMES n PICS                  
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by Hippytaff on 2010-12-23
> **forestpiskie said:**
> Please read the whole of a post ;)
 
 
 
would imply that it's gone.
 

 
Good point :? my bad, I tend to skim read long posts, information overload - no excuse. Consider me repramanded

---

### Post by Hippytaff on 2010-12-23
> **grubrescue said:**
> thanks for replying...
 
i would like to remind that i have DELETED MY UBUNTU FOLDER so these might b the values from the ubuntu live cd? excuse me if that sounds stupid..
 

 
I apologise, I'm the stupid one :? see above :roll:
 
I should change my name to Donkey :-)

---

### Post by kansasnoob on 2010-12-23
Using the Ubuntu Live CD simply run these two commands:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

That should get Windows booting again.

Then, before trying a Wubi install again, be sure to read this:

[http://ubuntuforums.org/showpost.php?p=10207564&postcount=1](http://ubuntuforums.org/showpost.php?p=10207564&postcount=1)

---

### Post by grubrescue on 2010-12-23
> **forestpiskie said:**
> would imply that it's gone.

@grubrescue - you need to reinstall your windows bootloader - however that is achieved nowadays.

Unless you've deleted things you shouldn't have your data is still there.

[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

at the end of that post - recovering win7 bootloader
thanks [[COLOR=#D40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428")...

it worked.. thanks a lot :)

thanks hippytaff... n no u r cant b stupid :P


@kansasnoob thanks but [[COLOR=#D40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428")'s method already worked :)

thanks for all the help guys :-)

---

### Post by theasprint on 2010-12-23
Hi,

To forestpiskie:
Just for learning, to identify if a Wubi installation exists, I should find /wubildr.mbr and /wubildr right?
And what is in /sda5, /sda6 and /sda7? Is it the partition for the Wubi install? Mainly root, /home and swap?

---

### Post by Rubi1200 on 2010-12-23
You should read the thread kansasnoob linked to; it will help you understand the issues with Wubi installs at the moment and there is also advice on how to prevent these problems from occurring.

Thanks.

A general plea to those reading this post: 
Those who want to help with Wubi installs; please read the Wubi Megathread to understand what to do in these situations.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---


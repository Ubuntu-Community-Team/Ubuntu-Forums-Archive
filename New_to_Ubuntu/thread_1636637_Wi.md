---
title: "Wi"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by insectatorious on 2010-12-03
Hi, 
   I'm pretty new to Ubuntu so I would appreciate everyone treating me  like a complete newbie. Earlier today I installed Ubuntu 10.10 on my  desktop. It is not the standard desktop edition, but a modified edition  that is provided by [http://www.linuxformat.com/](http://www.linuxformat.com/). 

I've been searching the forums for similar posts and have found many such threads. None however deal with my problem.

I had Windows 7 Business Edition 64-bit installed first. Next I  installed Ubuntu 10.10 from the aforementioned source. After the  installation was complete, I restarted my desktop and found that on the  GRUB menu I don't have a Windows option. Only Ubuntu appears.


I read on a forum somewhere that I need to run the Win7 Repair disc in order to fix the problem. I downloaded the disc and burnt it. While trying to run the repair procedure, I found something alarming: the repair disc detected a windows installation on D: drive when I have windows installed on C: drive. As there was nothing I could do about this, I went ahead and tried the repair three times without any luck. Then I tried a System Restore from yesterday - just before I started to install Ubuntu. While I still don't have a windows option on the GRUB menu, I can now mount my windows NTFS partitions from within Ubuntu. This was not possible before the System Restore.

I have included below the results from the boot_info_script (RESULTS1.txt).

---

### Post by Quackers on 2010-12-03
Welcome to UF.
When booted into your Linux system have you tried running sudo update-grub in a terminal and watching to see if Windows Loader is picked up during the configuration of grub.cfg ?

Also please copy/paste the contents of your results.txt file betwqeen code tags (either by using the # key in New Reply toolbar or by preceding the text with [code ] (without the space before the ] )and then putting [/code] after the pasted text).

---

### Post by insectatorious on 2010-12-03
Thanks.

Results of sudo update-grub:

```
Generating grub.cfg ...
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found memtest86+ image: /boot/memtest86+.bin
done

```and the results of the boot_info_script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1953519615 sectors, but according to the info from 
                       fdisk, it has 1953520001 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   104,859,647   104,652,800   7 HPFS/NTFS
/dev/sda3         104,859,648   493,563,903   388,704,256   7 HPFS/NTFS
/dev/sda4         493,565,950   703,281,151   209,715,202   5 Extended
/dev/sda5         493,565,952   495,564,799     1,998,848  82 Linux swap / Solaris
/dev/sda6         495,566,848   703,281,151   207,714,304  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        58A0AA10A0A9F522                       ntfs       System Reserved               
/dev/sda2        2690DDA890DD7F2D                       ntfs                                     
/dev/sda3        F8E6B659E6B617B8                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        341d3466-ce9a-4747-8fac-5e72b2bfebd1   swap                                     
/dev/sda6        e6b8f55c-3929-4bfb-ba7f-0db4ff7f5522   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14103C70103C5AC6                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/F8E6B659E6B617B8  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=================== sda6: Location of files loaded by Grub: ===================


 327.0GB: boot/grub/core.img
 327.0GB: boot/grub/grub.cfg
 254.5GB: boot/initrd.img-2.6.35-23-generic-pae
 327.0GB: boot/vmlinuz-2.6.35-23-generic-pae
 254.5GB: initrd.img
 327.0GB: vmlinuz


```

looks like Win7 wasn't picked up...did a restart to check the GRUB menu without any luck.

---

### Post by Quackers on 2010-12-03
Obviously your system seems to have a problem with sdb (your 1TB drive) and it may possibly be better for you to disconnect it until these problems are sorted out.
Some bioses aren't up to dealing with drives so large.
As for Windows, I see no problems at all with either your partitions or the boot files for Windows or Ubuntu.
I don't know why grub is not picking up your Windows system. It may be that one of its boot files has been slightly over-written or damaged. That's just a guess.
It may be that Windows would become bootable by running the Startup Repair function of a Windows repair cd (up to 3 times). This would, however, over-write grub, which would need to be re-installed later.
It may be worth while waiting for other people's input on this before taking any further action as it's possible I have missed something. That's happened before :-)

---

### Post by karthick87 on 2010-12-03
Try re-installing your grub,

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot your system and then run,
```
sudo update-grub
```

---

### Post by Quackers on 2010-12-03
Oops, I'm a dope :-(
Karthick87's suggestion should have been the first thing I suggested. That could well resolve the Windows 7 issue - hopefully :-)

Actually your boot script looks to have been truncated. Did you fail to copy the full file?

---

### Post by insectatorious on 2010-12-03
> **karthick87 said:**
> Try re-installing your grub,

```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```Reboot your system and then run,
```
sudo update-grub
```

I completed the first two steps and now I don't get anything from grub. No menu, no ubuntu login screen, just the following instead:
```
error: File not found
grub rescue>
```> **Quackers said:**
> Oops, I'm a dope :-(
Karthick87's suggestion should have been the first thing I suggested. That could well resolve the Windows 7 issue - hopefully :-)

Actually your boot script looks to have been truncated. Did you fail to copy the full file?

I did indeed remove some of the stuff from the page as I thought it looked to be related to the hardware side of the HDD. As stated above, I'm now unable to access anything on my machine thanks to the steps I followed so unless you read the attachment on my original post I can't show you the complete output.

Thanks.

---

### Post by karthick87 on 2010-12-03
@Quackers i cant guess what's going wrong with @insectatorious system?

---

### Post by Quackers on 2010-12-03
Me neither :-)
If you will boot from the live cd and select "try ubuntu" then make sure you have an internet connection I would appreciate you running the boot script again please, and please include it all this time.
TBH I don't expect to see anything wrong, it's just for confirmation purposes.

In my (limited) experience, it seems to me that there are 2 reasons for grub not finding another OS. The first is that the 30_os-prober is not running for some reason (which would be confirmed with the rest of the boot script output), or the boot files for the other OS are not present or readable.

There are still things we can try though. If all else fails we can try to repair the Windows bootloader again, to confirm that Windows will still boot. If it won't boot we could try moving the boot files from sda1 to sda2 and try booting Windows that way. My concern is that Windows has a more serious problem and no amount of MBR/bootloader fixing will get it bootable. In that case it would be necessary to re-install Windows.

For the boot script go here
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by karthick87 on 2010-12-03
Post the output of,

```
sudo aptitude show os-prober
```
```

sudo parted -l
```

---


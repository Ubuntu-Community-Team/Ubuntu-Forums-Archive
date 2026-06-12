---
title: "Dual Boot Win7 and Ubuntu with partition for Ubuntu"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Jasonix on 2011-05-05
Hello All! I am currently running windows 7 and want to install Ubuntu 10.04 LTS. I wish to dual boot and install ubuntu on a different hard drive. However, I only have a dedicated partition on that hard drive, I will not dedicate the whole hard drive. The partition I will use with ubuntu is sdb5. Here is my bootinfo script:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    53,255,474    53,255,412   7 HPFS/NTFS
/dev/sda2          53,255,475   156,248,189   102,992,715   f W95 Ext d (LBA)
/dev/sda5          53,255,538   114,688,034    61,432,497   7 HPFS/NTFS
/dev/sda6         114,688,098   156,248,189    41,560,092   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   281,844,359   281,844,297   7 HPFS/NTFS
/dev/sdb2         281,844,360   312,576,704    30,732,345   f W95 Ext d (LBA)
/dev/sdb5         281,844,423   312,576,704    30,732,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AA40D8EE40D8C26D                       ntfs       SYS1                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        FCE2450AE244CA9A                       ntfs       Apps                          
/dev/sda6        14E2F1D2989425F1                       ntfs       DB                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        18B077EFB077D22C                       ntfs       Sea                           
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        702EAEE12EAE9F98                       ntfs       Linux                         
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/Linux             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  8e 50 5d 06 00 00 00 01  |.........P].....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 49 9a cc 10 00 00  |......?...I.....|
000001d0  c1 ff 0f fe ff ff 88 9a  cc 10 39 f0 d4 01 00 00  |..........9.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

How do I successfully install it with my setup?

---

### Post by wilee-nilee on 2011-05-05
Use the custom install, choose that partition to change to a ext4, thrn in the dropdown from mount make it / click the yes to partition that is there, I forget all the exact words here, then install to that partition.

Now at that first window after choosing custom there is a dropdown or up of where grub should go it should be sdb the mbr of the sdb hd.

You could preformat that partition with gparted but the instuctions then are not much if any different.

---

### Post by Dutch70 on 2011-05-05
Edit: wilee-nilee & I were posting at the same time. To add to what he said. When you get to the place in the installer where you can see your partitions. Click the "change" button to make your settings.

You should create a swap partition equal to, or slightly larger than the size of your physical RAM if you want to be able to hibernate. 

Boot up the live cd or usb & select "Try Ubuntu" to be sure it will run well on your hardware. You can install from there.
When you run the installer, choose to select the partitions manually, not side by side or entire disk obviously. 
Install Ubuntu to sdb5, format to ext4 & set the mount point to "/" aka "root". Make sure it is installing the bootloader to sdb, not sda.

If you have questions during installation, you can get online while installing. There may be a "down arrow" or something, on the install window depending on which version you're installing.

---

### Post by Jasonix on 2011-05-05
> **wilee-nilee said:**
> Use the custom install, choose that partition to change to a ext4, thrn in the dropdown from mount make it / click the yes to partition that is there, I forget all the exact words here, then install to that partition.

Now at that first window after choosing custom there is a dropdown or up of where grub should go it should be sdb the mbr of the sdb hd.

You could preformat that partition with gparted but the instuctions then are not much if any different.

Should I make a linux swap? And if I should, how?
Btw, I have a ralink usb card for wireless, which isn't working. After I install I know how to fix it from another thread. Also, how do I boot up windows 7 and ubuntu with grub 2 after this?

---

### Post by Dutch70 on 2011-05-05
To make a swap partition, just shrink sdb5 by however much you want your swap partition to be. Format it to "swap" during installation the same way you format / to ext4.

Tip: If you format to ext3, you can access your Ubuntu files from windows if you install fs-driver into windows, but ext4 is the latest, supposedly greatest file system.

---

### Post by Jasonix on 2011-05-05
I have a problem...When I get to the part of selecting which partition to install to and everything, it freezes a few seconds after showing me the drives, if not immediately. Any suggestions?:(

---

### Post by Dutch70 on 2011-05-05
Did you select "Try Ubuntu" as I said to make sure it would run ok on your hardware? 

It's also a good idea to select "Check CD for defects".

If you've done the above, you'll probably need to give some hardware specs for others that may know more about that to help you.

---

### Post by Jasonix on 2011-05-05
> **Dutch70 said:**
> Did you select "Try Ubuntu" as I said to make sure it would run ok on your hardware? 

It's also a good idea to select "Check CD for defects".

If you've done the above, you'll probably need to give some hardware specs for others that may know more about that to help you.

Of course I selected try Ubuntu, that is how I got the bootinfo script. I have a radeon 9200 se graphics card(old, but the open source drivers should work), a zonet wireless usb adapter for internet, an amd processor...

---

### Post by Jasonix on 2011-05-05
No suggestions?

---

### Post by Jasonix on 2011-05-05
Ubuntu freezes immediately, if not a few seconds after, showing me where I want to install ubuntu and grub 2 to. Here is my bootinfo:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is 

installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: 

_________________________________________________________________________

    File system:       ntfs
   

 Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
 

   Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                    

   /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: 

_________________________________________________________________________

    File system:       

Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: 

_________________________________________________________________________

    File system:       ntfs
   

 Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, 

sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: 

_________________________________________________________________________

    File system:       ntfs
   

 Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 

starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: 

_________________________________________________________________________

    File system:       ntfs
   

 Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    

Operating System:  
    Boot files/dirs:   

sdb2: 

_________________________________________________________________________

    File system:       

Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: 

_________________________________________________________________________

    File system:       ntfs
   

 Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, 

sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda 

___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 

80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors 

of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         

Start           End          Size  Id System

/dev/sda1    *             63    53,255,474    53,255,412  

 7 HPFS/NTFS
/dev/sda2          53,255,475   156,248,189   102,992,715   f W95 Ext d (LBA)
/dev/sda5     

     53,255,538   114,688,034    61,432,497   7 HPFS/NTFS
/dev/sda6         114,688,098   156,248,189   

 41,560,092   7 HPFS/NTFS


Drive: sdb ___________________ 

_____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 

heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 

bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End  

        Size  Id System

/dev/sdb1                  63   281,844,359   281,844,297   7 HPFS/NTFS
/dev/sdb2         281,844,360   312,576,704    30,732,345   f W95 Ext d (LBA)
/dev/sdb5         

281,844,423   312,576,704    30,732,282   7 HPFS/NTFS


blkid -c /dev/null: 

____________________________________________________________

Device           UUID                      

             TYPE       LABEL                         

/dev/loop0                                       

       squashfs                                 
/dev/sda1        AA40D8EE40D8C26D                      

 ntfs       SYS1                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        FCE2450AE244CA9A    

                   ntfs       Apps                          
/dev/sda6        14E2F1D2989425F1          

             ntfs       DB                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        

18B077EFB077D22C                       ntfs       Sea                           
/dev/sdb2: 

PTTYPE="dos" 
/dev/sdb5        702EAEE12EAE9F98                       ntfs       Linux                  

       
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: 

/dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep 

^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   

iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5      

  /media/Linux             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT 

/NOEXECUTE=OPTIN
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on 

/dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 

fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 

11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  

|.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 

13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe 

bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  

|........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 

05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 

aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  

|.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 

8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa 

f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  

|...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 

fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 

72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading 

OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 

00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 

00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  8e 50 5d 06 00 00 00 01  

|.........P].....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 49 9a cc 10 00 00  |......?...I.....|
000001d0  c1 ff 0f fe ff ff 88 9a  cc 10 39 f0 d4 01 00 00  |..........9.....|
000001e0  00 00 00 00 00 

00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 

00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard 

drive==============

sdc sdd sde sdf 
```Any suggestions?

---

### Post by oldfred on 2011-05-05
I have 3 drives and lots of partitions, it takes gparted or the installer version of gparted a while to find all the drives & partitions.

If you do manual install you get a combo box on where to install grub2's boot loader. As Dutch70 mentioned you want to install the boot loader to sdb and leave windows boot loader in sda. If in BIOS you then change boot the the sdb drive, you can choose Ubuntu or Windows.

During install you should have Ethernet connect and then it should offer to download drivers for Video and wireless if it can. If not they may be in System, Administration, Additional Hardware Drivers, if it boots with generic video drivers.

---

### Post by Jasonix on 2011-05-05
> **oldfred said:**
> I have 3 drives and lots of partitions, it takes gparted or the installer version of gparted a while to find all the drives & partitions.

If you do manual install you get a combo box on where to install grub2's boot loader. As Dutch70 mentioned you want to install the boot loader to sdb and leave windows boot loader in sda. If in BIOS you then change boot the the sdb drive, you can choose Ubuntu or Windows.

During install you should have Ethernet connect and then it should offer to download drivers for Video and wireless if it can. If not they may be in System, Administration, Additional Hardware Drivers, if it boots with generic video drivers.

My wireless doesn't work...I am using a zonet wireless usb adapter to run wireless, which doesn't work. And I checked for drivers, which there were none. My problem is it freezes at the screen when it asks which partition to install on...

---

### Post by Jasonix on 2011-05-05
bump any suggestions?

---

### Post by Hakunka-Matata on 2011-05-05
You'll be glad you did it if you can somehow get a hardwire to the internet during install.  The installer will likely install the drivers for your wireless without even asking about it.  Believe me, it's worth the effort.  Don't forget, Ubuntu is not hardware dependent.  So take the box to a friends house where you can hook up to the Internet.

---

### Post by Dutch70 on 2011-05-05
Yes...3 of them.

1. Please read the code of conduct. 
2. Don't start multiple threads for the same problem.  
3. Wait 24 hours before you bump.

You're not the only person on this forum that needs help.

---

### Post by Jasonix on 2011-05-05
> **Hakunka-Matata said:**
> You'll be glad you did it if you can somehow get a hardwire to the internet during install.  The installer will likely install the drivers for your wireless without even asking about it.  Believe me, it's worth the effort.  Don't forget, Ubuntu is not hardware dependent.  So take the box to a friends house where you can hook up to the Internet.

Sorry, if I have to do that then I won't install Ubuntu. Any other suggestions?

---

### Post by Jasonix on 2011-05-05
> **Dutch70 said:**
> Yes...3 of them.

1. Please read the code of conduct. 
2. Don't start multiple threads for the same problem.  
3. Wait 24 hours before you bump.

You're not the only person on this forum that needs help.

Sorry. I just would like Ubuntu to work...Just like others. I'm sorry, won't happen again.

---

### Post by Dutch70 on 2011-05-05
You don't have to be hooked to the internet to install. I think what Hakunka was saying is that it may simplify things for you quite a bit, after you have it installed. 

Can you give us anymore details on how & when it freezes? 
How long did you wait? Any other details you can think of. 

I can't remember the entire install process, did you get to the part where you put in your name, user name..etc.?

---

### Post by Jasonix on 2011-05-05
> **Dutch70 said:**
> You don't have to be hooked to the internet to install. I think what Hakunka was saying is that it may simplify things for you quite a bit, after you have it installed. 

Can you give us anymore details on how & when it freezes? 
How long did you wait? Any other details you can think of. 

I can't remember the entire install process, did you get to the part where you put in your name, user name..etc.?

I got into live cd, it loaded the install manager that asks if I want to install or try ubuntu(I have clicked try ubuntu to get bootinfo script, so it works). I choose install ubuntu, and I get to the step where it asks where to install. Instead of install side by side, or the other option, I choose custom(choose partitions) and it freezes immediately after displaying partitions, if not a few seconds after it shows me partitions. So, any thoughts? Btw, this is the fix I will use after installation to fix wireless for my usb wireless adapter [http://ubuntuforums.org/showthread.php?t=1313516](http://ubuntuforums.org/showthread.php?t=1313516). Post number three...

---

### Post by Dutch70 on 2011-05-05
It's really hard to say what could be causing that. I would keep trying to see if it freezes at the same place every time. I would also choose the try ubuntu option, and install from there. You may stumble across some more useful info that way.

I'm not sure if it makes a difference at this point, but did you ever select "check cd for defects"?



Keep us updated & maybe someone else will have a better idea.

---

### Post by uRock on 2011-05-05
Duplicate threads merged. Please do not create duplicate threads on the same topic.

---

### Post by Hakunka-Matata on 2011-05-06
> **Dutch70 said:**
> It's really hard to say what could be causing that. I would keep trying to see if it freezes at the same place every time. I would also choose the try ubuntu option, and install from there. You may stumble across some more useful info that way.

I'm not sure if it makes a difference at this point, but did you ever select "check cd for defects"?



Keep us updated & maybe someone else will have a better idea.

@Dutch70, ya, i'm saying it would be a LOT easier on you if you just get an internet conection before you install.  Maybe the OP is a hardhead, like me, and wants to compile a driver for his wireless or other such time consuming chores.  Good Luck

---

### Post by Jasonix on 2011-05-06
So what should I do? I know it always crashes in the partition selection...Yeah what should I do?

---

### Post by oldfred on 2011-05-06
Try running chkdsk on all the NTFS partitions. I have had gparted not load my drive even though my XP would boot. After chkdsk then gparted would see drive without problem. chkdsk only repairs one thing at a time, so multiple passes may be required. Rerun until no errors.

Also from the liveCD you can try to create your partitions before the install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Jasonix on 2011-05-07
I am going to try to give my computer a wired internet connection...I'll post my results...

---


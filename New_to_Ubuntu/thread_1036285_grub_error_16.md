---
title: "grub error 16"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by woodmawa on 2009-01-10
sorry folks newbie here - trying to run ubuntu 8.10 from a USB stick on my siemens S7010D laptop.

This laptop deoesnt recognise USB as a bootable BIOS option 

I have installed wingrub on my machine at  c:/boot/grub

I made my USB stick bootable with the HP formatter.

I have used unetbootin-windows-304 to build my USB stick with the 8.10 iso.

my grub menu.lst config looks like this 

```

default 1
timeout 60
# Sample boot menu configuration file
#
# Boot automatically after a minute.
# By default, boot the second entry.
# Fallback to the first entry.
fallback 0

title Windows XP
unhide (hd0,0)
rootnoverify (hd0,0)
chainloader +1

# For booting Linux
title Boot USB Stick
root (hd1, 0)
chainloader +1
boot

title ubuntu 7.0.4
root (hd1, 0)
kernel /boot/vmlinuz-7.0.4 root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-7.0.4 
boot

title Run Xubuntu 8.10 from USB FLASH DRIVE
root (hd1,0)
kernel /boot/usb-boot/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent
initrd /boot/usb-boot/initrd.gz
boot 
```

The last line being a copy of something i found on one of the forums - edited to set root as (hd1,0).  My stick is disk 1 on my machine.

my bootini is set as follows 

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
C:\GRLDR="Start Grub"

```

when I reboot and start grub (second option on my boot menu.

it fails to start and dumps me into a second grub menu where i can select c:\boot\grub\menu.lst as an option 

however i get grub error 16 and unbuntu wont start.

i've tried looking up the error from google - but dont get a lot that helps me.

what do i have to do to get grub to see my stick and boot unbuntu 8.10?

Would really appreciate understanding what i have got wrong in config 

any ideas

---

### Post by woodmawa on 2009-01-11
does any one know where I should start to fix this?

---

### Post by hotweiss on 2009-01-11
> **woodmawa said:**
> does any one know where I should start to fix this?

Try going into recovery mode and see if the system will check the hard drive. If that doesn't work, boot up the live CD and run:

> fsck

---

### Post by caljohnsmith on 2009-01-11
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by woodmawa on 2009-01-11
sadly - i think you think i am further in.

i'm not.  I can boot XP (my primary login )

however I cant get grub to work at present - hence i cant try anything at a linux cmd terminal  as i cant even get ubuntu to boot at all.

i updated the grldr from the latest grub4dos-0.4.3-2007-05-09.zip
as this is newer than the version that wingrub installs in my C drive.

however i still cant get grub to bring up the c:\boot\grub\muenu.lst properly.  The bahviour is a little different now - when it all fails (too quick to read) i end at a command prompt.  I hit escape and it gives me three options to find a menu.lst.  

If i choose the first one - it at least holds the screen at the end and says that MBR doesnt align with bios details.  

At this point im not sure whats going on - I can main boot to XP okay (which I expect i count if my MBR on the c drive (hd0,0) was not working.  

however when it moans with these errors I presume its talking about my main HDD.  Their doesnt appear to an option in the bios boot order to boot from a USB (order currently reads, HDD, CD, Floppy)

so somehow i need to fix grub first before I can even start on ubuntu.

in the old version of GRLDR, it just said error 16 and stopped.

---

### Post by caljohnsmith on 2009-01-11
Do you have a Ubuntu Live CD you can use for troubleshooting? You did download the 8.10 ISO you mentioned, so can you burn that to CD and use it? If so, you could run the script from there. If not, it will be difficult to troubleshoot your problem. One thing we could check is when you get the Grub menu on start up, press "c" to get the command line, and then do:
```
grub> geometry (hd1)
```
and does that show your USB stick? It should show the partitions and size of the drive. If it does show your USB stick, how about doing:
```
grub> rootnoverify (hd1)
grub> chainloader +1
grub> boot
```
And let me know what happens after that. We can work from there if you want.

---

### Post by woodmawa on 2009-01-11
well something kinda works - this is typed from firefox within unbuntu8.10

first of all thanks for getting me this far.

I ignored all the grub errors about MBR cylinders (978) etc not being that in the bIOS (1024) etc errors - I think the 978 etc bits, must be from the USB stick and just dont look the bios settings for my HDD (normal xp boot mode of my c drive ??)

any way ignoring the errors the interleaved response from the geometry (hd1) command was

```

disc 0x81 (LBA) : c/h/s = 978/255/63, sector count/size = 151711570/512

partition type:0 file type is fat part 0xc


``` 

I then typed in your command sequence one after another and got to boot and hit return.

grub vanished and i hit the unetbootin boot screen (i built the disk from the ubuntu iso with this tool)

and the stick started to boot - 

and here i am so to speak.

what i'm not sure now is how to proceed makeing this painless to boot.

maybe you can now help me from here.

as I keep getting the errors from grub - i am assuming its looking at the USB before the HDD?  

if i copy the wingrub files from my HDD c drive (hd0) including  boot/grub/menu.lst files to my stick will it then find the grub config from the stick and try and load up okay??

I had an entry in the menu.lst file that runs the command sequence you gave me.

I think i just dont really understand what the bootloader is actually doing inside its little innards - and i'm nervous of corrupting my primary XP boot by messing about to much in my ignorance.


Can you now suggest what my next steps should be.  But hello ubuntu here we come -

---

### Post by caljohnsmith on 2009-01-11
Now that you successfully booted into Ubuntu on your USB drive, can you download and run the script from post #4? That will probably give us all the information we need to sort out your booting problem. Without it, doing everything manually could be quite time-consuming. If you don't have internet connectivity in 8.10 yet, can you download the script maybe when you are in Windows? If you can do that, you could then transfer it to you Ubuntu desktop and run it. Let me know how that goes or if you run into problems.

---

### Post by woodmawa on 2009-01-11
okay here goes 

when i put the win grub files on the usb stick things booted more readily (i've yet to go back to the previous grdlr file (as it didnt report the bios mismatch)

however it is 

results from the script are as follows

======================

```


============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot/grub/menu.lst /boot.ini /grldr /ntldr 
                       /NTDETECT.COM /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy
mount: according to mtab, /dev/sdb1 is mounted on /cdrom

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf4fbf4fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    37672424    18836181    7  HPFS/NTFS
/dev/sda2        37672425    78140159    20233867+   f  W95 Ext'd (LBA)
/dev/sda5        37672488    62798084    12562798+   7  HPFS/NTFS
/dev/sda6        62798148    78140159     7671006    7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition [6]: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15701759 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00df5cbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15701758     7850848    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(976, 254, 63) logical=(977, 99, 17)

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="72C8CB13C8CAD50F" TYPE="ntfs" 
/dev/sda5: UUID="001CA3B21CA3A0E0" LABEL="Customer Data" TYPE="ntfs" 
/dev/sda6: UUID="10148CCE7D70FBA9" LABEL="Support" TYPE="ntfs" 
/dev/sdb1: UUID="E46E-83EE" TYPE="vfat" 
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
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/Customer Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda1/boot/grub/menu.lst: ===========================

default 1

timeout 60

# Sample boot menu configuration file

#

# Boot automatically after a minute.

# By default, boot the second entry.

# Fallback to the first entry.

fallback 0



title Windows XP

unhide (hd0,0)

rootnoverify (hd0,0)

chainloader +1



# For booting ubuntu

title Boot USB Stick

rootnoverify (hd1)

chainloader +1

boot





title Run Xubuntu 8.10 from USB FLASH DRIVE

root (hd1,0)

kernel /boot/usb-boot/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent

initrd /boot/usb-boot/initrd.gz

boot 
================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

C:\GRLDR="Start Grub"


================================== sda1/boot: ==================================

total 97
drwxrwxrwx 1 root root      0 2007-08-07 17:06 .
drwxrwxrwx 1 root root  12288 2009-01-11 16:23 ..
drwxrwxrwx 1 root root   4096 2007-10-13 22:01 grub
-rwxrwxrwx 1 root root    512 2003-08-04 13:09 stage1
-rwxrwxrwx 1 root root 114064 2003-08-04 13:09 stage2

=============================== sda1/boot/grub: ===============================

total 229
drwxrwxrwx 1 root root   4096 2007-10-13 22:01 .
drwxrwxrwx 1 root root      0 2007-08-07 17:06 ..
-rwxrwxrwx 2 root root   7872 2004-07-31 06:02 e2fs_stage1_5
-rwxrwxrwx 2 root root   7632 2004-07-31 06:02 fat_stage1_5
-rwxrwxrwx 2 root root   6880 2004-07-31 06:02 ffs_stage1_5
-rwxrwxrwx 2 root root   6944 2004-07-31 06:02 iso9660_stage1_5
-rwxrwxrwx 2 root root   8384 2004-07-31 06:02 jfs_stage1_5
-rwxrwxrwx 1 root root    570 2009-01-11 17:40 menu.lst
-rwxrwxrwx 2 root root   7072 2004-07-31 06:02 minix_stage1_5
-rwxrwxrwx 2 root root   9632 2004-07-31 06:02 ntfs_stage1_5
-rwxrwxrwx 2 root root    394 2007-10-13 21:44 original menu.lst
-rwxrwxrwx 2 root root   9376 2004-07-31 06:02 reiserfs_stage1_5
-rwxrwxrwx 1 root root    512 2004-02-07 15:02 stage1
-rwxrwxrwx 1 root root 135240 2004-08-30 18:13 stage2
-rwxrwxrwx 2 root root   7156 2004-07-31 06:02 ufs2_stage1_5
-rwxrwxrwx 2 root root   6560 2004-07-31 06:02 vstafs_stage1_5
-rwxrwxrwx 1 root root  56832 2003-07-22 10:43 w32grub.exe
-rwxrwxrwx 2 root root   9320 2004-07-31 06:02 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda6

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  bb 19 ea 00 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  71 84 02 00 00 00 00 00  |........q.......|
00000040  f6 00 00 00 01 00 00 00  a9 fb 70 7d ce 8c 14 10  |..........p}....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 fa 33 c0  |..............3.|
00000060  8e d0 bc 00 7c fb b8 c0  07 8e d8 c7 06 54 00 00  |....|........T..|
00000070  00 c7 06 56 00 00 00 c7  06 5b 00 10 00 b8 00 0d  |...V.....[......|
00000080  8e c0 2b db e8 07 00 68  00 0d 68 66 02 cb 50 53  |..+....h..hf..PS|
00000090  51 52 06 66 a1 54 00 66  03 06 1c 00 66 33 d2 66  |QR.f.T.f....f3.f|
000000a0  0f b7 0e 18 00 66 f7 f1  fe c2 88 16 5a 00 66 8b  |.....f......Z.f.|
000000b0  d0 66 c1 ea 10 f7 36 1a  00 88 16 25 00 a3 58 00  |.f....6....%..X.|
000000c0  a1 18 00 2a 06 5a 00 40  3b 06 5b 00 76 03 a1 5b  |...*.Z.@;.[.v..[|
000000d0  00 50 b4 02 8b 16 58 00  b1 06 d2 e6 0a 36 5a 00  |.P....X......6Z.|
000000e0  8b ca 86 e9 8a 36 25 00  b2 80 cd 13 58 72 2a 01  |.....6%.....Xr*.|
000000f0  06 54 00 83 16 56 00 00  29 06 5b 00 76 0b c1 e0  |.T...V..).[.v...|
00000100  05 8c c2 03 d0 8e c2 eb  8a 07 5a 59 5b 58 c3 be  |..........ZY[X..|
00000110  59 01 eb 08 be e3 01 eb  03 be 39 01 e8 09 00 be  |Y.........9.....|
00000120  ad 01 e8 03 00 fb eb fe  ac 3c 00 74 09 b4 0e bb  |.........<.t....|
00000130  07 00 cd 10 eb f2 c3 1d  00 41 20 64 69 73 6b 20  |.........A disk |
00000140  72 65 61 64 20 65 72 72  6f 72 20 6f 63 63 75 72  |read error occur|
00000150  72 65 64 2e 0d 0a 00 29  00 41 20 6b 65 72 6e 65  |red....).A kerne|
00000160  6c 20 66 69 6c 65 20 69  73 20 6d 69 73 73 69 6e  |l file is missin|
00000170  67 20 66 72 6f 6d 20 74  68 65 20 64 69 73 6b 2e  |g from the disk.|
00000180  0d 0a 00 25 00 41 20 6b  65 72 6e 65 6c 20 66 69  |...%.A kernel fi|
00000190  6c 65 20 69 73 20 74 6f  6f 20 64 69 73 63 6f 6e  |le is too discon|
000001a0  74 69 67 75 6f 75 73 2e  0d 0a 00 33 00 49 6e 73  |tiguous....3.Ins|
000001b0  65 72 74 20 61 20 73 79  73 74 65 6d 20 64 69 73  |ert a system dis|
000001c0  6b 65 74 74 65 20 61 6e  64 20 72 65 73 74 61 72  |kette and restar|
000001d0  74 0d 0a 74 68 65 20 73  79 73 74 65 6d 2e 0d 0a  |t..the system...|
000001e0  00 17 00 5c 4e 54 4c 44  52 20 69 73 20 63 6f 6d  |...\NTLDR is com|
000001f0  70 72 65 73 73 65 64 2e  0d 0a 00 00 00 00 55 aa  |pressed.......U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-11
You mentioned that you are using the Grub4DOS-0.4.3 version; how about downloading the [Grub4DOS-0.4.4]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip") version, and replace the current "grldr" file in your Windows root directory C:\ with the one that comes in that package. Then open a notepad document, and copy the following into it:
```
default 0
timeout 60

title Ubuntu on the USB stick
rootnoverify (hd1)
chainloader +1
```
And save that file to your Windows C:\ root directory (where the grldr file is), not the C:\boot\grub directory where your current one is. Then reboot, and let me know exactly what happens when you go through the boot menus to boot the USB stick. We can work from there if you want.

---

### Post by woodmawa on 2009-01-11
actually - i went back to the original older wingrub grldr, and scrapped the 4.0.3 version.

This seems to okay this time and no errors.

i go to start grub - and then it now shows me the grub menu (this after i copied all the boot/grub .. dir into my usb stick.

when i hit the start linux entry it runs the commands you gave me and goes straight to the unetboot loader - and then into booting ubuntu.

winding back seems to have the error messsages with the 4.03 version of grub which didnt seem to like the mismatch somehow between my stick details and the bios.



Next step appears to be that the build that starts is like a live CD - and wont persist any of the session details (files etc).

how do I tell unbuntu to allow me to store session work persistently on the extra space on the stick?

is this an error in the unetbootin build sequence i did from the ubuntu.iso to build the stick.  

I am nervous about running the install command from the system menu.  The last time I did this from a 7.04 live cd it built a file system on the stick but messed up the MBR of my normal HDD - which meant i couldnt boot the laptop without having the stick.  

I ended up haveing to do a system recovery in windows and rebuild my MBR to get me back to normal and i'd rather no go through that again.

how do i convert the stick to persistent build ???

otherwise I now seem to up and running - thanks for all the help provided its really appreciated :p

---

### Post by thomas228 on 2009-01-11
> **woodmawa said:**
> actually - i went back to the original older wingrub grldr, and scrapped the 4.0.3 version.

This seems to okay this time and no errors.

i go to start grub - and then it now shows me the grub menu (this after i copied all the boot/grub .. dir into my usb stick.

when i hit the start linux entry it runs the commands you gave me and goes straight to the unetboot loader - and then into booting ubuntu.

winding back seems to have the error messsages with the 4.03 version of grub which didnt seem to like the mismatch somehow between my stick details and the bios.



Next step appears to be that the build that starts is like a live CD - and wont persist any of the session details (files etc).

how do I tell unbuntu to allow me to store session work persistently on the extra space on the stick?

is this an error in the unetbootin build sequence i did from the ubuntu.iso to build the stick.  

I am nervous about running the install command from the system menu.  The last time I did this from a 7.04 live cd it built a file system on the stick but messed up the MBR of my normal HDD - which meant i couldnt boot the laptop without having the stick.  

I ended up haveing to do a system recovery in windows and rebuild my MBR to get me back to normal and i'd rather no go through that again.

how do i convert the stick to persistent build ???

otherwise I now seem to up and running - thanks for all the help provided its really appreciated :p

Hi

The unibootin method worked for me to create a liveusb from the iso download in both 8.04 and 8.10 on 2GB thumbs

For a viable thumb installation I used an 8GB thumb using 2 GB as swap an 6GB for 8.04 persistent build.
The threads I used were [http://ubuntuforums.org/showthread.php?t=1017566&page=2](http://ubuntuforums.org/showthread.php?t=1017566&page=2) post #14 and [http://ubuntuforums.org/showthread.php?t=1021772](http://ubuntuforums.org/showthread.php?t=1021772)

Where did you get the window's grub installation at.  That might be the solution to a problem I have for another laptop and 3 desktops I have that do not have a bios option for a thumb bootup.

Thanks and good luck

Tom

---

### Post by woodmawa on 2009-01-14
first off - Thomas thankyou for the post (couldnt get to the forums the other day - hence time to reply.

in case any else goes through this quick update 

First off i ended up trying the thread you posted - Bit of a fiddle (thats my uncertainty about messing my main build).

in order to that i ended up having to trash the liveUSB build + unibootin.  However I had to burn the iso to a liveCD (i used easy cd creator - and theres instructions on that you can lookup) 

I booted of the live CD and went to the install option and followed the instructions.  One thing I have noted is that the liveUSB build on fat32 - appeared to run faster - but i presume thats because its running in memory and not really using the disk?

anyhow - went through the partition section and used ext3 format as suggested and allocated 6.5M to the drive and about 1.5M for swap (used the manual approach as per instructions).  Not really sure what proportion of swap to disk would be - but about 19% sounded okay.

when the install gets going (remembering to select the install grub to usb stick ) it all goes but its pretty slow from the live CD so go have a coffee.

I thought it hadn't worked when i completed as when i booted again with the live CD out - i got a grub 16 error (that was my c drive HDD grub failing to find what needed to see on the stick (which is odd as grub is there - but maybe its because if my boot from the HDD first the ntfs load cant read the ext3 format on the stick ?

got depressed went to bed.  Looked in the morning and i found the option at last in bios to boot from the usb first and the hdd second.  

but the stick back in and hey presto the stick comes up.  You installed as sdb (hd1) drive relative to  live CD boot - magically becomes sda and hd0 - the syslinux formatting finds the grub menu.lst off the stick and you get straight in

Hooray!!!

Still not sure i truely understand how all this is working - but somehow when i had the hdd as first in the boot sequence - i called the grldr on my hdd c drive - and somehow instead of reading the boot/grub details on the c drive (which is what i thought it would do) it seemed to look for boot/grub details on the stick instead!

I am not sure if this was the unibootin - i think i saw something that said unibootin has some interaction with grdlr. Net of this was that when i copied the menu.lst into details onto the stick my error 16 finished and i could chain load from c drive to the stick - this presents the grub menu of the stick - when i ran the simple chainloader +  detail that someone pointed out earlier - this started the unibootin menu - which then booted my liveUSB!!! phew.

as i said however i couldnt figure out how to turn the liveUSB config (on bootable fat32 format) into persistent mode.  The posted you suggested allowed my to do this.  

So here i am ready to go I think  

so last tom - in answer to your question back re you older machines that cant boot of USB.

what i did was from windows was download the HP format app - I formatted the stick (fat32) and made bootable (but i needed a bootable win98 dos disc to do that to provide the io.sys etc bits and pieces.  )

Once i had a bootable (but empty USB) I used unibootin to install ubuntu from the iso to the bootable stick.

Then once i copied my boot/grub config from my c drive to the stick (still not sure why it couldnt find the c drive version. However once you do that it posts the grub menu off your stick - you run the entry you create to chainload and this runs unibootin menu and then into unbuntu.

as i said it only seems to build a liveUSB ubuntu and therefore you cant save your settings etc.  so the option below is better in the end.

havnt tried it on another machine yet but it sounds from the posts that it should just work 

> 
The unibootin method worked for me to create a liveusb from the iso download in both 8.04 and 8.10 on 2GB thumbs

For a viable thumb installation I used an 8GB thumb using 2 GB as swap an 6GB for 8.04 persistent build.
The threads I used were [http://ubuntuforums.org/showthread.php?t=1017566&page=2](http://ubuntuforums.org/showthread.php?t=1017566&page=2) post #14 and [http://ubuntuforums.org/showthread.php?t=1021772](http://ubuntuforums.org/showthread.php?t=1021772)

Where did you get the window's grub installation at. That might be the solution to a problem I have for another laptop and 3 desktops I have that do not have a bios option for a thumb bootup.

Thanks and good luck

Tom


Hope that answers your question.

Have to say this is quite for the under confident at this point but thanks for getting my through this 

:popcorn:

---


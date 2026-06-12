---
title: "Cannot boot from boot DVD"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Patrick A on 2011-01-08
Hi,
I'm having problems with my Wubi install. I've read the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") and they suggest first to get a boot CD.

So I get the ISO from Ubuntu and burn it on a DVD. I check the files on the DVD and it looks ok (many directories, files, etc). Now I'm trying to boot (yes, I changed my boot order to CD first) and the only thing I get is a screen from Ubuntu (actually it's an empty screen except at the bottom where there is something like a keyboard and a little man) and after a few seconds, black screen appears with a blinking cursor at the upper left. Nothing more happens. Can someone help me with this problem (so I can address the bigger problem of Wubi breakage after!).

Thank you very much,
Patrick

---

### Post by Rubi1200 on 2011-01-08
Hi and welcome to the forums :)

Well obviously I am glad you found the Wubi Megathread since that is where I would have sent you for help ;)

What graphics card do you have installed?

Thanks.

---

### Post by Patrick A on 2011-01-08
Thank you Rubi1200 for your quick reply, it seems that you're always there to help someone!

I have a Nvidia geoforce GT 130M. I have to say that pressing enter while on the "keyboard-little man logo screen" redirects me to a screen where I can choose a language (I chose english) and after a menu where I can choose something like "Try Ubuntu without installing". Choosing this option (or any other) gives me the black screen and the blinking cursor again.

---

### Post by Rubi1200 on 2011-01-08
So, this is what you need to do.

Start the LiveCD and when you see that first logo press F6 followed by Esc.

You should see a line that looks like this:
> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Use the arrow key to move the cursor backwards and delete quiet splash.

Type nomodeset instead so that it looks like this:

> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**
Then, Enter to boot and you should hopefully be at the live desktop.

If this does not work, try doing it after the steps you mentioned above.

---

### Post by Patrick A on 2011-01-08
Thanks again Rubi1200. I tried it and now a lot of statements are displayed. I cannot reproduce them all here but the last ones are:

...
[3.108685] Cannot allocate resource for EISA slot 1
... (other ones)
[3.109135] Cannot allocate resource for EISA slot 8
[3.109198 EISA: Detected 0 cards.
... (other ones)
[3.111420] registered taskstats version 1

and under these statements, this damned blinking cursor again.

---

### Post by Rubi1200 on 2011-01-08
Do you have a setting in BIOS for AGP or PCI? Basically, you are looking to see if there is a graphics setting in there.

Whichever one it is, try changing to the other. This is only for the purposes of getting the CD booted.  You can change it again afterwards.

---

### Post by Patrick A on 2011-01-08
Unfortunately, I don't see any setting in the BIOS setup that is related to the videocard.

---

### Post by Rubi1200 on 2011-01-08
I have not seen those errors before, but I am fairly certain they are related to the graphics card.

Are you able to boot into Windows normally?

If yes, download and burn a different LiveCD.

My suggestion would be Knoppix.

As long as we can boot the computer, we can help you fix the Wubi breakage.

---

### Post by Patrick A on 2011-01-08
Ok Rubi1200, I'll try it right now.
And yes I can boot Windows. Other info that can be meaningful to you: I try the boot CD on my very old Compaq laptop and it works!

---

### Post by Rubi1200 on 2011-01-08
Yes, I have seen that before that the CD works on one computer but not on the other; odd I know!

If you can make another CD work to boot the computer then go to the Megathread again and follow the instructions relevant to your situation.

Sounds like problem #2, probably needs solution #1 or #2.

I will be online for another 3-4 hours or so.

---

### Post by Patrick A on 2011-01-08
Thank you so much Rubi1200, your help is very very appreciated. I'm downloading Knoppix right now. At the same time, I'm gonna make a liveUSB with the first ISO I got this morning. We'll see. Back in a few minutes. Thanks again.

By the way, when I say that it works on my old Compaq, I mean that there is no more blinking cursor. I see a black screen with some commands available (help returns a list of these commands). No graphics interface. Is it normal?

EDIT: the liveUSB process just finished. I got a 7-zip (my zip program) diagnostics message window that says

# Message
0 D:\Ubuntu\ubuntu-10.10-desktop-i386.iso
1 Data error in 'casper\filesystem.squashfs'. File is broken

I'll try the knoppix iso as soon as the download is finished.

EDIT 2:
When I press Close to close the 7-zip diagnostics window, it says
Universal USB Installer successfully installed
... Installation Done, Process Complete!
I'm trying to boot from the USB

---

### Post by Patrick A on 2011-01-08
Nothing is easy today... The boot from the USB does not seem to work. I looked at the boot order again and CD is first, removable device is second, network is 3rd and hard drive 4th. When I boot, the window letting me to choose between Vista and Ubuntu is displayed. Sigh.

---

### Post by Rubi1200 on 2011-01-08
If you want to boot from the USB, you need to set Removable Device as first priority, then CD, then Hard-Drive (at least that is how I have mine set up).

---

### Post by Patrick A on 2011-01-08
I set the Removable device 1st in the boot order: does not work anymore (I mean, no linux boot)

I tried the Knoppix boot CD, does not work (it says loading linux..........) and suddenly two nice penguins appear at the upper left (the equivalent of the blinking cursor I suppose) and nothing more happens.

I tried the same boot CD on my old Compaq and it works.

Looks like a problem related with my ASUS laptop. Maybe my videocard as you said Rubi1200.

---

### Post by coffeecat on 2011-01-08
> **Patrick A said:**
> I tried the Knoppix boot CD, does not work (it says loading linux..........) and suddenly two nice penguins appear at the upper left (the equivalent of the blinking cursor I suppose) and nothing more happens.

From what I remember of Knoppix that sounds as though it's trying but failing to boot from the CD, so at least the process started. The penguins are often seen in distros with text-only boot. You have a dual-core CPU. :) You should see a quad-core booting - the four penguins of the Apocalypse! 

> **Patrick A said:**
>  Looks like a problem related with my ASUS laptop. Maybe my videocard as you said Rubi1200.

... or possibly the BIOS itself, perhaps the implementation of ACPI. Some are so buggy they are positively Linux-hostile. I had a desktop motherboard that worked just fine with Linux until I made the mistake of flashing a newer version of the BIOS. Oops! I couldn't get any Linux distro to boot either from the HD or from a CD. Fortunately I'd saved the old BIOS with a Windows-based utility the manufacturer supplied and was able to downgrade and now that m'board is in a machine happily running Ubuntu 10.04 for a relative.

What model Asus is it? A google/forum search for the particular model might uncover something helpful.

---

### Post by Patrick A on 2011-01-08
Ruby1200, I noticed another option above the nomodeset that is called noapic. I replaced the quiet splash option with noapic (instead of nomodeset). It seems to work. Again, I mean by that that it does not freeze anymore though I don't see any graphics interface, is it normal? I see only a minimal black and white screen with "(initramfs)" prompt. 

Last message before the prompt was:
"mount: mounting /dev/loop0 on //filesystem.squashfs failed: invalid argument. Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

The filesystem.squashfs was the "file broken" mentioned above in the usb installer process.

Can I try something at the initramfs prompt?

---

### Post by Rubi1200 on 2011-01-08
The error sounds as if the image may be corrupt in some way.

As coffeecat asked, what model is this?

I highly recommend UNetbootin for putting images on a USB:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ugm6hr on 2011-01-08
> **Patrick A said:**
> By the way, when I say that it works on my old Compaq, I mean that there is no more blinking cursor. I see a black screen with some commands available (help returns a list of these commands). No graphics interface. Is it normal?

No it isnt. Have you checked the md5sum?
The Live CD no longer has a check for errors option, which is a shame.

---

### Post by Patrick A on 2011-01-08
Do you recommend also to download a new iso? (the one I got this morning is ubuntu-10.10-desktop-i386.iso). Would you recommend an earlier version? 32-bit or 64-bit?

Out of curiosity, what is supposed to appear after a successful boot? The normal graphical interface?

My system is ASUS Notebook F90SG/F90SV/N90SV series
Intel Core 2 Duo CPU T9550 2.66Ghz 2.67Ghz

---

### Post by Patrick A on 2011-01-08
@ugm6hr: No I didn't check the md5sum. I'll google it to know how to do it (and what it is!) and I get back to you as soon as I can.
thanks!

---

### Post by Rubi1200 on 2011-01-08
You could give the 10.04 version a try. If the notebook is 32bit then choose the 32bit version:
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

> Out of curiosity, what is supposed to appear after a successful boot? The normal graphical interface?
Yes.

You are supposed to see something like this:
[http://2.bp.blogspot.com/_JBHfzEovWs8/TMWj79HzhEI/AAAAAAAAAws/QJfWoKaMqWY/s1600/1ubuntu10.10installationstart.png](http://2.bp.blogspot.com/_JBHfzEovWs8/TMWj79HzhEI/AAAAAAAAAws/QJfWoKaMqWY/s1600/1ubuntu10.10installationstart.png)

Not sure why you are having these difficulties, but try checking the integrity before burning and also burn at the lowest possible speed.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If all else fails, there is another option to deal with this, but I would rather wait and see if we can get a CD booted for you.

---

### Post by Patrick A on 2011-01-08
Did the checksum and compare it to ubuntu-10.10-desktop-i386 hash. Result: it is not the same! Thank for the hint ugm6hr. 

I will try with my new download as soon as it's finished.

Oh, thank you so much guys, this Ubuntu community is so great!
Patrick

---

### Post by Rubi1200 on 2011-01-08
It is quite possible that this was the reason things failed before.

Fingers crossed that it works this time :)

---

### Post by Patrick A on 2011-01-08
Actually, my system is 64-bit. Should I download the 64 bit version of Ubuntu-10.10-desktop.i386?

---

### Post by Rubi1200 on 2011-01-08
Probably better, but for the purposes of fixing the Wubi install it should not really make a difference.

On the Ubuntu download page you can choose the 64bit version at the side where it offers download options.

---

### Post by Patrick A on 2011-01-08
I've tried the 32bit: does not work on the 64bit ASUS (blinking cursor) but works like a charm on the old Compaq (I see now for the first time the graphical environment!).

I've downloaded the 64 bit version (which is called ubuntu-10.10-desktop-amd64.iso, I'm a little bit concerned about the amd tag as I have an Intel processor). Anyway, I will try the boot CD for the 64 bit iso in a moment.

thanks again,
Patrick

---

### Post by coffeecat on 2011-01-08
> **Patrick A said:**
>  I'm a little bit concerned about the amd tag as I have an Intel processor).

It's not a problem. It's a historical thing - AMD were first out with their AMD64 processors. The AMD64 ISO will work just fine with an Intel 64-bit CPU.

---

### Post by Patrick A on 2011-01-08
IT'S WORKING GUYS, IT'S WORKING!!
I was losing hope as the first try with the 64 bit boot CD was not working but I tried after to boot with the nolapic option and suddenly, IT'S WORKING! 

But wait, calm down Patrick, you have to address now the problem you had at 6AM this morning...

Well ok, back to the Wubi megathread now.

First question about it: is it really a grub update (or something like that) that caused the problem? I have to say that my laptop was not shut down yesterday night (my 5-year old child loves all these buttons on my computer...) and this morning, ubuntu did not work anymore. I checked in the ubuntu directory (in Windows) and noticed that the disks directory was not there anymore (Oh my God, all my data!)

Anyway, I will try the procedure described by Ruby1200 in the megathread and get back to you with the results of the boot info script.

Thanks again to all of you!
Patrick

---

### Post by Patrick A on 2011-01-08
results from boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   488,384,511   488,382,464   7 HPFS/NTFS
/dev/sda2         488,384,512   976,768,064   488,383,553   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,015,230     2,015,168   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    24,579,449    24,579,387  1c Hidden W95 FAT32 (LBA)
/dev/sdd2    *     24,579,450   512,955,449   488,376,000   7 HPFS/NTFS
/dev/sdd3         512,955,450   976,768,064   463,812,615   f W95 Ext d (LBA)
/dev/sdd5         512,955,513   976,768,064   463,812,552   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        50FEB45AFEB439D4                       ntfs                                     
/dev/sda2        924EBA2F4EBA0BCB                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1515-3457                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        D476-EF15                              vfat       RECOVERY                      
/dev/sdd2        C6187A011879F133                       ntfs       Vista64                       
/dev/sdd5        810001C9C38C8760                       ntfs       DATA                          
/dev/sdd: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 bf 1e 00 ad 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 57 34 15 15 4e  4f 20 4e 41 4d 45 20 20  |..)W4..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 82 0f 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 08 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3a 14 93 1e  |........?...:...|
00000020  3b 8b 38 01 fc 4d 00 00  00 00 00 00 5d 07 00 00  |;.8..M......]...|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  ff 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 c8 37 a5 1b 00 00  |......?....7....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by Patrick A on 2011-01-08
By the way, I didn't say that the version number of ubuntu I "wubi" installed last year was 10.10. The solutions in the megathread are for a 10.04 install, a 10.04 to 10.10 upgrade or a 10.041 to 10.10 upgrade. Nothing for the fresh 10.10 install?

---

### Post by Patrick A on 2011-01-08
I don't see the root.disk anywhere in the RESULTS.txt.
Don't hide me the truth doctor...

---

### Post by Patrick A on 2011-01-08
After the mount of my /dev/sdd2 to /media/win, I confirm that there is no disks directory in the /media/win/ubuntu directory. But there is hope! I have noticed that there is a found.000 directory in the /media/win dir. It contains a "boot" directory and the files root.disk and swap.disk.

Question: Should I copy the two files found in found.000 in the /media/win/ubuntu/disks directory (this one should be created first as disks dir does not exist)?

P.S. boot directory in found.000 contains only the grub directory. Grub dir is empty.

---

### Post by Patrick A on 2011-01-08
IT'S WORKING NOW! 
After copying the swap.disk and root.disk files in the /media/win/ubuntu/disks directory, I followed the procedure for problem #2 solution #1 in the wubi megathread and I recovered Ubuntu (and all my data!).

Thank you to all of you guys, especially Ruby1200 for this precious thread.

Patrick

---

### Post by Rubi1200 on 2011-01-09
Sorry I wasn't there to see you through to the end; time zones and all that.

I am really pleased you got it working and this is, in my opinion, a valuable learning experience.

You are also more than welcome as far as helping is concerned :)

Don't forget to apply the Permanent Fix from the Megathread.

If, at some point, you would like to install Ubuntu to the drive, just ask and we will be more than happy to help.

Also, for a bit more information. Sometimes, if Windows does something like a chkdsk it moves the files to the folder you saw.

Your approach was exactly right in the situation.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by Patrick A on 2011-01-09
Don't be sorry Ruby1200, you were not there but your megathread was! And oh, that's true, I forgot the permanent fix, I'll do it. In retrospect, do you think the error was due to the grub update or to the non-clean shutdown? The last one seems more plausible to me. And one other thing that I cannot explain is that I couldn't find the folder000 in Windows (yes my folder option is set to show hidden files) but I could see it after mounting the windows partition on Ubuntu.

Anyway, a very good learning experience as you said!
Thank you so much,
Patrick

---


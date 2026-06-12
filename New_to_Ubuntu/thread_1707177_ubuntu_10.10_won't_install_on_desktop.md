---
title: "ubuntu 10.10 won't install on desktop"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Jayme Harris2007 on 2011-03-15
I'm very new to ubuntu and can't get 10.10 to install on a desktop computer with a fresh formated hard drive. In most cases I get the following error message (*process:255): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0). There have been a couple of times when I get as far as the install screen on the Live CD and the system freezes up when I click on the install button. 

 The desktop is running a Pentium 4 with a 40 GB hard drive and 512 MB of ram. If more information is needed let me know and I'll try to find out what I can. 


Thank you all in advance for the help.  

Jayme

---

### Post by Temposs on 2011-03-15
You could try installing Ubuntu 10.04 instead, since that is the more stable version and it is a Long Term Support version. This is what I would recommend you try first.

---

### Post by Rubi1200 on 2011-03-15
Hi and welcome to the forums Jayme Harris2007 :)

Could be a bad burn?

Follow these steps:

download the Ubuntu iso: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

try as a LiveCD first to see that everything works as it should (don't forget to set BIOS to boot from the CD drive first)

---

### Post by Jayme Harris2007 on 2011-03-16
Thank you for the suggestions. I've downloaded the ubuntu 10.04.2 iso and was able to download a program for windows to confirm the hash. I'm in the process right now of burning the live CD to a disk. Can I run the hash on the live CD and if I can will it have the same hash as the iso? 


Jayme

---

### Post by Temposs on 2011-03-16
When you load up the LiveCD it will have an option on the first menu to check the disk integrity. This is probably the extent of checking the already burned CD that you could do.

---

### Post by Jayme Harris2007 on 2011-03-16
> **Jayme Harris2007 said:**
> Thank you for the suggestions. I've downloaded the ubuntu 10.04.2 iso and was able to download a program for windows to confirm the hash. I'm in the process right now of burning the live CD to a disk. Can I run the hash on the live CD and if I can will it have the same hash as the iso? 


Jayme

 Okay I burned the Live CD and tested it on my laptop that is running Windows Vista. I made sure that my first boot option was my DVD and it booted up and seems to run okay. I tried it on the desktop this morning and only got at far as the ubuntu screen with the five dots it froze up at that point. I think I may also have a keyboard error since my Function, Cap locks and Num locks lights are all flashing.

Thank again for the help.

Jayme

---

### Post by Rubi1200 on 2011-03-16
What graphics card do you have installed?

How many partitions are on the drive?

---

### Post by Jayme Harris2007 on 2011-03-18
> **Rubi1200 said:**
> What graphics card do you have installed?

How many partitions are on the drive?

  Sorry it's taken me so long to get back. The system is an ATA motherboard and has a built in video card. Here's the information I was able to come up with:

Video Chip Vendor:  Intel Corp
Video Chip:  82845G/GL/GE Int Graphics Device (B1-Step)
Visa OEM String Brookdale-G Graphics Chip Accelerated VGA
Video Memory:  832kb.

  There appear to be two partitions C: and D:. I'm assuming that the D drive is a DOS shell of some kind since the old Windows XP OS that I formated over doesn't actually run in DOS.



Jayme

---

### Post by rupak447 on 2011-03-18
Hey Jayme, if you do not mind then I suggest you to change your older version and  have a try with a new version. I am using  ubuntu 10.10 on ma core i3 desktop computer and it really does well.

---

### Post by Jayme Harris2007 on 2011-03-18
> **rupak447 said:**
> Hey Jayme, if you do not mind then I suggest you to change your older version and  have a try with a new version. I am using  ubuntu 10.10 on ma core i3 desktop computer and it really does well.

Hi Saiful,
  
  Thanks for the suggestion, but I've already tried 10.10 and it didn't work either. That's why I was trying 10.04.2. :)

Jayme

---

### Post by sandyd on 2011-03-18
> **Jayme Harris2007 said:**
> Okay I burned the Live CD and tested it on my laptop that is running Windows Vista. I made sure that my first boot option was my DVD and it booted up and seems to run okay. I tried it on the desktop this morning and only got at far as the ubuntu screen with the five dots it froze up at that point. I think I may also have a keyboard error since my **Function, Cap locks and Num locks lights are all flashing.**

Thank again for the help.

Jayme
might be kernel panic.

try choosing "more options" -> nomodeset when booting

---

### Post by Jayme Harris2007 on 2011-03-19
> **sandyd said:**
> might be kernel panic.

try choosing "more options" -> nomodeset when booting

Hi Sandy,

  I'm not sure what you mean by choosing more options. My Ubuntu never gets to a point where I can choose any kinds of options.

Jayme

---

### Post by Rubi1200 on 2011-03-19
When the computer starts and you see the entry for Ubuntu highlighted in the GRUB menu press "e" to edit.

Navigate with the arrow keys and find the line that ends with quiet splash.

Add i915.modeset=1 after quiet splash so it looks like this:

> quiet splash i915.modeset=1Then, "Ctrl" +"x" to boot.

If this helps, we can make it more permanent.

EDIT: sorry, just realized you are still trying to get things going.

When the CD boots press F6 followed by Esc to see the boot line:

>  **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Add the parameter I mentioned above so it looks like this:

>  **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash i915.modeset=1--**
Then Enter to boot.

---

### Post by Jayme Harris2007 on 2011-03-19
> **Rubi1200 said:**
> When the computer starts and you see the entry for Ubuntu highlighted in the GRUB menu press "e" to edit.

Navigate with the arrow keys and find the line that ends with quiet splash.

Add i915.modeset=1 after quiet splash so it looks like this:

Then, "Ctrl" +"x" to boot.

If this helps, we can make it more permanent.

EDIT: sorry, just realized you are still trying to get things going.

When the CD boots press F6 followed by Esc to see the boot line:



Add the parameter I mentioned above so it looks like this:


Then Enter to boot.

Hi Rubi1200,

  Thank you for the suggestions. When I booted up the PC with the Live CD in the drive I never saw a GRUB Menu. It always just went straight to the ubuntu screen. The good new is for some reason the Live CD booted up to the demo or install screen twice the first time I clicked on demo and played around with the program for a bit before there was an error and I had to shut down the PC after some restarts it booted to the demo/install screen and I clicked on Install. It's in the process of installing right now. 

  I appreciate all of the suggestions and will post again after the installation is complete and I've had a chance to check it out.

Jayme

---

### Post by Jayme Harris2007 on 2011-03-20
> **Jayme Harris2007 said:**
> Hi Rubi1200,

  Thank you for the suggestions. When I booted up the PC with the Live CD in the drive I never saw a GRUB Menu. It always just went straight to the ubuntu screen. The good new is for some reason the Live CD booted up to the demo or install screen twice the first time I clicked on demo and played around with the program for a bit before there was an error and I had to shut down the PC after some restarts it booted to the demo/install screen and I clicked on Install. It's in the process of installing right now. 

  I appreciate all of the suggestions and will post again after the installation is complete and I've had a chance to check it out.

Jayme

Well it looks like I spoke to soon. The install got to 45% and then the system froze. I tried to restart the install and the computer wouldn't even read the CD, so I re-formated the hard drive again and started over. This time I got to 39% and got an error message that there was an unrecoverable error. It said that I need to check the disc integrity. How can I do that if it won't install or run. I'm going to run it on my laptop and see what I can see. 

Jayme.

---

### Post by Rubi1200 on 2011-03-20
Hi,
sorry to hear this is such a difficult beginning.

Please do this:

1. start the Ubuntu CD and choose to check the integrity; perhaps another bad burn?

2. afterwards, choose to try not install Ubuntu. Then, go to Applications > Accessories > Terminal and post the output of this command:

```
sudo fdisk -lu
```
lowercase L not 1

---

### Post by Jayme Harris2007 on 2011-03-20
> **Rubi1200 said:**
> Hi,
sorry to hear this is such a difficult beginning.

Please do this:

1. start the Ubuntu CD and choose to check the integrity; perhaps another bad burn?

2. afterwards, choose to try not install Ubuntu. Then, go to Applications > Accessories > Terminal and post the output of this command:

```
sudo fdisk -lu
```
lowercase L not 1

Rubi,

  I got lucky one for time and the CD booted to the install screen. I typed in the command you posted and attached is an image file of the output. I hope you can read it okay. It would be a lot to have to type:)

Jayme

---

### Post by Rubi1200 on 2011-03-20
Okay, I don't really understand what is happening here. 

According to the results of the command you have Ubuntu installed on the computer.

Are you saying that you can't boot into it at all?

There is another thing to do from the LiveCD:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Jayme Harris2007 on 2011-03-20
> **Rubi1200 said:**
> Okay, I don't really understand what is happening here. 

According to the results of the command you have Ubuntu installed on the computer.

Are you saying that you can't boot into it at all?

There is another thing to do from the LiveCD:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


Rubi,

  Thanks again for your help. If I booted the computer without the Live CD up until the time that I was able to get the desktop to install the program to the 45% mark I always got the Windows XP log in/password screen, even though I had formated the drive. After that I wouldn't boot, all I got was a flashing cursor in the upper left corner of the screen. When I tried again with the Live CD it still wouldn't boot so I used a boot disc to start the system and re-formated the HDD again. After that I got it to start the install again with the Live CD and saw that it said I was running ubuntu. I thought great all I have to do is let the CD complete the install. That's when I got to 39% and got the unrecoverable error message.

  Anyway the good news is I'm posting these results from the system in question running from the Live CD. It made it a lot easier to post these results for you.  :)


Jayme

 ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    75,194,367    75,192,320  83 Linux
/dev/sda2          75,196,414    78,163,967     2,967,554   5 Extended
/dev/sda5          75,196,416    78,163,967     2,967,552  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20015856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    20,000,924    20,000,862   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        03c24b6d-1979-4e33-9c15-95836f6c7369   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ae47efcb-af1b-4602-bcde-f73feaf12eca   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2E72-1DF3                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=03c24b6d-1979-4e33-9c15-95836f6c7369 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ae47efcb-af1b-4602-bcde-f73feaf12eca none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  cb 88 9f 11 f5 a0 3f 18  29 b0 5b 04 1d c4 d1 3f  |......?.).[....?|
00000010  18 97 74 41 3f 1d c4 d1  3f 18 83 2c 12 dc 16 1d  |..tA?...?..,....|
00000020  f5 3f 18 91 fa 88 06 11  7c 9a 40 18 d8 71 1d a5  |.?......|.@..q..|
00000030  16 4c 23 41 18 9b 87 a9  0c 16 99 2b 41 18 e0 db  |.L#A.......+A...|
00000040  9c 39 16 3f 05 42 18 d2  a9 99 4b 1d b9 43 42 18  |.9.?.B....K..CB.|
00000050  7d 3d 9f f7 1d 09 59 42  18 41 3f 9c 48 1d 74 a9  |}=....YB.A?.H.t.|
00000060  42 18 a3 25 af 2c 14 9e  ec 42 18 23 9f a2 33 16  |B..%.,...B.#..3.|
00000070  bc 5a 43 18 df b4 30 df  1d 58 ab 43 18 98 68 b2  |.ZC...0..X.C..h.|
00000080  89 16 c6 06 44 18 c8 27  62 83 16 ea 4c 44 18 fd  |....D..'b...LD..|
00000090  5a be a7 11 b3 5c 44 18  bc 12 cf d7 16 07 99 44  |Z....\D........D|
000000a0  18 1d 2d 2f f9 17 d0 9d  44 18 ef ce e7 17 1e fc  |..-/....D.......|
000000b0  d1 44 18 24 b8 0f b1 16  47 db 44 18 d5 58 5b 82  |.D.$....G.D..X[.|
000000c0  1d e7 e1 44 18 29 94 ac  75 1f 2d 0b 45 18 f2 7c  |...D.)..u.-.E..||
000000d0  75 8d 16 d1 56 45 18 ae  7a e2 53 16 d1 56 45 18  |u...VE..z.S..VE.|
000000e0  0e a4 30 9b 1e d1 56 45  18 75 70 8b 9f 17 39 65  |..0...VE.up...9e|
000000f0  45 18 77 87 9d 3b 17 39  65 45 18 c1 0d 4a 8a 11  |E.w..;.9eE...J..|
00000100  aa 9e 45 18 6a 0e 8b d8  1d ce df 45 18 b3 f6 aa  |..E.j......E....|
00000110  e7 16 16 04 46 18 11 2e  6a c7 1d ec 89 46 18 45  |....F...j....F.E|
00000120  43 dd 22 14 38 93 47 18  62 9f 69 6f 14 38 93 47  |C.".8.G.b.io.8.G|
00000130  18 79 95 ec a5 14 38 93  47 18 f6 28 e5 af 14 38  |.y....8.G..(...8|
00000140  93 47 18 a5 3b 3f bc 1d  6b a4 47 18 9b 1d ad 8e  |.G..;?..k.G.....|
00000150  1e ef c7 47 18 3e 78 f6  a0 1d 28 e7 47 18 53 db  |...G.>x...(.G.S.|
00000160  27 47 1e 5a 0b 48 18 2d  8d 26 7b 16 61 b5 48 18  |'G.Z.H.-.&{.a.H.|
00000170  42 f4 87 f0 15 3b 50 49  18 ec 83 c8 ca 18 04 6a  |B....;PI.......j|
00000180  49 18 11 72 d2 fe 16 b5  7f 49 18 a4 e2 66 53 16  |I..r.....I...fS.|
00000190  b5 7f 49 18 ea 76 b1 81  16 c1 ca 4a 18 5e 80 a2  |..I..v.....J.^..|
000001a0  17 11 30 d9 4b 18 12 f3  25 58 1d 84 15 4c 18 52  |..0.K...%X...L.R|
000001b0  5a 4b 90 1d 84 15 4c 18  dc bc 05 cf 1d 34 00 fe  |ZK....L......4..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 48 2d 00 00 00  |...........H-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by Rubi1200 on 2011-03-21
If I am not mistaken, the results indicate a half-installed system.

I want to be careful offering advice about the next step. Therefore, I am going to ask some other users to take a look and offer their perspectives.

---

### Post by coffeecat on 2011-03-21
Hi. I'm one of the other perspectives. :)

> **Rubi1200 said:**
> If I am not mistaken, the results indicate a half-installed system.

I agree. With the live CD session freezing part the way through the installation I personally wouldn't attempt to repair it. A re-install would be quicker. But before you do that, some thoughts.

I believe this is the underlying problem:

> **Jayme Harris2007 said:**
> Video Chip: [COLOR=Red] 82845G[/COLOR]/GL/GE Int Graphics Device (B1-Step)
Visa OEM String Brookdale-G Graphics Chip Accelerated VGA
Video Memory:  832kb.

The Intel 8** series are known to be problematic in recent versions of Ubuntu. If you don't apply the boot parameters Rubi1200 suggested then you get system freezes. Which is what you've seen. As an aside, the problem is worse in Maverick/10.10, so you were right to go with Lucid/10.04.

One for your bookmarks:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

If I read what you've said correctly, sometimes the live CD booted up and sometimes it didn't. You were lucky, as you pointed out, when it did, but then it froze during the installation. You need to add the i915.modeset=1 parameter as Rubi1200 described in post #13 before booting the CD. When you first start the CD you'll see a purple screen with two small icons at the bottom. Tap the space bar, select your language and you are at the live CD boot menu. From there you can press F6 to add "i915.modeset=1".

Hopefully, that will allow you to boot up the CD and install Ubuntu without a system freeze. But once you have Ubuntu installed, you will still need to add  i915.modeset=1 before booting the first time. You can then make the change permanent. Details are under "Workarounds" in that link.

I believe this is the way to go - see what Rubi1200 says - but you'll get indifferent graphics performance on that old Intel chipset even if you avoid system freezes. You don't happen to have a nvidia or ATI graphics card that will fit in that machine? A motherboard of that vintage will likely  have either an AGP or even only a PCI slot for graphics cards - not the newer PCIe. If you do have such a card, post details and we can see whether that would be a better option. Having said that, older nvidia and ATI chipsets can be just as problematic.

---

### Post by Rubi1200 on 2011-03-21
I agree with coffecat that a fresh install would be easier than attempting to fix a half-installed system.

Use the boot parameter to get the LiveCD going and then install.

Let us know what happens please.

---

### Post by Jayme Harris2007 on 2011-03-21
Coffeecat,

  I'm trying to do what you said. I got to the screen and pushed the F6 key then a box comes up that reads: acpi=off, noapic, nolapic, edd=on, nodmraidm, nomidest and Free software only. I hit enter on nomodeset and an X appeared next to it. If I hit enter again the X vanishes. What am I doing wrong.

---

### Post by yellerKat on 2011-03-21
> **Jayme Harris2007 said:**
> Coffeecat,

  I'm trying to do what you said. I got to the screen and pushed the F6 key then a box comes up that reads: acpi=off, noapic, nolapic, edd=on, nodmraidm, nomidest and Free software only. I hit enter on nomodeset and an X appeared next to it. If I hit enter again the X vanishes. What am I doing wrong.

Press ESCape and then enter!

---

### Post by coffeecat on 2011-03-21
> **Jayme Harris2007 said:**
> Coffeecat,

  I'm trying to do what you said. I got to the screen and pushed the F6 key then a box comes up that reads: acpi=off, noapic, nolapic, edd=on, nodmraidm, nomidest and Free software only. I hit enter on nomodeset and an X appeared next to it. If I hit enter again the X vanishes. What am I doing wrong.

I'm going from memory here, and what the link I posted says:

> 
**From the LiveCD:**

 1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu. 
2) Hit Enter to select your language, and then press F6 and then Esc. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Press Enter to boot the LiveCD.I think you forgot to press ESC after F6. If that doesn't work for you, post back and I'll try booting from a 10.04 live CD to see.

---

### Post by Jayme Harris2007 on 2011-03-21
Coffeecat,

  I saw the line on the screen that reads "Check disc for defects" I ran the test and the check found and error in one file. It doesn't tell me which one. I did a hash test on the disc and it came up fine. I've downloaded this file twice from the ubuntu web site. Is there a trusted mirror site that you would suggest that I try.

---

### Post by anthony2010 on 2011-03-21
You dont need two partitions.

If this wer my computer I would go to distrowatch and download 'sysres' which is a gentoo based tool for repairing hard drives. Most of it is in ubuntu too but you cant load it so get that and run it live from the disk.

When you are running it, navigate to the disk utility and run a test on your hard drive. If it passes, format it to ext4 using the same program. Be sure to remove all partitions (assuming you no longer want windows) 

Then once completed, re boot using your ubuntu disk.

That should cure it.

Happy ubuntuing!

---

### Post by Rubi1200 on 2011-03-21
> **Jayme Harris2007 said:**
> Coffeecat,

  I saw the line on the screen that reads "Check disc for defects" I ran the test and the check found and error in one file. It doesn't tell me which one. I did a hash test on the disc and it came up fine. I've downloaded this file twice from the ubuntu web site. Is there a trusted mirror site that you would suggest that I try.
If you checked the integrity, try another CD. Also make sure to burn at the lowest possible speed that your burning software will allow.

This is starting to sound like either a problem with the integrity of the image or the CD itself.

---

### Post by coffeecat on 2011-03-21
> **Jayme Harris2007 said:**
> Coffeecat,

  I saw the line on the screen that reads "Check disc for defects" I ran the test and the check found and error in one file. It doesn't tell me which one. I did a hash test on the disc and it came up fine. I've downloaded this file twice from the ubuntu web site. Is there a trusted mirror site that you would suggest that I try.

If the downloaded ISO passes the md5sum test, then it's OK. No need to go to another mirror. How exactly did you do a hash test on the disc?

> **Rubi1200 said:**
> If you checked the integrity, try another CD. Also make sure to burn at the lowest possible speed that your burning software will allow.

This is starting to sound like either a problem with the integrity of the image or the CD itself.

I'm inclined to agree about the disc. An error on one file is worrying or it could be just a speck of dust.

@Jayme Harris2007, if I were in your situation  I'd simply burn another disc if there was the slightest doubt about its integrity. If you do, don't forget the "i915.modeset=1" business. With your graphics chipset it's fundamental to keep in mind.

---

### Post by Jayme Harris2007 on 2011-03-21
> **coffeecat said:**
> If the downloaded ISO passes the md5sum test, then it's OK. No need to go to another mirror. How exactly did you do a hash test on the disc?



I'm inclined to agree about the disc. An error on one file is worrying or it could be just a speck of dust.

@Jayme Harris2007, if I were in your situation  I'd simply burn another disc if there was the slightest doubt about its integrity. If you do, don't forget the "i915.modeset=1" business. With your graphics chipset it's fundamental to keep in mind.

I found a copy of ubuntu 10.04.2 at softpedia.com and downloaded it. I did a hash test and it matched, I used a program I found online called MD5.exe. I ran the disc and it asked for a login. This is the first time I've seen anything like that. Is there a default login for this screen if it comes up? 

I also installed an AGP nvidia card that I picked up from Micro Center.

---

### Post by Jayme Harris2007 on 2011-03-21
> **anthony2010 said:**
> You dont need two partitions.

If this wer my computer I would go to distrowatch and download 'sysres' which is a gentoo based tool for repairing hard drives. Most of it is in ubuntu too but you cant load it so get that and run it live from the disk.

When you are running it, navigate to the disk utility and run a test on your hard drive. If it passes, format it to ext4 using the same program. Be sure to remove all partitions (assuming you no longer want windows) 

Then once completed, re boot using your ubuntu disk.

That should cure it.


Happy ubuntuing!

Anthony,

  Thank you for the suggestion. I found two different versions sysres_1.0.3_all.deb and sysres_1.0.3.tar.gz. Which one do I use.

Jayme

---

### Post by coffeecat on 2011-03-22
> **Jayme Harris2007 said:**
> I found a copy of ubuntu 10.04.2 at softpedia.com and downloaded it. I did a hash test and it matched, I used a program I found online called MD5.exe. I ran the disc and it asked for a login. This is the first time I've seen anything like that. Is there a default login for this screen if it comes up? 

I also installed an AGP nvidia card that I picked up from Micro Center.

The usual place to download Ubuntu ISOs is at the main Ubuntu site:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

But softpedia seems to be a reputable site, so if the md5sum matches, that's fine.

As far as doing a md5sum check in Windows is concerned, you shouldn't have to login anywhere. This is the Windows section of the Ubuntu documentation page for doing md5sum checks:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

Try winMD5sum as recommended there.

Good news about the nvidia card. Hopefully that will make things easier. Do you know which actual chipset it is?

> **anthony2010 said:**
> You dont need two partitions.

@anthony2010, why do you say that the OP does not need two partitions? **At least** two partitions are needed. Are you suggesting that the OP runs without a swap partition? That is simply bad practice.

> **anthony2010 said:**
> 
That should cure it.

How does running a utility CD which does little more than can be achieved with an Ubuntu live CD help with the OP's two principal problems: a difficult legacy Intel graphics chipset and the possibility of a faulty CD? And anyway, I think the Gentoo based utility from Distrowatch that you are thinking of is sysresccd, not sysres.

@Jayme Harris2007, those sysres files you downloaded won't be of any use. They were an attempt to develop a Windows restore-like utility to Ubuntu, which won't help you. It looks as though there has been no development for over two years:

[https://launchpad.net/sysres](https://launchpad.net/sysres)

---

### Post by Rubi1200 on 2011-03-22
I agree with coffeecat; let's stay focused here and work on the problems we know about rather than the ones that could be potentially created by using outdated or inappropriate tools.

---

### Post by Jayme Harris2007 on 2011-03-22
> **coffeecat said:**
> The usual place to download Ubuntu ISOs is at the main Ubuntu site:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

But softpedia seems to be a reputable site, so if the md5sum matches, that's fine.

As far as doing a md5sum check in Windows is concerned, you shouldn't have to login anywhere. This is the Windows section of the Ubuntu documentation page for doing md5sum checks:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

Try winMD5sum as recommended there.

Good news about the nvidia card. Hopefully that will make things easier. Do you know which actual chipset it is?



@anthony2010, why do you say that the OP does not need two partitions? **At least** two partitions are needed. Are you suggesting that the OP runs without a swap partition? That is simply bad practice.



How does running a utility CD which does little more than can be achieved with an Ubuntu live CD help with the OP's two principal problems: a difficult legacy Intel graphics chipset and the possibility of a faulty CD? And anyway, I think the Gentoo based utility from Distrowatch that you are thinking of is sysresccd, not sysres.

@Jayme Harris2007, those sysres files you downloaded won't be of any use. They were an attempt to develop a Windows restore-like utility to Ubuntu, which won't help you. It looks as though there has been no development for over two years:

[https://launchpad.net/sysres](https://launchpad.net/sysres)

Coffeecat and Rubi,

  I really appreciate all the help. Here's the video card information that I got from my UBCD 

VESA Version: 3.0
Vendor      : NVIDIA Corporation
Product     : NV34 Board - p162-1n
Product Rev : Chip Rev
Software Rev: 1076
Memory (KB) : 131072

For some reason I'm back to the point where the system is freezing up. I tried the i915.modeset=1 but it hasn't seemed to make a difference. Not to mention that ubuntu is asking for a username and password when it does reach a certain level.

Jayme :(

---

### Post by coffeecat on 2011-03-22
> **Jayme Harris2007 said:**
> VESA Version: 3.0
Vendor      : NVIDIA Corporation
Product     : NV34 Board - p162-1n
Product Rev : Chip Rev
Software Rev: 1076
Memory (KB) : 131072

That's probably a Geforce 5200 or thereabouts. It's an old chipset but probably going to be easier to work with than the Intel 845G

> **Jayme Harris2007 said:**
> For some reason I'm back to the point where the system is freezing up. I tried the i915.modeset=1 but it hasn't seemed to make a difference. Not to mention that ubuntu is asking for a username and password when it does reach a certain level.

Is that freezing without adding the i915.modeset=1 parameter? Because i915.modeset=1 is for Intel cards. I think it will produce problems - or make no difference - with nvidia cards. Best to leave it out, and if you are still getting freezing with the nvidida card, then Rubi1200's suggestion that this is a disc problem is getting more and more likely. And... The live system asking you to login with a username and password is almost certainly indicative of a faulty CD. Did you burn a new one or is this the one you got an error with when you ran "check disc for defects"?

---

### Post by Jayme Harris2007 on 2011-03-22
> **coffeecat said:**
> That's probably a Geforce 5200 or thereabouts. It's an old chipset but probably going to be easier to work with than the Intel 845G



Is that freezing without adding the i915.modeset=1 parameter? Because i915.modeset=1 is for Intel cards. I think it will produce problems - or make no difference - with nvidia cards. Best to leave it out, and if you are still getting freezing with the nvidida card, then Rubi1200's suggestion that this is a disc problem is getting more and more likely. And... The live system asking you to login with a username and password is almost certainly indicative of a faulty CD. Did you burn a new one or is this the one you got an error with when you ran "check disc for defects"?

CC,

  You are correct it is a GeForce 5200. It was the lowest price AGP Video card that Micro Center had in stock. I didn't want to spend a whole lot of money on a video card. I've been out of work for over a year, so money is really tight.  

  I was getting the login request on both my original CD that showed a bad file on the first disc test and on the CD that I downloaded from softpedia. Both of the ISO's that I burned these from passed the hash test. I'm pretty sure that these were burned at 8X speed which is the slowest that InfraRecorder will allow.

  I just tried the softpedia CD again without the i915 command and it's locked up on the ubuntu splash screen again. :(


Jayme

---

### Post by coffeecat on 2011-03-22
Sorry to hear that this is not going right for you.

Ideally, I'd prefer to burn at no more than x4, but if this is the slowest InfraRecorder will do, then there's not much you can do about it. I've come across this myself - not being allowed to burn at a really slow speed - it could be to do with the make and specification of the CD rather than the software.

Another thought. I'm sure you have, but just to check. Now that you've fitted the AGP card, have you plugged your monitor VGA cable into the VGA port of the AGP card and not the motherboard VGA port? Sorry to ask such a basic question, but it's a mistake I've made.

If the VGA cable is plugged into the AGP card, it's also worth checking in the BIOS. Most BIOS's should auto-disable the motherboard graphics when you plug a separate card in, but some don't. Have a look through the BIOS and see if there are any settings that you need to change. Sometimes it's not that obvious - sorry.

That's all I can think of at the moment, but I'll post back if I do think of something else. Perhaps Rubi1200 has some other ideas.

---

### Post by Jayme Harris2007 on 2011-03-22
> **coffeecat said:**
> Sorry to hear that this is not going right for you.

Ideally, I'd prefer to burn at no more than x4, but if this is the slowest InfraRecorder will do, then there's not much you can do about it. I've come across this myself - not being allowed to burn at a really slow speed - it could be to do with the make and specification of the CD rather than the software.

Another thought. I'm sure you have, but just to check. Now that you've fitted the AGP card, have you plugged your monitor VGA cable into the VGA port of the AGP card and not the motherboard VGA port? Sorry to ask such a basic question, but it's a mistake I've made.

If the VGA cable is plugged into the AGP card, it's also worth checking in the BIOS. Most BIOS's should auto-disable the motherboard graphics when you plug a separate card in, but some don't. Have a look through the BIOS and see if there are any settings that you need to change. Sometimes it's not that obvious - sorry.

That's all I can think of at the moment, but I'll post back if I do think of something else. Perhaps Rubi1200 has some other ideas.

CC,

  Yes I did make sure to put the monitor into the new AGP card :p  but just to be on the safe side I plugged the monitor into the on board port to make sure that the system disabled that port and it did. I did another burn of the 10.04.2 ISO with NERO and it loaded to the point where it's asking for the username and password. I'm going to hunt around online and see if I can find a program that will let me burn at slower speeds. So far every thing I've found will only let me burn at 8X as the slowest speed.


  Jayme

---

### Post by Jayme Harris2007 on 2011-03-22
I tried making a Live USB drive and the system doesn't read it. I also tried making sure that usb was set on my BIOS but for some reason the system won't accept it when I press the F10 key to save my changes.

Jayme

---

### Post by coffeecat on 2011-03-23
Apologies for not remembering this before, but you probably need the option "nomodeset" to boot with that nvidia chipset. It's been a long time since I've used a nvidia Geforce 5200, and then you didn't need to, but things have changed. I think this is what you do:

```
**From the LiveCD:**

1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu. 
2) Hit Enter to select your language, and then press F6. 
3) Choose "nomodeset" with the enter key.

```**EDIT**: just found this:

[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

It shows you how to add nomodeset with screenshots. It also explains why you need nomodeset for some nvidia cards. If this works and you can install Ubuntu, you'll need to add nomodeset for at least the first boot into the hard drive installation. Once you've installed the proprietary nvidia driver you probably won't need to add nomodeset at each boot, but if you do, there's a way of doing that automatically. <**end of edit**>

As far as your other points are concerned...

So it's Nero that's asking you for a username and password. This is probably some registration/authentication issue that's peculiar to Nero. Sorry I can't help with that. Nero is proprietary software and the free alternatives whether Linux or Windows fill my needs. 

The BurningISOHowto page, here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

... recommends InfraRecorder which you've tried and ISO Recorder, which might be worth trying. However, this minimum 8x speed might be a function of the particular CDRs you are using.

On that note - do you have access to another machine with different hardware? You could use that to test the CDs you've burnt, or use it to burn a CD to try on your machine.

Booting from a USB is a good idea - if it works. I think a machine from when the Intel 845G chipset was current is unlikely to be able to boot from USB, so I'm surprised that there is an option for that in the BIOS. A shame though that the BIOS won't seem to accept the setting.

But... try the nomodeset option in the live CD first. Let us know if that helps.

---

### Post by Jayme Harris2007 on 2011-03-23
> **coffeecat said:**
> Apologies for not remembering this before, but you probably need the option "nomodeset" to boot with that nvidia chipset. It's been a long time since I've used a nvidia Geforce 5200, and then you didn't need to, but things have changed. I think this is what you do:

```
**From the LiveCD:**

1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu. 
2) Hit Enter to select your language, and then press F6. 
3) Choose "nomodeset" with the enter key.

```**EDIT**: just found this:

[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

It shows you how to add nomodeset with screenshots. It also explains why you need nomodeset for some nvidia cards. If this works and you can install Ubuntu, you'll need to add nomodeset for at least the first boot into the hard drive installation. Once you've installed the proprietary nvidia driver you probably won't need to add nomodeset at each boot, but if you do, there's a way of doing that automatically. <**end of edit**>

As far as your other points are concerned...

So it's Nero that's asking you for a username and password. This is probably some registration/authentication issue that's peculiar to Nero. Sorry I can't help with that. Nero is proprietary software and the free alternatives whether Linux or Windows fill my needs. 

The BurningISOHowto page, here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

... recommends InfraRecorder which you've tried and ISO Recorder, which might be worth trying. However, this minimum 8x speed might be a function of the particular CDRs you are using.

On that note - do you have access to another machine with different hardware? You could use that to test the CDs you've burnt, or use it to burn a CD to try on your machine.

Booting from a USB is a good idea - if it works. I think a machine from when the Intel 845G chipset was current is unlikely to be able to boot from USB, so I'm surprised that there is an option for that in the BIOS. A shame though that the BIOS won't seem to accept the setting.

But... try the nomodeset option in the live CD first. Let us know if that helps.

CC,

  Well the nomodeset seemed like it was going to work. The first time I tried it the system installed a driver for the NVIDIA card and seemed to be working. There was a message on the screen that I needed to reboot the system, so I did. It wouldn't reboot. So I reformated the hard drive yet again and now I can't get the nomodeset to work. :confused:

Jayme

---

### Post by coffeecat on 2011-03-23
@Jayme, I'm going to take some time to re-read the thread after I've regenerated myself with some supper, so I may be a few hours yet. I want to remind myself of every step we've taken to make sure we haven't missed anything. I will post back.

---

### Post by Quackers on 2011-03-23
I don't understand something.
In post #38 you said that booting from the disc that you burned with Nero got you as far as the username and password screen. This was without the nomodeset option, yes? Was that after selecting "install ubuntu" or were you just trying to run the live desktop, by selecting "try ubuntu"?
Have you ever loaded the live desktop (try ubuntu)?

---

### Post by Jayme Harris2007 on 2011-03-23
> **Quackers said:**
> I don't understand something.
In post #38 you said that booting from the disc that you burned with Nero got you as far as the username and password screen. This was without the nomodeset option, yes? Was that after selecting "install ubuntu" or were you just trying to run the live desktop, by selecting "try ubuntu"?
Have you ever loaded the live desktop (try ubuntu)?

Hi Quackers,

  Yes I was able to run the Live CD in try it mode a couple of times. There were times when it would run for a while and then freeze up and other times when I would get to the screen to choose try or install and I would pick install. As I mentioned in one of my posts I actually got it to install to 45% one time before it locked up. At this time I have three different Love CDs of ubuntu 10.04.2 They all pass a hash test and they all run in test mode on my Toshiba laptop.

  Any suggestion you might have would be appreciated.

Jayme

---

### Post by Jayme Harris2007 on 2011-03-23
> **coffeecat said:**
> @Jayme, I'm going to take some time to re-read the thread after I've regenerated myself with some supper, so I may be a few hours yet. I want to remind myself of every step we've taken to make sure we haven't missed anything. I will post back.

Okay CC,

  Let me know if there is any information I can try to get for you. Thank you again.

Jayme

---

### Post by Quackers on 2011-03-23
As you have reformatted a few times, I presume there is no other operating system installed?
If that is the case, where are the downloaded iso's stored? My point is, could you access the iso files from the Ubuntu live desktop?

---

### Post by Jayme Harris2007 on 2011-03-23
> **Quackers said:**
> As you have reformatted a few times, I presume there is no other operating system installed?
If that is the case, where are the downloaded iso's stored? My point is, could you access the iso files from the Ubuntu live desktop?

The ISO's are on my Toshiba Laptop. The same unit I'm using to type this post. :o

Jayme

---

### Post by Quackers on 2011-03-23
Thanks.
What I was thinking is if the iso can be made available to the live cd (maybe on a usb flash drive) it can then be burned to a disc using Brasero. It's just another way of burning the disc, rather than keep using the same program. It may give a different result.

Edit Actually that makes no sense at all, as the cd drive would be in use already! Sorry.
We need to get an iso burned to a disc so that it will pass the error check.

---

### Post by coffeecat on 2011-03-23
@Jayme, let's just clarify a couple of things before we move on to make sure I'm understanding you correctly.
[B]
Checking the md5sum of the ISO.[/B] Earlier in the thread you encountered a problem with a Windows utility for checking md5sums called MD5.exe. So I posted this link:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

And suggested you tried winMD5Sum as recommended there. Were you able to and did the ISO pass the md5sum check?

**Burning and Checking the CD.** You say you have three CDS which pass the hash test (your words) and which work in your Toshiba laptop. What exactly do you mean by passing the hash test. Have a look at the screenshot of the live CD menu in this:

[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Do you mean you are choosing the third menu item, "Check disc for defects"?

If it's yes to both then we must assume the CDs are OK and look elsewhere for why you are still getting problems. So....

> **Jayme Harris2007 said:**
> Well the nomodeset seemed like it was going to work. The first time I tried it the system installed a driver for the NVIDIA card and seemed to be working. There was a message on the screen that I needed to reboot the system, so I did. It wouldn't reboot. So I reformated the hard drive yet again and now I can't get the nomodeset to work. :confused:

I think I follow that, but let's clarify again. You applied nomodeset to the live CD session and it booted. Correct? You were able to install a system without the live CD freezing. Correct? You were then able to boot into the installed system by adding the nomodeset option at the grub menu. Correct? You then installed the proprietary nvidia driver from System > Administration > Hardware Drivers. Correct? But when you rebooted with the proprietary driver installed it wouldn't reboot. What exactly happened when you tried to reboot? (Sorry about all the "corrects?". It sounds a bit brusque but I want to be clear over those points. :))

Also - you say that now you can't get nomodeset to work. Do you mean with the live CD? Because if that is so I am beginning to wonder if there is a hardware problem with this desktop machine. Perhaps faulty RAM, which is possible because Windows and Linux use RAM in different ways, and Linux is more likely to encounter a faulty bit in the upper registers. By the way, how much RAM is in that machine? I don't think that's been mentioned. Or perhaps even a failing optical drive. That's a possibility too. Don't act on these suggestions just yet - I'm simply voicing possibilities that we need to consider

I'd like to see your answers to all my "correct?" questions because there might be a clue there, but if not I do have another suggestion to get you going on that machine. I'll voice it now so that Quackers can comment, but don't try it just yet.

The suggestion is to use the alternate CD to install Ubuntu. The alternate CD has an old-fashioned text interface installer. It's not pretty but it's not that difficult to use. One advantage is that you are not going to trip over this graphics card nomodeset problem while using the alternate CD, which means that you can be fairly confident you can install without the installer freezing on you. You would then have to apply the nomodeset option to boot into the hard drive, but I would then propose postponing installing the proprietary nvidia driver until you can convince yourself that you can boot reliably into Ubuntu with the default open source driver (called 'nouveau' for nvidia cards). @Quackers, what do you think?

---

### Post by Jayme Harris2007 on 2011-03-23
CC,

  Before I answer all of your corrects. Let me just say "IT'S ALIVE" I shut the desktop down at the power supply and let it sit for a while. I then booted it back up and added the nomodeset after pressing the F6 key. The system automatically asked me if I wanted to install the NVIDIA driver and I said yes. This time after the install I didn't do the reboot as suggested and installed the OS it installed 100%. I rebooted the system and got a message that it was running in low graphics mode and it locked up again. I shut it down at the power supply and went and ran sum errands. When I got back I read your email and figured I try again before answering. I got the low graphics message again and this time it gave me the option to run in low graphics for one session. I followed your directions in the last post System>Administration>Hardware Drivers to install the NVIDIA driver. I'm getting some error messages of things that aren't loading correctly, but at least it boots up and runs. I'll post a list of the error messages I'm getting and maybe you can point me in a direction to get them fixed as well. 

Thanks to all of you for not giving up on me. :)

Jayme

---

### Post by coffeecat on 2011-03-23
OK, it's getting late here so I may not be able to respond to your next post until the morning (local time here). If you are in Western USA I guess you're about 6-8 hours behind where we are here.

Whatever - I can see now that there is one mistake you made, but it probably doesn't matter now. You can't install the proprietary driver in the live CD session. Or rather, you can, but it's pointless. Anything you install in the live session is saved in volatile memory and is lost when you power down or reboot. And, of course, since you have to reboot to activate the proprietary driver.... I think you get where this is leading to. :)

FWIW the routine I would advise is:

1 - Boot up live CD. Ignore nag message concerning proprietary driver.

2 - Install system.

3 - Reboot into installed system. Ignore nag message concerning proprietary driver. :wink:

4 - Update newly installed system and install some extra apps if you want to. Ignore nag message concerning proprietary driver. :p

5 - Use the system and reboot a few times to ensure it is stable.

6 - Then, and only then, install proprietary driver. The nag message has probably given up by now.

Anyway, you've installed the proprietary driver now, so that’s all theoretical. I'll have a look at your error messages after you've posted them.

Good luck!

---

### Post by Jayme Harris2007 on 2011-03-23
I should have guessed that my troubles weren't over, just because I finally got the OS installed. I was trying to run a system test when the system locked up again. I wouldn't think that it is a RAM issue. The system has 512MB of RAM and I ran a memory test using my Ultimate Boot CD and everything passed with no errors.

Jayme

---

### Post by Rubi1200 on 2011-03-24
> **Jayme Harris2007 said:**
> I should have guessed that my troubles weren't over, just because I finally got the OS installed. I was trying to run a system test when the system locked up again. I wouldn't think that it is a RAM issue. The system has 512MB of RAM and I ran a memory test using my Ultimate Boot CD and everything passed with no errors.

Jayme
Sorry to hear about these continued troubles.

All things considered, you might want to give one of the other lighter Ubuntu versions a try.

The reason I suggest this is because even though 512MB of RAM *should *be enough, perhaps it is not on your particular computer.

My recommendation would be to give Lubuntu a go:
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by coffeecat on 2011-03-24
> **Jayme Harris2007 said:**
> I should have guessed that my troubles weren't over, just because I finally got the OS installed. I was trying to run a system test when the system locked up again. I wouldn't think that it is a RAM issue. The system has 512MB of RAM and I ran a memory test using my Ultimate Boot CD and everything passed with no errors.

Two points. Unfortunately, it can take a long time to detect RAM errors with memtest. Sometimes errors show up only occasionally and you can run memtest repeatedly  without seeing any. I've seen this myself. The only thing you can be sure of is that if you see errors with memtest, you have faulty RAM. But if you don't see errors you may or may not have faulty RAM.

What was the system test you were running when the system locked?

But most importantly, I want to focus on the nvidia card and the nomodeset option. Please tell us whether you have the proprietary driver installed and whether you were using the nomodeset option. I was hoping that you would install the system and not install the proprietary driver so that we could see whether the system was stable or not using the nomodeset option. If it wasn't then there would have been no point installing the proprietary nvidia driver, and we would need to look for a cause of instability elsewhere.

---

### Post by Jayme Harris2007 on 2011-03-25
> **coffeecat said:**
> Two points. Unfortunately, it can take a long time to detect RAM errors with memtest. Sometimes errors show up only occasionally and you can run memtest repeatedly  without seeing any. I've seen this myself. The only thing you can be sure of is that if you see errors with memtest, you have faulty RAM. But if you don't see errors you may or may not have faulty RAM.

What was the system test you were running when the system locked?

But most importantly, I want to focus on the nvidia card and the nomodeset option. Please tell us whether you have the proprietary driver installed and whether you were using the nomodeset option. I was hoping that you would install the system and not install the proprietary driver so that we could see whether the system was stable or not using the nomodeset option. If it wasn't then there would have been no point installing the proprietary nvidia driver, and we would need to look for a cause of instability elsewhere.

Hi CC,

  I took some time away from this yesterday and ran a bunch of errands. At Rubi's suggestion I've tried some other distributions to see if something else might work. I've tried kubuntu, lubuntu, linuxmint and opengeu. Opengeu was the only one I could get to run from the LiveCD. I've come to the conclusion that it is a hardware problem, because all of the aforementioned CD's will run on a RAID box that I have here. 

  Another strange thing happened this morning. I turned on the PC to remove the linuxmint CD and the system continued to boot and ubuntu 10.04 loaded. I thought this was strange because I had reformated the C: drive since I couldn't get it to boot correctly after it installed. At this point I installed all the updates and did a reboot. Now It's booting and freezing up. I'm going to check and see if the RAM in the RAID systems is the same and try it. I may also try the video card from the RAID unit.  I'll let you know what happens.

Jayme

---

### Post by Rubi1200 on 2011-03-25
This is actually progress believe it or not. And, it is becoming more apparent that it must be hardware related and that something on the computer in question is struggling.

Keep us informed so we can try and help you further.

---

### Post by cmcanulty on 2011-03-25
Also try installing it from a USB flash drive in case your cd drive is flaky use unetbootin to download an image, very easy
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by coffeecat on 2011-03-25
> **Rubi1200 said:**
> This is actually progress believe it or not.

I agree. :)

Hardware problems can be very frustrating - if this is what it is. This has been  a wretched journey for you - you have my sympathy. You are right to try a different video card. RAM, graphics card and PSU are the three things I would look at, and in that order, with this sort of problem. Sorry to be a Jeremiah by mentioning the PSU, but they do fail and ones in the process of failing can cause odd symptoms.

> **cmcanulty said:**
> Also try installing it from a USB flash drive in case your cd drive is flaky use unetbootin to download an image, very easy
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Nice idea, but Jayme's ahead of you. See post #39.

---

### Post by Jayme Harris2007 on 2011-03-25
> **cmcanulty said:**
> Also try installing it from a USB flash drive in case your cd drive is flaky use unetbootin to download an image, very easy
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hi camcanulty,

  Welcome to my problems :P.  I've already tried booting from a Live USB. For some reason known only to the computer Gremlins my system won't allow me to make any changes to my BIOS, so I'm not able to set the USB as a bootable drive, when I press the F10 key to save my changes it's like it doesn't even exist it will accept all other key presses except the F10.

Jayme

---

### Post by Jayme Harris2007 on 2011-03-25
> **coffeecat said:**
> I agree. :)

Hardware problems can be very frustrating - if this is what it is. This has been  a wretched journey for you - you have my sympathy. You are right to try a different video card. RAM, graphics card and PSU are the three things I would look at, and in that order, with this sort of problem. Sorry to be a Jeremiah by mentioning the PSU, but they do fail and ones in the process of failing can cause odd symptoms.



Nice idea, but Jayme's ahead of you. See post #39.

Swaping out the video card didn't help. I found some specs. online for the motherboard and it will take up to 2GB of DDR333 (PC2700). Microcenter has some for 16.99 each, so I'm going to go and pick some up. I'll let you know the results. 

Jayme

---

### Post by Quackers on 2011-03-25
Excuse my late intervention here, but have you tried resetting the bios to default settings? There will be an option to do that. Then re-enter the bios and try changing settings again. Sometimes bioses can get mixed up.

---

### Post by Jayme Harris2007 on 2011-03-25
> **Quackers said:**
> Excuse my late intervention here, but have you tried resetting the bios to default settings? There will be an option to do that. Then re-enter the bios and try changing settings again. Sometimes bioses can get mixed up.

Quackers,

Thanks for the suggestion. I may try that if I run into more issues. 

Now here's an update: NEVER EVER ASSUME ANYTHING :p. I assumed that I was running 2 256MB DDR333 (PC2700) RAM chips, because my BIOS said I was only running with 512MB. If I had looked closer I would have noticed that the BIOS was only picking up one bank of memory. It turns out that one of the little white levers was messed up and not letting the second 512MB RAM chip seat correctly. I found this out when I got back from Microcenter. I actually broke the little white lever trying to get it to seat correctly. After removing the broken pieces the memory now seats correctly and I'm running a full 1GB of RAM. ubuntu likes that much better. 

I'm in the process right now of rebooting the system a few times to see if it's going to work that way. Any suggestion on what I should do or run to check system stability and also can one of you tell me how to set up the system so I only need to type in my password at login and not every time the screen goes to sleep?   Knock on wood I think we're getting real close. :p

Jayme

---

### Post by coffeecat on 2011-03-25
> **Jayme Harris2007 said:**
> It turns out that one of the little white levers was messed up and not letting the second 512MB RAM chip seat correctly.



Now that's *very* interesting. There was probably  an intermittent connection with the second stick which would have played havoc with system stability.

> **Jayme Harris2007 said:**
> Any suggestion on what I should do or run to check system stability

I would think just to run the system and see how you get on. Unless one of m'learned friends has a better idea! :)

> **Jayme Harris2007 said:**
>  and also can one of you tell me how to set up the system so I only need to type in my password at login and not every time the screen goes to sleep?

System > Preferences > Screensaver. Untick the 'lock screen when screensaver is active' tickbox. You're not alone. That setting seems to irritate most people! Myself included. :)

---

### Post by Jayme Harris2007 on 2011-03-25
> **coffeecat said:**
> Not that's *very* interesting. There was probably  an intermittent connection with the second stick which would have played havoc with system stability.



I would think just to run the system and see how you get on. Unless one of m'learned friends has a better idea! :)



System > Preferences > Screensaver. Untick the 'lock screen when screensaver is active' tickbox. You're not alone. That setting seems to irritate most people! Myself included. :)


I did a warm boot a cold boot and a freezing boot :P, I shut down the power supply for 10 seconds and then turned the system back on. It rebooted all three times. Yea!. I decided a good test would be to run some videos. I downloaded the flash plug in for firefox and went to the hulu site. The video was a bit choppy, but that may be a streaming issue. Right now I'm watching an MP4 file of Star Gate Universe. Its playing great. 

I'll go and make that change to the screen saver. Thanks to everyone for all the help. 

Jayme

---

### Post by coffeecat on 2011-03-25
Good luck! I hope the system continues to work well. 

By the way, a silly typo in my last post which I've corrected. "Not that's very interesting." What were my fingers thinking of? "**Now** that's very interesting."

---

### Post by Quackers on 2011-03-25
I've got my fingers crossed too :-)
Bad-hair day coffeecat?

---

### Post by Jayme Harris2007 on 2011-03-25
> **coffeecat said:**
> Good luck! I hope the system continues to work well. 

By the way, a silly typo in my last post which I've corrected. "Not that's very interesting." What were my fingers thinking of? "**Now** that's very interesting."

I'll give it a couple days before I mark the thread as solved. Thanks again. :popcorn:

Jayme

---

### Post by cmcanulty on 2011-03-25
Also look at power options. Ubuntu tweak will let you disable lock screen entirely.[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by Rubi1200 on 2011-03-26
> **Jayme Harris2007 said:**
> I'll give it a couple days before I mark the thread as solved. Thanks again. :popcorn:

Jayme
Sorry for crashing the party so late. I am really pleased you managed to get things sorted out. What a learning experience for us all.

Enjoy :)

---

### Post by Jayme Harris2007 on 2011-03-27
> **Rubi1200 said:**
> Sorry for crashing the party so late. I am really pleased you managed to get things sorted out. What a learning experience for us all.

Enjoy :)

I just wanted to thank everyone again for all the help getting ubuntu up an running on my desktop computer. I've installed the latest version of WINE on the system and have gotten a couple of hidden object games to run in it. I played one for a few hours the other day and didn't have any issues.

Jayme

---


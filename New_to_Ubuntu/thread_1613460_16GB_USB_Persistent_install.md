---
title: "16GB USB Persistent install"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by k33bz on 2010-11-04
I am getting this problem:

```
keebler@mobile:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aec6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38543   309593088   83  Linux
/dev/sda2           38543       38914     2975744+   5  Extended
/dev/sda5           38543       38914     2975744   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
64 heads, 32 sectors/track, 15272 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2501     2561008    b  W95 FAT32
/dev/sdb2            2502       15272    13077504   83  Linux
keebler@mobile:~$ sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sdb2
mke2fs 1.41.11 (14-Mar-2010)
Could not stat /dev/sdb2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
keebler@mobile:~$ 

```

I am following this guide [here]("http://www.infosecramblings.com/backtrack/backtrack-4-usbpersistent-changesnessus/#tools")

---

### Post by bioterror on 2010-11-04
Looks so complicated.
You could just boot LiveCD, plug your stick in, wait 'till it's mounted and start installer and install on that stick.

Ofcourse you loose ability to make installations from the pendrive. But so what, you've got a 100% persistent usb pendrive linux which does not go bonkers when you upgrade kernels.

---

### Post by baldy4eva on 2010-11-04
> **bioterror said:**
> Looks so complicated.
You could just boot LiveCD, plug your stick in, wait 'till it's mounted and start installer and install on that stick.


That's what worked for me.

---

### Post by k33bz on 2010-11-04
ya that is what I figured I will be doing next, now off to burn iso to a dvd.

---

### Post by wilee-nilee on 2010-11-04
That is a interesting link it makes sense that it should work. I have to study for class but I will look later and see if I see anything, or have any ideas. That was a good find.;)

---

### Post by oldfred on 2010-11-04
I do not see anything wrong.

You should also be able to use gparted as long as the flash drive is not mounted. Gparted is not normally installed in Ubuntu as you cannot work with the mounted system partition. I still use synaptic to install gparted as I like to see what partitions are where and can use it for unmount partitions.

But if you have a 16GB flash drive why waste it on one persistent install. 

I have two flash drives with installs. My 4GB is FAT32 but still have grub2 installed and as many ISOs as I can fit. Grub2 lets me loop mount any of the ISOs. Not sure if BT4 allows loop mounting but there are work arounds for that also.
My16GB flash drive is a full install of Ubuntu and I left 8GB for /home. I could and may install some of the ISO to the 16GB flash also.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 


Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
partitions aligned with flash erase block size
If we pre-partition our thumb drives with GParted before we start the Ubuntu installer, we can create a partition beginning in sector 2048 by removing the check mark from the 'Round to cylinders' checkbox, and then set the spinbox for 'Space preceding' to 1 MiB.
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)
[http://fenidik.blogspot.com/2010/03/ext4-disable-journal.html](http://fenidik.blogspot.com/2010/03/ext4-disable-journal.html)

---

### Post by k33bz on 2010-11-04
> **oldfred said:**
> I do not see anything wrong.

You should also be able to use gparted as long as the flash drive is not mounted. Gparted is not normally installed in Ubuntu as you cannot work with the mounted system partition. I still use synaptic to install gparted as I like to see what partitions are where and can use it for unmount partitions.

But if you have a 16GB flash drive why waste it on one persistent install. 

I have two flash drives with installs. My 4GB is FAT32 but still have grub2 installed and as many ISOs as I can fit. Grub2 lets me loop mount any of the ISOs. Not sure if BT4 allows loop mounting but there are work arounds for that also.
My16GB flash drive is a full install of Ubuntu and I left 8GB for /home. I could and may install some of the ISO to the 16GB flash also.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 


Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
partitions aligned with flash erase block size
If we pre-partition our thumb drives with GParted before we start the Ubuntu installer, we can create a partition beginning in sector 2048 by removing the check mark from the 'Round to cylinders' checkbox, and then set the spinbox for 'Space preceding' to 1 MiB.
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)
[http://fenidik.blogspot.com/2010/03/ext4-disable-journal.html](http://fenidik.blogspot.com/2010/03/ext4-disable-journal.html)

The original method I was going to use was with gpart and unetbootin, however I was having problems doing that way, so I figured I look into a way to do it manually. Sometimes I find it better to understand what is going on, also in my experience doing things by cmd line you usually get better results.

Now as far as it being 16gb thumbdrive and only 1 OS, that is the way I was setting it up now, then adding onto it at a later date, after shrinking the partition of course :)

---

### Post by k33bz on 2010-11-04
ok new problem,

I thought maybe at first I was getting bad downloads or bad burns, so I tried a different live disc that I have that I know works. However I am still unable to boot into it. Before you suggest, yes I went in my bios to change teh boot order for my cd/dvd player to boot into. I tried several disc. The disc reader itself reads and burns fine, however it seems I am unable to boot into it now. (Before I could). I also have a dvd burner that I occasional use (external) for times I work with my wifes laptop (which her reader dont work at all) or on my kids eeepc. But it seems that my laptop dont even notice that it is plugged in during the boot up process. (weird).

I have not flashed my bios, and everything use to work flawlessly, now booting into other devices other than the internal HDD (not sure on live usb disc as of yet, this would be my first). However all these devices work fine after everything is loaded.

What are my options? If any?

---

### Post by oldfred on 2010-11-04
Have heard of a few systems that required both BIOS and one time boot key to change boot order.

Are all the connections, power & signal firmly connected? I do not like to open my desktop as the minute I touch one thing I manage to loosen several others.:)

---

### Post by wilee-nilee on 2010-11-04
I always have a plop cd sitting around to check for problems even on a computer that has usb boot.
[http://www.plop.at/](http://www.plop.at/)

---

### Post by k33bz on 2010-11-04
> **oldfred said:**
> Have heard of a few systems that required both BIOS and one time boot key to change boot order.

Are all the connections, power & signal firmly connected? I do not like to open my desktop as the minute I touch one thing I manage to loosen several others.:)

I have never had a problem booting up before from a live cd or dvd. But it would seem that my drive is failing, after a while I started to get some dvds and cds to boot. But had boot errors involved. So my best guess is to go out and buy another internal cd/dvd burner for my laptop. yippeee (that was sarcastics)

---

### Post by k33bz on 2010-11-05
Ok, I am now able to boot from my optical drive, the lens was dirty, so I had cleaned it.

But I still have a problem of installing BT4 onto a thumb drive, I tried to install but sometimes at 24% it stalls and says that the HDD (talking about the thumbdrive) may be bad or I need to move to a cooler place. Well I checked the thumbdrive with fsck and it reported back that the drive is still good. I tried in several cooler places, hell even outside and its cold out there, yet I still get it stuck at 24% and sometimes at 55%. Have never gotten any further than 55%.

I am going to try a few other methods of installing to the thumb drive and see where I get.

---

### Post by oldfred on 2010-11-05
I manually created my flash with grub. The only difficulty was finding the correct boot stanza as you have to manually add each entry into grub.cfg.

But this script automates the entire process. I just checked and bt4 is one on its list.
**MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk**
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by beew on 2010-11-06
For multiboot you may also want to check this out.
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Nice and easy to use tool. The best thing is it is completely integrated into Ubuntu's program manager. Once installed  it gets frequently updated through Synaptic (just like adding a PPA), though perhaps may not be as customisable as oldfred's script.

---

### Post by k33bz on 2010-11-06
Ok I have it all installed on there, FINALLY, but grrrrrrrrrrrrrr, I come across a glitch when I try to boot from the USB. I get a grub error 25, of course that is after it hangs for awhile on booting up the grub.

Not sure how I can fix this

---

### Post by k33bz on 2010-11-06
bump

---

### Post by oldfred on 2010-11-06
I thought all the error numbers were from old grub legacy.

Plug in the flash and run the boot info script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by k33bz on 2010-11-06
> **oldfred said:**
> I thought all the error numbers were from old grub legacy.

Plug in the flash and run the boot info script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

That I have not tried as of yet, may do so soon. I tried this other method I had found on these forums. Dont remember the link. But it was basically running from live disc and go into grub and set some paremters up. however that did not work for me.

```

sudo grub

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/fat_stage1_5" exists... yes
 Running "embed /boot/grub/fat_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>quit

```

then reboot, however I still get an error 25

Is there something I am doing wrong?

A little note, this is with my Laptops internal HDD out, just making sure I was going to be editing the right grub. With the internal HDD in it displays (hd1,0)

---

### Post by k33bz on 2010-11-06
RESULTS.txt
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

hda: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 16.0 GB, 16013852672 bytes
64 heads, 32 sectors/track, 15272 cylinders, total 31277056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  32     5,122,047     5,122,016   b W95 FAT32
/dev/sda2           5,122,048    31,277,055    26,155,008  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda                                                iso9660    BT4                           
/dev/loop0                                              squashfs                                 
/dev/sda1        4CD4-DFC5                              vfat                                     
/dev/sda2        3df72ee6-bc92-46bc-8acf-55a01e899405   ext3       casper-rw                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/hda         /media/cdrom0            iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 4

# Boot automatically after 30 secs.
timeout 30

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1

=================== sda1: Location of files loaded by Grub: ===================


   2.0GB: boot/grub/menu.lst
   2.0GB: boot/grub/stage2
    .0GB: boot/initrd800.gz
    .0GB: boot/initrdfr.gz
    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz

=========================== hda/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1

==================== hda: Location of files loaded by Grub: ====================


   2.0GB: boot/grub/menu.lst
   2.0GB: boot/initrd800.gz
   2.0GB: boot/initrdfr.gz
   1.9GB: boot/initrd.gz
   2.0GB: boot/vmlinuz

```

---

### Post by k33bz on 2010-11-06
Looks like it is saying it can not find an OS on sda1 like it should. I had rsync the entire cdrom0 to /mnt/sda1 before hand. And to just double check:

```

root@bt:/media# fdisk -l

Disk /dev/sda: 16.0 GB, 16013852672 bytes
64 heads, 32 sectors/track, 15272 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2501     2561008    b  W95 FAT32
/dev/sda2            2502       15272    13077504   83  Linux
root@bt:/media# mkdir /mnt/sda1
root@bt:/media# mount -t vfat /dev/sda1 /mnt/sda1
root@bt:/media# cd /mnt/sda1
root@bt:/mnt/sda1# ls
boot  boot.catalog  casper  md5sum.txt
root@bt:/mnt/sda1#      
```

am following these steps that are here [www.techwarelabs.com/how-to-installing-backtrack-4-r1-to-a-usb-flash-drive/](www.techwarelabs.com/how-to-installing-backtrack-4-r1-to-a-usb-flash-drive/)

---

### Post by oldfred on 2010-11-06
I do not think I have run across error 25 before.

[http://members.iinet.net.au/~herman546/p15.html#25](http://members.iinet.net.au/~herman546/p15.html#25)

---

### Post by k33bz on 2010-11-06
Well next I think I am going to try the multi boot script that was mentioned here before hand. I will let yall know i that works, maybe I can find a way to make it persistant.

---

### Post by k33bz on 2010-11-06
ok, so I have tried that script, but with that script after I boot up from USB I get a error 17 :(

---

### Post by oldfred on 2010-11-07
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

Error numbers are still from old grub legacy. Did you not install grub2?

---

### Post by k33bz on 2010-11-08
Ok, so since I have been following other's tutorials, and I have not seen that in any the tutorials I have been doing, how do I install grub2 to USB?

---

### Post by oldfred on 2010-11-08
I thought you were following the instructions in Post #6 on grub2 and USB flash drives.

---

### Post by k33bz on 2010-11-08
> **oldfred said:**
> I thought you were following the instructions in Post #6 on grub2 and USB flash drives.

Actually I was following the instructions on the ones I posted earlier. But now that I see that you have posted that link, I am going to be doing that one. Sorry :(

---

### Post by k33bz on 2010-11-08
Ok I followed the steps from [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB) surprisingly it is the same steps I was following before, with more details though. Which is good. 

However I come across a question. on the grub.cfg file, do I change it to resemble more of the menu.lst?

PS-- I went over both of the links described in the links that oldfred posted. To me it seems that it will just support LiveCD/DVD with no persistancy. Which I want it to be persistant. So this is what I have done so far, I created my partitions with fdisk, there is 2 partitions. First one /dev/sdb1 is a fat32 with the liveDVD rysnc to it. Partition 2 /dev/sdb2 is an ext3 with journaling labled casper-rw. 

I followed the steps from oldfred's post #6 on this thread to install grub2, which is installed. I am no longer getting grub errors, however I am getting errors still. I am guessing it is because I dont have grub.cfg file edited right. I dont remember what the errors are, but there are 3 of them.
The last error displayed was that it does not recognize the command terminal, or something of that nature. I will be re-editing this here soon to display all 3 of the errors.

error: out of disk
error: no suitable mode found
error: unknown command "terminal"

Just noticed that it also provided a few more errors, right before It decided to boot from my internal HDD, went by to fast for me to catch them. I saw at least 2 i/o buffer errors though.

Should I use gpart to make /dev/sdb1 larger, it is currently at +2500M

---

### Post by oldfred on 2010-11-08
Since I did it manually I had to search all over to find correct boot stanzas for each ISO I was booting. The link in post #6 gives several examples.

I just created and added the boot stanzas to grub.cfg. The other consistency issue was I named my subdirectory /boot/ISOs, others use iso or ISO and I had to make sure I had it correct for my path.

I did not make any Iso boots persistent as I used my 4GB for installs and repair ISOs and my 16GB for a full install of Ubuntu.

---

### Post by k33bz on 2010-11-08
> **oldfred said:**
> Since I did it manually I had to search all over to find correct boot stanzas for each ISO I was booting. The link in post #6 gives several examples.

I just created and added the boot stanzas to grub.cfg. The other consistency issue was I named my subdirectory /boot/ISOs, others use iso or ISO and I had to make sure I had it correct for my path.

I did not make any Iso boots persistent as I used my 4GB for installs and repair ISOs and my 16GB for a full install of Ubuntu.

For some reason I cant get a full install on this USB, no matter how I try, which is what I was trying to do. Either that make it where it is persistent, which is also causing problems. I think maybe it is the type of USB ThumbDrive I am using. The type I am using is Patriot XT 16GB. If that one will not work, what ones will?

---

### Post by k33bz on 2010-11-08
> **oldfred said:**
> I manually created my flash with grub. The only difficulty was finding the correct boot stanza as you have to manually add each entry into grub.cfg.

But this script automates the entire process. I just checked and bt4 is one on its list.
**MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk**
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Also makes me wonder that this link did not work for me. Matter fact after doing that one, my USB was labeled live-disc and was at 13GB, running fdisk -l didnt show any other mounts from sdbX. And looking inside live-disc did not show anything, even with cntrl+h. Although I must admit I did not do ls -a.

---

### Post by oldfred on 2010-11-08
I have heard where some flash drives have settings that you have to remove. I have always totally reformated with gparted and never had any issues. I did not try to leave a FAT partition at the beginning either. 

If a full install it should be just like any other install to a second drive. You do have to use manual install to get the combo box that lets you choose to install grub2 to the MBR of the flash drive or else it installs to the main drive sda.

---

### Post by k33bz on 2010-11-08
> **oldfred said:**
> I have heard where some flash drives have settings that you have to remove. I have always totally reformated with gparted and never had any issues. I did not try to leave a FAT partition at the beginning either. 

If a full install it should be just like any other install to a second drive. You do have to use manual install to get the combo box that lets you choose to install grub2 to the MBR of the flash drive or else it installs to the main drive sda.

I tried it that way, yet it fails, just to be on the safe side of other things I even completely removed my laptops internal HDD. That way there would be no mistakes. I just got through doing the entire process of the link you left me with installing Grub2 from here
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

So I am about to reboot and boot into the USB with the ISO present, wish me luck :)

Well that proved unsuccessful, it started to booted up into the USB, was watching the light on it blink for a bit. However it never did anything, lights stopped blinking for a good lil bit, and screen stayed on with a blinking cursor. Nothing else. So maybe I am doing something wrong, here is my grub.cfg
```

menuentry "BT4R1" {
    set isofile="/boot/isos/bt4-r1.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

```
iso is located at /dev/sdb1/boot/isos/bt4-r1.iso

Just a little side note, according to my computer's BIOS it states my USB as ```
Patriot (16GB USB HDD)
```
So is there possibly an area of the USB drive that displays that info that I cant seem to locate or re-format. To my understanding I have re-formatted the entire USB Drive both with fdisk and mkfs. as well as formatting in CLI, including using gparted. 

Later, I will be trying to reformat my USB repeat steps above placing ISO file within, as well as not including a fat32 in the beginning, since oldfred stated he does not have that there.

> **oldfred said:**
> I have heard where some flash drives have settings that you have to remove.
where would those settings be?

I think I might have found one of my problems. Checked in synaptic to see if grub2 was the one installed on my computer. However it shows that it is not installed, I have grub-common, & grub-pc installed. I guess it was foolish of me to assume that I had grb2 installed.




Now going to be trying this: [http://this.is.thoughtcrime.org.nz/multi-boot-bt4-from-usb-with-grub2](http://this.is.thoughtcrime.org.nz/multi-boot-bt4-from-usb-with-grub2)

---

### Post by oldfred on 2010-11-08
grub-pc is the name of grub2 and grub common seems to be used by both grub legacy & grub2.

Just as a test I would copy one of the standard ISOs Ubuntu or gparted that were in the link & copy the grub boot stanza. Or use mine, just check path as mine is /boot/ISOs and caps or small letter matter in Linux.

These were mine but I have actually only booted the first 3 or 4 including gparted, system rescue & parted magic. I use this for all my installs by removing an old Ubuntu ISO & adding the new with edits to grub for the new name.
```

menuentry "Ubuntu 10.04 64bit" {
    set isofile="/boot/ISOs/ubuntu-10.04-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.10 64 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 9.10 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.04 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

menuentry "Parted Magic" {
    set isofile="/boot/ISOs/pmagic-4.8.iso"

    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry " " {
set root= 
}

menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

menuentry "Ubuntu Mini 9.10 32 bit" {
    set isofile="/boot/ISOs/miniKarmic32.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}


menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}

menuentry "Darik's Boot and Nuke" {
 loopback loop /boot/iso/dban-beta.2006042900_i386.iso
 linux (loop)/ISOLINUX/DBAN.BZI nuke="dwipe" silent --
}



```

---


---
title: "Boot Linux ISO Image From Hard Drive"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by oldefoxx on 2010-02-14
I did some research over the last week on this.  Many say it can't be done.  Others agree, but say how great it would be if it could.  And there are still others that say I've done it, and here is how:

Those last links were the ones I was searching for.  Sometimes it began with someone just wanting or needing to, and the someone else in a lower post pointed the way.  It is not a mystery the way they put it, but there is some extra work involved.  Nothing too hard, but you have to pick your method and work through it.  After that, you might want to write a step-by-step procedure yourself, maybe to help someone else out with your how-to way, maybe as preparation against a future need.  How about if you could just quit burning some CDs every time a new release of Ubuntu comes out?

Enough said.  These is the links I fetched and forwarded to myself in an email.  Using WebMail, I copied it down onto each of my PCs.  Now even if one PC crashes, I can find the instructions elsewhere without searching all the web again.  Trying to use my head, you see.


[http://ubuntuforums.org/showthread.php?t=273114]("http://ubuntuforums.org/showthread.php?t=273114")
[http://ubuntuforums.org/showthread.php?]("http://ubuntuforums.org/showthread.php?")
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")
[http://ubuntuforums.org/showthread.php?t=28948]("http://ubuntuforums.org/showthread.php?t=28948")
[http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/page__s__1901b54c2fd8d8fb30989f058b8e7364]("http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/page__s__1901b54c2fd8d8fb30989f058b8e7364")
[http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/]("http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/")
[http://www.linuxquestions.org/questions/fedora-35/installing-f9-from-iso-on-hard-disk-grub-command-help-654136/]("http://www.linuxquestions.org/questions/fedora-35/installing-f9-from-iso-on-hard-disk-grub-command-help-654136/")

"mount /path/to/image.iso /mnt/mountpoint -t iso9660 -o loop=/dev/loop0" (only thing of interest found in one thread)

[http://www.computing.net/answers/linux/booting-iso-and-img-from-hard-drive/28977.html]("http://www.computing.net/answers/linux/booting-iso-and-img-from-hard-drive/28977.html")
[https://help.ubuntu.com/community/Installation/FromLinux http://ubuntuforums.org/showthread.php?t=273114]("https://help.ubuntu.com/community/Installation/FromLinux http://ubuntuforums.org/showthread.php?t=273114")

"I can boot from the iso using qemu." (one of several references to software that can help with doing this)

Oh, here is a thought about the suggested added partition that some want used for the image.  You already have one, or should, designated Swap.  Just sacrifice Swap for a bit, use it for the image, then restore Swap.  You can use gparted for part of this, and comment out the referemce to swap in /etc/fstab while it is used for the image.  Or you might be able to split the swap partition into two, leave one as swap, and the other for the ISO.  After all, a CD image cannot be more than 700 MB in size, and even if handling a DVD, the most it will go is less than 4.8 if using both surfaces, or under 2.5 if one surface.  

Lots of ways to play with this stuff. Success and crash stories are welcomed, as they may help others towards the same end.

---

### Post by niffcreature on 2010-02-14
i dont want to read all those posts, not too sure about all the details just wanted to let you know there is a program that claims to do it. i tried it with ubuntu studio, which does not work because it wanted to configure network at startup and download all of the packages.

the program is called unetbootin.
it installs the iso on the hard drive as sort of a virtual flash drive. you can then reboot to a live ubuntu or install it.

---

### Post by nooby on 2010-02-14
thanks for all the links. I have not tested what they recommend but I did found example from pendrivelinux and tested them on a 4GB flash memory USB and I also tested on a USB HDD external drive, 

But it is more difficult to do it on the NTFS internal HDD. 

Two ubuntus will mess up loading files from each others. That is my experience but it could be me using the wrong code in menu.lst 

But I like the idea so thanks indeed for making a thread and posting all the links to examples. 

You can have persistence on a fat32 formatted disk but not on a NTFS one due to limitation in the boot scripts to handle NTFS. But that could change soon enough if somebody good at writing codes for boot does a new version that has these features.

Hope this is the original. Have not tested it recently but this did work for me IIRC

default 0

timeout 30

color NORMAL HIGHLIGHT HELPTEXT HEADING

# Splash Image

splashimage=/splash.xpm.gz

foreground=FFFFFF

background=0066FF 



# Linux Mint 8 Menu Item Submitted by Szymon Silski

title Boot Linux Mint 8

find --set-root /LinuxMint-8.iso

map /LinuxMint-8.iso (0xff)

map --hook

root (0xff)

kernel /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper persistent iso-scan/filename=/LinuxMint-8.iso splash

initrd /casper/initrd.lz

boot



title Boot Ubuntu 9.10

find --set-root /ubuntu-9.10-desktop-i386.iso

map /ubuntu-9.10-desktop-i386.iso (0xff)

map --hook

root (0xff)

kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-9.10-desktop-i386.iso splash

initrd /casper/initrd.lz

boot



But due to the persistent they borrowed things from each others files so I must have done something wrong there. But many people have tested similar setups of usb fat32 formatted drives or on DVD.

---

### Post by nooby on 2010-02-14
many of your links breaks into text instead of links so the fail. Hard to guess what should be there. Could you repair them please

I found this link and used that one 

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")

---

### Post by shadowlands on 2010-02-14
Ca you hilight the one that deals with loading the kernel/> **nooby said:**
> many of your links breaks into text instead of links so the fail. Hard to guess what should be there. Could you repair them please

I found this link and used that one 

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")

---

### Post by nooby on 2010-02-14
first, my english are not that good. What exactly is it you ask Tell me what you want to accomplish and maybe I know how to answer it or link to such answers. 

[B]
But generally I know too little. I just did what they told me there until it worked for me. [/B]

I don't know much about what it actually do. 

Kernel is another name for vmlinuz if I remember. 

Late at night here so I go to bed now. Others can explain it better. 

what it does is to treat the iso with code for CD/DVD despite it being on a usb flash or HDD external. You need to add a casper-rw file to get it to save changes. pendrivelinux has several such premade. 512, 10024, 2GB 4GB. I tested to use the small 512MB on the 2GB flash and a 4GB on on my HDD. But there are other ways to do it too that fill the whole external HDD

goodnight

---

### Post by oldefoxx on 2010-02-15
> **nooby said:**
> many of your links breaks into text instead of links so the fail. Hard to guess what should be there. Could you repair them please

I found this link and used that one 

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")

For anyone interested in conducting their own search, I find Google to give some of the best results, and my search query was basically this: boot ISO from hard drive.  Variations in the wording can help produce more results.  So far as I can determine,
one repeated step is to mount whatever hard drive gets the ISO image as though it were a CD drive, meaning it has to be mounted to loop about as a CD disk will.  Some indications of just getting the software on the drive as an extract and going from there.  And even some mention of software that will just let you run the ISO as-is where it lies on the partition.  Need to look into it more myself before I can confirm any of this.

Sorry about the messed-up links.  It seems a repeatable problem based on the way forum software treats post submissions.  You may have noted that excess spaces and tabs get replaced by single spaces, and it can do other things as well.  I looked at the choices offered here for entering code, but did not find that option, but they do have one for including links.  I will do two things:  Enter each link here by that means, then attach a list at the end of this post.  One or the other of those should serve for most people.

[http://ubuntuforums.org/showthread.php?t=273114]("http://ubuntuforums.org/showthread.php?t=273114")
[http://ubuntuforums.org/showthread.php?]("http://ubuntuforums.org/showthread.php?")
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")
[http://ubuntuforums.org/showthread.php?t=28948]("http://ubuntuforums.org/showthread.php?t=28948")
[http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/page__s__1901b54c2fd8d8fb30989f058b8e7364]("http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/page__s__1901b54c2fd8d8fb30989f058b8e7364")
[http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/]("http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/")
[http://www.linuxquestions.org/questions/fedora-35/installing-f9-from-iso-on-hard-disk-grub-command-help-654136/]("http://www.linuxquestions.org/questions/fedora-35/installing-f9-from-iso-on-hard-disk-grub-command-help-654136/")

"mount /path/to/image.iso /mnt/mountpoint -t iso9660 -o loop=/dev/loop0" (only thing of interest found in one thread)

[http://www.computing.net/answers/linux/booting-iso-and-img-from-hard-drive/28977.html]("http://www.computing.net/answers/linux/booting-iso-and-img-from-hard-drive/28977.html")
[https://help.ubuntu.com/community/Installation/FromLinux http://ubuntuforums.org/showthread.php?t=273114]("https://help.ubuntu.com/community/Installation/FromLinux http://ubuntuforums.org/showthread.php?t=273114")

"I can boot from the iso using qemu." (one of several references to software that can help with doing this)

Note that VirtualBox and VMWare are apparently both capable of letting you mount an ISO as though using a CD or DVD drive, but only in the Virtual Environment.  Some point to this as a way out of the quagmire, but all it really tells me is that it is do-able.

If you could move beyond the stage of using a partition per ISO image, then you could transcribe scores of ISO files for storage in one place and just pick one to mount and run the next time around.  That would eliminate the need for having CDs and DVDs on hand, and mean reduced use of your CD and DVD drive, and also increase overall performance by a wide margin.  Now that would be something worth working out how to do.

---

### Post by nooby on 2010-02-15
thanks these worked better. 

To do it on a USB external HDD or USB flash mem stick seems to work on many iso but not all. They could search for things and not find it so one have to add things that give it to them or stop that search and redirect it to a better path. 

I gave two example above that I hope works but maybe not on same usb. but on separate with persistence to save changes.

---

### Post by oldefoxx on 2010-02-15
The search isn't over yet.  Like I said, change the wording in the search query can produce different results:

Boot from ISO with GRUB.
[http://http://ubuntuforums.org/showthread.php?t=774539]("http://http://ubuntuforums.org/showthread.php?t=774539")

use GRUB to boot an ISO of say a Linux live CD
[http://http://forums.whirlpool.net.au/forum-replies-archive.cfm/925285.html]("http://http://forums.whirlpool.net.au/forum-replies-archive.cfm/925285.html")

With grub2 you can directly boot an (iso9660) ISO using its loopback option.
[http://http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/]("http://http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/")

you can grab the grub.iso CD image
[http://http://www.google.com/cse?cx=partner-pub-9300639326172081%3Aljvx4jdegwh&ie=UTF-8&q=boot+grub+iso&sa=Search]("http://http://www.google.com/cse?cx=partner-pub-9300639326172081%3Aljvx4jdegwh&ie=UTF-8&q=boot+grub+iso&sa=Search")

Boot with GRUB
[http://www.linuxjournal.com/article/4622]("http://www.linuxjournal.com/article/4622")

Help! Was using LILO to boot and MBR tanked!  What now?
"[I]There are several ways to do this from a rescue environment. But I
recomend using a bootable grub CD to get to your native install and
fixing it from there.

Here's a grub.iso

[http://www.laclinux.com/~sam/grub.iso](http://www.laclinux.com/~sam/grub.iso)

Boot from that and you'll get a grub prompt.

grub>

Set the grub root (your /boot partition

grub> root (hd0,0)

Then load your kernel; use tab completion to get the name right. and put
your kernel arguments behind it. This should be the same as the 'image='
line in lilo.conf 

So if lilo.conf has:
vga=normal
image=/boot/vmlinuz-2.6.9
initrd=/boot/initrd-2.6.9
        root=/dev/hda3


grub> kernel vmlinuz-2.6.9 ro root=/dev/hda3 vga=normal

Then the initrd. (If there's not one that's cool just skip this step)

grub> initrd initrd-2.6.9

now boot it.

grub> boot
[/I]"

Howto boot [...] without a cdrom via grub [or lilo]
[http://dirk.eddelbuettel.com/quantian/howto_lilogrub.html]("http://dirk.eddelbuettel.com/quantian/howto_lilogrub.html")

Yolinux.com Tutorial   	
Linux Recovery and Boot Disk Creation
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html")

How to boot several CD iso files in a DVD
[http://www.justlinux.com/forum/showthread.php?t=150078]("http://www.justlinux.com/forum/showthread.php?t=150078")

WindowsDualBoot
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

What is Wubi?
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

BootFromUSB
[https:/**/help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")

"[I]
-create a mountpoint to mount the ISO with loopback:
mkdir /mnt/LiveISO

-mount the image:
mount -t iso9660 -o loop,ro /DOWNLOADS/Knoppix-3.7-en.iso /mnt/LiveISO

-create a directory on the device where you are going to boot from:
mkdir /mnt/hda4/KNOPPIX

-copy the contents of the mounted image to that directory:
cp /mnt/LiveISO/KNOPPIX/* /mnt/hda4/KNOPPIX/

-copy kernel and initrd files to yor boot device:
cp /mnt/LiveISO/boot/* /boot

* Grub:
title KNOPPIX
root (hd0,0)
kernel /linux26 ramdisk_size=100000 fromhd=/dev/hda4
initrd /minirt26.gz
savedefault
boot

* Lilo:
image=/boot/linux26
initrd=/boot/minirt26.gz
label=KNOPPIX
append="ramdisk_size=100000 fromhd=/dev/hda4"
-------------------

The basic idea is that you copy the contents of the iso to a partition. Then, in your current linux os, you copy the kernel and initrd images from the iso to your current boot directory. Last, you edit LILO so that it points to the kernel and initrd images you just copied, and make sure you append the "fromhd" line so that the "livecd" will know where the rest of the knoppix files are. I know that similar instructions worked with kanotix as well (which makes sense since it is knoppix based). The only possible problem for other isos (say non-livecds, for example) is that they may not have a "fromhd" option the way knoppix distros do.[/I]"

System Rescue Super Grub Disk Download – PC Boot Specialized Disk
[http://www.techmynd.com/system-rescue-super-grub-disk-download-pc-boot-specialized-disk/]("http://www.techmynd.com/system-rescue-super-grub-disk-download-pc-boot-specialized-disk/")

Okay, it's me again.  Now some may wonder why bring Grub or Lilo into a discussion about running or booting ISO images off of other devices than a CD?  Because these are your boot methods with Linux, and Grub has even been extended to Windows.  And it is even worth mentioning that you do have options when it comes to trying to recover or repair an install gone bad, so that was brought into the picture as well.

Now somebody has already commented that they didn't have time to read all this stuff, they just wanted a quick and easy.  Well, this is an effort to collect a lot of quick and easys in one place, and let you take your pick.  For the picking to be any good, you may have to do a bit of reading.  It's like prowling the magazine stacks in a library, at least you can tell from the cover and the index whether it might interest you or not.

---

### Post by nooby on 2010-02-15
Thanks indeed for providing all these examples in one place. 

 read all of them in due time. 

what people ask for is also to make changes persistent. Pendrivelinux has several texts about those things. 

It works at most time on USB either flash or HDD formatted in Fat32 but on an internal HDD formatted to NTFS most commenters say it is impossible due to the boot software has not provided the means to do it for all linuxes. Puppy can do it due to them using UnionFs internal program. Some of the Slackware distros have that ability too. Vector linux and Nimblex and others. 

How could one do something like that for Ubuntu? 

Could one use Sbackup or Resmastersys or something to save changes despite being "live session users" or is the ubuntu internal not allowing such saves?

---

### Post by bodhi.zazen on 2010-02-15
> **oldefoxx said:**
> The search isn't over yet. 

The link you listed :

[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

is the best.

From that link :

> With [grub2]("http://www.gnu.org/software/grub/") you can *directly*  boot an (iso9660) ISO using its **loopback** option.

BUT : > **PLEASE NOTE:** grub itself can NOT boot CDROM  images/ISOs. Neither version 1 nor version 2 of grub. [Grml]("http://grml.org/") provides this feature via its isofrom  bootoption. Grub2 strongly simplifies this setup with its loopback  option but grub alone will NOT be enough. It’s the live system (as for  example [grml]("http://grml.org/")) that has to support this  “boot from ISO” feature.

So, there are modifications that need to be made to the iso. 

Since those modifications are not mentioned on the BOLG you can either try the grml .iso and see if you can modify the Ubuntu iso or ask on the grml forums or google search for detailed information on how to do this.

Your other solutions are to use a flash drive and either use unetbootin (the flash drive acts as a live CD) or USB creator (the flash drive allows changes).

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

unetbootin is in the Ubuntu repositories.

[code[sudo apg-get install unetbootin[/code]

Or

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

(See the section on Live  USB creator).

So not the exact solution you are asking for, but flash drives are inexpensive and will allow you to boot without burning a CD.

---

### Post by oldefoxx on 2010-02-15
I sense we might be making progress.  Here is another:

"I have copied the iso image of LFS 6.3-x86-r2160 to the lfs
partition. I have also copied the isolinux folder from the
LiveCD to the lfs partition.

I have referred to the LiveCD Documentation "Booting from ISO image" which says to copy those files to hard disk. It then says...

Configure the boot loader to load “linux” as a kernel image and “initramfs_data.cpio.gz” as an initrd. The following parameters
have to be passed to the kernel:

rw root=iso:/dev/XXX:/path/to/lfslivecd.iso rootfstype=fs_type

I do not understand the instructions. I have reached Chapter 5.6 Glibc-2.5.1 of the manual v6.3. I am new to linux but have used
CentOS intermittently before.

I have 2 questions.

1) Is what I have done correct ? If not what is the correct method ?

2) How do I install and configure the bootloader to boot from ISO image ?

Short answer is that you need a boot loader that will allow you to load the kernel and provide that root parameter. GRUB is your friend in this regard. If you used GRUB you would enter this into the grub command line

root (hd0,1)
kernel /path/to/isolinux/linux root=iso:/dev/hda2:/path/to/lfslivecd.iso
initrd /path/to/initrd.img
boot
"

---

### Post by nooby on 2010-02-15
Here is one good link I hope 

[https://docs.google.com/Doc?docid=0ATls0YIAGFKmZGduenpqOHhfM2M4ZndueGZ0&hl=en]("https://docs.google.com/Doc?docid=0ATls0YIAGFKmZGduenpqOHhfM2M4ZndueGZ0&hl=en")

Maybe info at this link may help too. 
[http://www.911cd.net/forums//index.php?showtopic=18045]("http://www.911cd.net/forums//index.php?showtopic=18045")

and this one mention things maybe of help

[http://www.knoppix.net/forum/viewtopic.php?t=11796&postdays=0&postorder=asc&start=600]("http://www.knoppix.net/forum/viewtopic.php?t=11796&postdays=0&postorder=asc&start=600")

this text may be helpful to some

[http://www.boot-land.net/forums/index.php?showtopic=5041]("http://www.boot-land.net/forums/index.php?showtopic=5041")

I know almost nothing about that set up you mention but as I remember the partition has to be Fat32 or some other linux formatting. 

I have read several seasoned linux users that say that grub does not allow one do it on NTFS formatted partitions. And that is ok for many people and I did test similar set ups on USB flash and on USB HDD and it worked ubuntu could get persistence through a casper-rw file 

hac5 which forums had a server thing going but may be up sooner or hater and bootland has many people trying to do what we also want. 
[http://www.boot-land.net/forums/index.php?showtopic=8944]("http://www.boot-land.net/forums/index.php?showtopic=8944")

and other places have descriptions on how to too.

---

### Post by oldefoxx on 2010-02-15
Turning up some more leads:

[http://www.plex86.org/linux/Hi-from-kubuntu.html]("http://www.plex86.org/linux/Hi-from-kubuntu.html")

[http://www.plex86.org/linux/Hi-from-kubuntu.html]("http://www.plex86.org/linux/Hi-from-kubuntu.html")

UNetbootin - Homepage and Downloads
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

Install Linux on a USB drive with UNetbootin
[http://www.ghacks.net/2008/12/16/install-linux-on-a-usb-drive-with-unetbootin/]("http://www.ghacks.net/2008/12/16/install-linux-on-a-usb-drive-with-unetbootin/")

UNetbootin Creates USB-Bootable Linux the Easy Way
[http://lifehacker.com/5042630/unetbootin-creates-usb+bootable-linux-the-easy-way]("http://lifehacker.com/5042630/unetbootin-creates-usb+bootable-linux-the-easy-way")

Install any Linux distro directly from hard disk without burning any DVD
[http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html")

What is ISOLINUX?
[http://syslinux.zytor.com/wiki/index.php/ISOLINUX]("http://syslinux.zytor.com/wiki/index.php/ISOLINUX")

Boot Live CD From Hard Drive
[http://forums.techguy.org/linux-unix/811964-boot-live-cd-hard-drive.html]("http://forums.techguy.org/linux-unix/811964-boot-live-cd-hard-drive.html")

Grub2 boot Live CD from hard disk
[http://lxer.com/module/forums/t/29912/]("http://lxer.com/module/forums/t/29912/")

"[I] Booting F12 LiveCD from hard disk [SOLVED]
I want to run F12 Live from hard disk as a live OS, not an "installed to hard drive" OS. Googling has turned up others asking for similar, but not finding a complete solution for F12, I struck out on my own.

What I did:

1) Started with a working Red Hat 5.2 installation with its /boot on sda1 and root fs on sda2
2) created an ext2 partition on /dev/sda3
3) Boot from F12 Live CD
4) mount the F12 LiveCD iso (on a USB stick) to /mnt/LiveISO
5) run /mnt/LiveISO/LiveOS/livecd-iso-to-disk with proper arguments to load it to /dev/sda3
6) reboot under RH 5.2 and edit grub.conf to add this boot option:

Code:

title Fed Live
   root (hd0,2)
   kernel /EFI/boot/vmlinuz0 fromhdd=/dev/sda3 root=live:LABEL=Fedora-12-i686-Live rootfstype=auto ro liveimg
   initrd //EFI/boot/initrd0.img

7) reboot, selection the new "Fed Live" menu option

What I get:

Loads vmlinuz0 and initrd0.img, then after "drcut: Starting plymouth daemon" it says "No root device found. Boot has failed, sleeping forever."

It looks like I may be very close but just missing telling it where to find the root filesystem.

Any idears?
Last edited by RAThomas; 2010-01-15 at 10:22 AM CST.
Reply With Quote
RAThomas
View Public Profile
Find all posts by RAThomas
  #2  
Old 2010-01-15, 10:36 AM CST
RAThomas Offline
Registered User
	  	
Join Date: Jan 2010
Posts: 4
windows_vistafirefox
My particular solution is mostly based on another thread found here that was related to installing to a USB drive. I'll add the link once I find it again.

Install the target hard disk in a Linux based setup computer and power it up.

Verify that the target hard disk is /dev/sdb (or substitute whatever it *is* in the steps here).

Erase the partition table on the target disk:
Code:

dd if=/dev/zero of=/dev/sdb bs=512 count=1

Label the disk:
Code:

parted /dev/sdb mklabel msdos

Create a FAT32 (vfat) partition that is at least large enough to hold the DVD image (on a 250 GB drive, 20% is way more than enough):
Code:

parted /dev/sdb mkpartfs p fat32 0% 20%

Label the partition:
Code:

mlabel -i /dev/sdb1 ::LIVECD

Mount the new hard disk partition so the live image files can be written to it:
Code:

mkdir /mnt/livehdd
mount /dev/sdb1 /mnt/livehdd

Mount the ISO image of the LiveCD so its files can be accessed:

Code:

mkdir /mnt/liveiso
mount -o loop <path_to>/<name_of_image_file>.iso /mnt/liveiso

Copy the LiveCD files from the ISO file to the target hard disk:

Code:

cp -r /mnt/liveiso/* /mnt/livehdd

Sanity check, verify the file/directory structure on the target hard disk:
Code:

ll /mnt/livehdd
[todo: example of proper directory structure]

Install the grub bootloader on the target disk
Code:

grub-install --root-directory=/mnt/livehdd  /dev/sdb

Use your favorite editor to create a new file “/mnt/livehdd/boot/grub/grub.conf” with the following entry:
Code:

title Fedora 12 Live [your specific version info here]
root (hd0,0)
kernel /isolinux/vmlinuz0 ro root=LABEL=LIVECD rootfstype=auto liveimg selinux=0
initrd /isolinux/initrd0.img[/I]"

Note to all:  "F12" is shorthand for Fedora 12, so just think Ubuntu instead where you see either of those terms.

"[I]I like the boot way of knoppix's iso file,and i have a ubuntu live cd iso too.
how can ubuntu live cd iso boot like knoppix from hard disk?

Look in the ubuntu's forum (if they got one. Never been there) and look for 'Poor Man Installation'. that's how is called what you want to do with the ubuntu.iso or google it

Knoppix's Poor Man Installation
[http://www.knoppix.net/wiki/Poor_Mans_Install]("http://www.knoppix.net/wiki/Poor_Mans_Install")[/I]"

Oh man, seems everyone is doing it.  How can we remain far behind?

---

### Post by niffcreature on 2010-02-15
what youre doing here is so broad and abstract.
it is a much more useful thing on a forum to compile your understanding of all these things and type it out instead of the links.
actually that doesnt even have to do with forums.
you cant get through everything with copy and paste. typing new things increases your comprehension SO much. posting all of these links is just jumbled and confusing. i might be able to help but i dont know where your problem is anymore.
sorry, not trying to flame you or anything just actually sum things up.

---

### Post by oldefoxx on 2010-02-16
> **niffcreature said:**
> what youre doing here is so broad and abstract.
it is a much more useful thing on a forum to compile your understanding of all these things and type it out instead of the links.
actually that doesnt even have to do with forums.
you cant get through everything with copy and paste. typing new things increases your comprehension SO much. posting all of these links is just jumbled and confusing. i might be able to help but i dont know where your problem is anymore.
sorry, not trying to flame you or anything just actually sum things up.

No offense taken.  The idea is to explore the concept and see what has been made to work by others.  It is a lot to take in, but note that some have already begun to post their own experiences and which technique worked for them.  Further, it's like a rating system, where you come up with the few that seem to be best suited.  I see one I don't quite understand, I might then see another that explains it better.  I note a tendency right now to either dedicate a partition to an ISO image, or rely on a USB pendrive.

I think the ultimate goal is just to be able to designate and boot any ISO image stored on a hard drive rather than conduct a normal boot, with none of the hassles involving manual editing and command line efforts.  I don't see that here yet.  Be nice if it could be made to happen.  

Maybe just helping others see what has been achieved by someone else might somehow get us closer to that goal.  So I guess you could say that is what I am looking for, but maybe what I turn up will be enough for others.  If you think it is still too much, then you are not required to keep pace with this thread, that being a matter of personal choice.  At least I should be putting to rest the notion that it can't be done at all, which is a common opinion on many threads out there.

And not to depart with nothing to add, here are a few more links to consider:

What is grml?
[http://grml.org/]("http://grml.org/")

"[I]ISO files are just images of the content they cloned, most likely created from a DVD/CD.

I use to boot Live CDs off the Hard Drive. It was simply downloading the ISO, giving it a location:

CODE
cat name_of_iso.iso > /dev/hda10


Then alter the bootloader to point to the root /dev/hda10.

Booting ISOs under NTFS partitions is another story though and since I work mostly under Linux, I never did get round to doing an NTFS ISO boot.[/I]"

Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")

"*maybe a bit off the topic ... but i see u r using xp/w2k ... ever tried MS wirtual pc 2004 which is now free available. you can mount ISO images as boot disc from any location.*"

Installing Fedora from the hard drive (without a boot CD)
[http://bobpeers.com/linux/hard_drive_install]("http://bobpeers.com/linux/hard_drive_install")

XP: Small, Free Way to Use and Mount Images (ISO files) Without Burning Them
[http://www.tech-recipes.com/rx/620/xp_small_free_way_to_use_and_mount_images_iso_files_without_burning_them/]("http://www.tech-recipes.com/rx/620/xp_small_free_way_to_use_and_mount_images_iso_files_without_burning_them/")

---

### Post by nooby on 2010-02-16
Yes and to save changes is not so easy. Slackware linux variants seems to be able to using unionfs save files but Debian seems to do things in a different ways them not using unionfs files at all??? 

To compare Debian/Ubuntu with Slackware. 

Slax is a slackware variant. Here pendrivelinux talk about it and what is needed to be saved and restored. 

[http://www.pendrivelinux.com/slax-savingrestoring-settings/]("http://www.pendrivelinux.com/slax-savingrestoring-settings/")

As a newbie I wonder what is needed to be saved on Ubuntu? 

Say I do an update to Firefox and also add some addons like xmarks and I add youtube addon to save such a file in flv or mp3. there are several such addons to use. 

when I shut down the computer these addons and the upgrade to FF are gone. 

On Slax they tell what to save and restore. 

How do I find an easy tutorial to do that in Ubuntu. CLI maybe is easiest if one only need one command and one path to the HDD. 

I find this thread incredibly helpful. I looked for such a thread for some three years. so if others don't have a need for it then they can create their preferred threads.

---

### Post by bodhi.zazen on 2010-02-16
> **nooby said:**
> As a newbie I wonder what is needed to be saved on Ubuntu? 

In Ubuntu, boot the live CD and use the USB Creator.

No offense, but the biggest problem with this thread is that it is the blind leading the blind.

I suggest you start with the links I gave already.

[http://ubuntuforums.org/showpost.php?p=8831219&postcount=11](http://ubuntuforums.org/showpost.php?p=8831219&postcount=11)

Did you read those links ? Those links are Ubuntu specific.

If you want to go beyond that you need to look under the hood. Ubuntu is not Slackware is not SLAX. So pick a distro, stay with it until you understand it.

Now if you wish to dissect Ubuntu , start with this page :

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

If you want to make the ubuntu iso work like grml, dissect the grml live CD and see what customizations they made, then try to implement them in Ubuntu.

Slax , Wolvix, these boot off an iso on your hard drive. Dissect these to understand how they do it.

Unetbootin or USB creator will allow you to make a bootable usb drive from an iso, unetbootin is like the live CD, your changes are not saved, usb creator is persistent, your changes are saved. If you are not using those applications to make a bootable usb you are likely spinning your wheels.

If you want to understand how to make a live CD, and customize it to make it bootable via grub , on a hard drive, that is going to  be much more difficult and will require you to dissect the live CD and likely modify the boot (upstart) scripts. Since Ubuntu is not SLAX, using slax as and example of how Ubuntu "should work" is not going to get you far. The two projects have very different goals and very different config files.

---

### Post by nooby on 2010-02-16
Thanks, I do trust that this is very helpful if one understand the text you wrote on the level of knowledge you have. 

From my perspective it was way too abstract. That doesn't mean me did not appreciate your efforts but sadly me lacks the means to know how to make use of it. 

But I keep this in mind and will go back to it due to a bookmark marked as high priority to learn from. 

So thank you very much indeed. 

regards 

Nooby

---

### Post by bodhi.zazen on 2010-02-16
> **nooby said:**
> Thanks, I do trust that this is very helpful if one understand the text you wrote on the level of knowledge you have. 

From my perspective it was way too abstract. That doesn't mean me did not appreciate your efforts but sadly me lacks the means to know how to make use of it. 

But I keep this in mind and will go back to it due to a bookmark marked as high priority to learn from. 

So thank you very much indeed. 

regards 

Nooby

Building live CD is not an easy task, and if you wish to learn, I highly suggest a much more systematic approach then reading the random links in this thread.

Using unetbootin or the Live CD creator are both very very easy and are both GUI based tools.

Here are links to graphical how to's

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

---

### Post by nooby on 2010-02-16
Thanks, I thought of using Remastersys but got "chicken" when one guy wrote that that program destroyed everything he had so now he only use windows and is fed up with using linux. Sad story. 
[B]
make-bootable-iso of current system set up would be a nice feature to have in standad coming ubuntu. [/B]

But how much do I need to learn to do these things manually? 

I need to know where the changes did go. Then if it is possible as a "live session user" to save and restore these saved snapshots. 

[B]what I worry about is the permissions. A "live session user" are not supposed to be a regular user. One should only test things and then install. Only then does one get permissions to do things. IIRC 

So I would need to either changes the log in at boot up by remaster the live iso so it behave more normally and not the restricted "live session user" automatic log in. [/B]

---

### Post by bodhi.zazen on 2010-02-16
Remastersys if a nice tool, but as you say, you really need to read the documentation very very carefully.

The problem with remastersys is that it makes changes to the system, then makes a back up or iso rather then making a backup and changing the backup. This results in damage to the system if you do not understand what you are doing and, IMO, should be fixed.

The link for customizing an Ubuntu ISO are

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by nooby on 2010-02-16
jay, that maybe is a better way. I try to use these. 

But it will take time due to me a very slow learner but these links seems to be the most promising way forward. 

May I just ask one thing more. Do you know now if the "live session user" are as restricted as I wild guess it to be? 

Okay I should test it first but I do remember vaguely that I read somewhere that the "live session user" is not supposed to be given normal permissions. 

I guess it will be obvious what permissions that is missing when I try to follow the instructions in the two links. I get to it now this week. Will be a cool adventure to try to make my own version of ubuntu. 

heheh problem already here. 

mkdir ~/live

The tilde seems to be lacking in the Swedish setxkbmap se and I have no idea where itis in the usa kbmap. Usually things go wrong due to such easy things not known to a complete newbie. here in windows the tilde is not easy to make either ~ one need to combine three keys to get it.

cool thing they mention:

> You will need a kernel and an initrd that was built with the Casper scripts. Grab them from your chroot. Use the current version. Note that as of 9.10, the initrd is in lz not gz format... This may cause problems with GRUB2

That was what did happen to me but I had imagination enough to try out lz instead and that get the frugal install working. 

find --set-root /casper/vmlinuz
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper splash --
initrd /casper/initrd.lz 
boot

I still don't know what the preseed is about. Too knew term for me. 
they don't explain what preseed is anyware in that tutorial. 

Here is a comment on how difficult it is to use it for someone not English. 

> How can I set the keyboard language for the console and X? Currently I can make the livecd without problem but the kbd language is always en. Tnx in advance.

Matteo

LiveCDCustomizationFromScratch (last edited 2010-02-03 19:26:12

that is what we need to know. I need to make it a Swedish kbmap.

---

### Post by oldfred on 2010-02-16
I did not see herman's page where he mounts an ISO
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Loopback_Boot_Entry](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Loopback_Boot_Entry)

[FONT=Bitstream Vera Sans Mono]#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry "Ubuntu Lucid Lynx ISO" {
loopback loop (hd0,1)/home/herman/Downloads/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/home/herman/Downloads/lucid-desktop-i386.iso noprompt noeject quiet splash
initrd (loop)/casper/initrd.lz
}
EOF[/FONT]

---

### Post by nooby on 2010-02-16
thanks that was a good contribution. But all these are using fat32 formatted USB flash or usb hdd and not using the internal NTFS formatted HDD? 

That is still a very valuable thing but some older computers like Compaq Pressrio doesn't boot using usb despite one tell the Bios that it should. Sad thing. But it does boot a DVD so that allowed me to doing a full install on the small internal HDD. 

If we can do away with both usb and CD / DVD then people can test linux by just downloading the iso and just boot it on the same NTFS that they already use for windows. No need to resize or to partition.

Yes I have tested the live CD thing and that is not comparable to using the iso directly, big difference in performance. I have tested Qemu and VirtualBox too and it is not comparable with doing frugal install and using the iso directly. so that would be a very neat thing. It works on Fat32 but not on NTFS jet. But hopefully somebody change the boot programs until one of them can be used that way.

---

### Post by bodhi.zazen on 2010-02-16
> **nooby said:**
> If we can do away with both usb and CD / DVD then people can test linux by just downloading the iso and just boot it on the same NTFS that they already use for windows. No need to resize or to partition.

Not exactly. This method of booting an iso is using GURB, which is not a part of windows.

To do this from windows as you describe would require configuration of the windows boot loader.

There already exist several very simple solutions:

First I would also point you to wubi :

[http://wubi-installer.org/](http://wubi-installer.org/)

> 
             **Wubi is Simple**

             No need to burn a CD. Just run the installer, enter a  password for the new account, and click "Install", go grab a coffee, and  when you are back, Ubuntu will be ready for you.wubi does not require partitioning your hard drive or installing grub. If one does not like Ubuntu, one simply removes wubi. Very very easy and straight forward.

Second I would point out Virtualilzation. Virtualbox, KVM, VMWare will all boot an ISO and is almost certainly adequate for testing purposes. Almost anything resembling a modern computer will easily run VirtualBox.

---

### Post by nooby on 2010-02-16
Yes I had Ubuntu in wubi just a few hours ago. But have uninstalled it. Yes I have Vbox and have tested solaris and many others in it. 

Yes it works but is not really the same as iso booting. 

You are right that it doesn't work on NTFS. But it does work on a Fat32 formatted HDD used externally via usb.

---

### Post by oldefoxx on 2010-02-19
Been real busy setting up a new PC for family member that will use combo of Ubuntu+VirtualBox+Win2k in place of Vista.  Major problem was old PC had beem reconfigured with hard drive split into three partitions, C, D, and E, and the operating system and programs are installed on D.  This is bad, because VirtualBox provides a Local C Drive and a D drive designation for theCD-ROM drive, and these designations are fixed.  To restore the old D Drive backup to the new local C Drive means nothing that is installed will work, since settings in the Registry and links include drive designations by letter, and it is all going to be a letter off.

I think the reason for dividing old drives that way is that the put the innermost and outermost cylinders away from the OS, and I guess it was a way to get past problems as those drives aged, since the center cylinders were a good compromise point on drive aspects.

But I remain interested in this topic, and am in no rush to mark it solved, simply because there is a good dialog going on that brings more light to the subject.  If nothing else, some of the things being said right now are insights to what has to happen for this really to work.

I am not so keen on the VM approach to this, because I've worked with VirtualBox for quite awhile, and even had a situation where I tried to use a Ubuntu+VirtualBox+LiveCD.iso all together, and while it got up and running, keystrokes and mouse movements within the LiveCD were cut by a fierce amount, maybe every fourth or fifth key pressed getting through.
And like I said before, the VM is really confining activity to the virtual environment created, though that can be extended using a mix of USB and Shared Folders.  But that is a lot of prep work, involving the /etc/fstab fole, added subfolders to /media or /mnt, and you likely will have to use CHMOD so that some of these can be written to.

One thread elsewhere had someone going off on the topic that there is no way that one OS can be made to boot up another OS in its stead.  Well, that is not something that one OS would normally be designed to do, I agree, but software is software, and you can structure software to do just about anything if you want to.  In fact, if you think about it, the boot process looks to another device to boot in its place, and the second process is something like grub, then it will likewise search further and boot another process in its place, and when it points to Windows, it is likely going to boot.ini which is yet another boot process.  So wham-bam-bam! you are going through a sequence of processes whose only goal is to bring up something to load in place of what came before it.  You can argue that these aren't true operating systems, but that only means they were not designed for those added responsibilities.  Had they been, then they could do those as well.

We are just discussing ways to go back the other way, to take and existing OS and use certain features together to bring up nother OS.  With a VM Manager, you are actually going to have the host, the manager, and the client all striving to function at the same time, and there can be some induced problems when you do that.  So maybe the better idea is to do what you can and need to with the first OS, then have some way for it to bring up the next OS up and getting it started, then shut itself down.  Since the startup of the next OS is no more strange than starting up some other programs, it is really a question of initiating that second OS via an ISO or other footprint and then closing down the running OS, and every OS provides suitable means for being shut down.

What might be of some value is a handstamp by the first OS as to where it was and what it was doing that can be resumed if it is restarted in the proper manner.  Perhaps more to the point, might there not be a way for a multi-core cpu to divide the roles between the host and the guest, so that if you did kick off an ISO, it could run in parallel with the host?  Well, actually the host+VM+guest works somewhat like that, but somehow the focus of where the user is and what the user is doing needs to be strengthened so that all pressed keys get registered where intended.

---

### Post by nooby on 2010-03-03
Ulteo linux maybe is a special case. The first OS doesn't really shut down like a boot loader would? 

[http://www.ulteo.com/home/en/home?autolang=en]("http://www.ulteo.com/home/en/home?autolang=en")

I wish more people would be interested in booting iso or doing frugal installs.

---

### Post by dan98 on 2010-07-23
What is the bottom line? Just using grub2 not unetbootin, grml, mounting the iso, or grub4dos. I don't think 'Using grub 2 to boot an iso off hard drive' works. It sounds nice. 
 
Does anyone out there have this working? Can you build a virtualbox VM and make it available for download?
 
Update it works!
[http://newyork.ubuntuforums.org/showthread.php?t=1535864](http://newyork.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by oldefoxx on 2010-07-28
> **nooby said:**
> jay, that maybe is a better way. I try to use these. 

But it will take time due to me a very slow learner but these links seems to be the most promising way forward. 

May I just ask one thing more. Do you know now if the "live session user" are as restricted as I wild guess it to be? 

Okay I should test it first but I do remember vaguely that I read somewhere that the "live session user" is not supposed to be given normal permissions. 

I guess it will be obvious what permissions that is missing when I try to follow the instructions in the two links. I get to it now this week. Will be a cool adventure to try to make my own version of ubuntu. 

heheh problem already here. 

mkdir ~/live

The tilde seems to be lacking in the Swedish setxkbmap se and I have no idea where itis in the usa kbmap. Usually things go wrong due to such easy things not known to a complete newbie. here in windows the tilde is not easy to make either ~ one need to combine three keys to get it.

cool thing they mention:



That was what did happen to me but I had imagination enough to try out lz instead and that get the frugal install working. 

find --set-root /casper/vmlinuz
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper splash --
initrd /casper/initrd.lz 
boot

I still don't know what the preseed is about. Too knew term for me. 
they don't explain what preseed is anyware in that tutorial. 

Here is a comment on how difficult it is to use it for someone not English. 



that is what we need to know. I need to make it a Swedish kbmap.

I've been off this topic for awhile. There are several new things worthy of adding to the topic range.

First off, any LiveCD is the basis for dealing with any system regardless of what is installed on it.  I found Fedora 13 wanted to constrain use of su and sudo by adding a special table at /etc/sudoers to control this, and that you had to use visudoers to get into and update, which you could not do without root powers.  All I had to do is boot up Ubuntu on the LiveCD, get into terminal mode, use sudo -s there, then work to mount the partitions on the system and finally edit its /etc/sudoers with my gedit.  Now I was on the approved list for using sudo on that system.

Becoming root is not a big deal, because as su, you have the power to set a new password for anyone including root.  Of course if you don't know what you are doing, you will lose track of the existing root password, meaning someone will see later that it was tampered with.  But if I come in as su from a LiveCD, I'm not committed to using any of the standing system's resources for logging or tracking activities, and the changes will just appear almost magically, unless the standing system is already active or actively monitored on it own, and remains that way as I penetrate it.  Any stoppage of ongoing monitoring or logging can also be a dead giveaway of an external presence.
er 
I am not here to really discuss ways to get around system safeguards, just to show that putting up some safeguards is not a guarantee of system security.  I am showing that there is a great deal of power present in a LiveCD because you have essentially the power of a full system at your disposal from a LiveCD, any LivedCD, regardless of source.

To drop support for or not put out a LiveCD of your own is rediculous, because they already exist in many forms.  It is true that you will find the words to the effect that any changes made while working from a LiveCD will not effect the system underneath, but if you tunnel down by becoming root or su, your changes are then part of the system below if you want them to be.  Sometimes when you don't want them to be as well.

There is a critical area here, between what the user wants to be able to do with his own system, which is certainly his to do as he will with, and what a corporatin, business, or government agency wants to allow to happen with their system with or without their knowledge and approval.  What makes this area critical is that what works on one side also works on the other.

To truly protect and secure a system, all knowledge of it existence, purpose, use, and details about the equipment, language and code involved must be hidden away securely.  When governments adopt commercial offerings, which fall into the hands of corporations and users alike, there is great risk of someone crossing into or over that critical area.  The same risks are shared in the commercial arena when others have access to the same manner and nature of hardware and software.

To not do something now because it might fall into the wrong hands is far too late in the game.  You might as well go ahead and learn how yourself, because you will not be the first or the last.

---

### Post by bodhi.zazen on 2010-07-28
> **oldefoxx said:**
> I've been off this topic for awhile. There are several new things worthy of adding to the topic range.

First off, any LiveCD is the basis for dealing with any system regardless of what is installed on it.  I found Fedora 13 wanted to constrain use of su and sudo by adding a special table at /etc/sudoers to control this, and that you had to use visudoers to get into and update, which you could not do without root powers.  All I had to do is boot up Ubuntu on the LiveCD, get into terminal mode, use sudo -s there, then work to mount the partitions on the system and finally edit its /etc/sudoers with my gedit.  Now I was on the approved list for using sudo on that system.

Becoming root is not a big deal, because as su, you have the power to set a new password for anyone including root.  Of course if you don't know what you are doing, you will lose track of the existing root password, meaning someone will see later that it was tampered with.  But if I come in as su from a LiveCD, I'm not committed to using any of the standing system's resources for logging or tracking activities, and the changes will just appear almost magically, unless the standing system is already active or actively monitored on it own, and remains that way as I penetrate it.  Any stoppage of ongoing monitoring or logging can also be a dead giveaway of an external presence.
er 
I am not here to really discuss ways to get around system safeguards, just to show that putting up some safeguards is not a guarantee of system security.  I am showing that there is a great deal of power present in a LiveCD because you have essentially the power of a full system at your disposal from a LiveCD, any LivedCD, regardless of source.

That is a long winded way of stating the old adage, physical access == root access.

IMO the only defense (other then limiting physical access) is encryption.

---

### Post by nooby on 2011-10-18
Took me a year to get success. And not my genius either. 
More due to an accident than any real know how. 
The original code is from here 
[http://agnipulse.com/2011/08/install-ubuntu-hard-disk/]("http://agnipulse.com/2011/08/install-ubuntu-hard-disk/")
But I simplified it to work for grub4dos iso frugal install of Live session Ubuntu.
I can now boot all??? various Ubuntu iso and them all work for me even editing 
on a NTFS internal HDD on an Acer D250 10" Netbook with an Atom N270 CPU. 

I used this grub4dos code. The one that give best OOTB exerience is 
Netrunner OS [http://www.netrunner-os.com/](http://www.netrunner-os.com/)

      
 title Netrunner 2011 frugal iso boot of netrunner-3.2.iso 
 find --set-root --ignore-floppies --ignore-cd /netrunner-3.2.iso
 kernel	/netrunner/casper/vmlinuz rw  file=/cdrom/preseed/netrunner.seed boot=casper iso-scan/filename=/netrunner-3.2.iso noeject noprompt quiet splash --
 initrd	/netrunner/casper/initrd.lz

  but the one I used first was this one 

title Bodhi Linux boots from Bodhi_1.2.1.iso
find --set-root --ignore-floppies --ignore-cd /bodhi_1.2.1.iso
kernel /casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper persistent iso-scan/filename=/bodhi_1.2.1.iso quiet splash --
initrd /casper/initrd.gz

Do you notice that the preseed can have different names there. custom.seed 
or ubuntu or netrunner or whatever. so you have to look it up. 
I edited out almost all of the fancy code but fortunately 
by accident kept the part that was needed. Thanks to D4P fellow

title Bodhi_1.2.1.iso
find --set-root --ignore-floppies --ignore-cd /bodhi_1.2.1.iso

[B]you place the iso on /mnt/home and you extract out the casper 
and preseed and the isolinux and the ubuntu file and place them 
also on the root or C:/ whatever it is named. [/B]

And the very good thing is that Bodhi is an exception from the norm. 
Usually only Slax varieties allow you to change a text file and save it again. 

Neither AntiX that is a Mephis variety nor Archiso that is an Arch variety 
allow you to save on same partition you boot a live version on. 

Bodhi and almmost or all of the Ubuntu varieties allow that on save changes on the hdd
but I have failed to get it to use casper-rw files to get permanence. 

A good thing is that for the first time I am able to change text files 
like menu.lst from within ubuntu. That was lost when I had the 2009 version 
IIRC or was it the 2010? Anyway now it works again. 

So thanks for allowing is iso boot option using grub4dos.

---

### Post by nooby on 2011-12-08
Being as curious as I am and combined with my total lack of deeper 
Linux knowledge is frustrating. I have tried to get why Ubuntu would 
allow me to do things that them again and again say should not be allowed 
if one are "Live Session User". I find it likely it has to do with this error. 

[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

If I add the .disks or some other named hidden directory 
then that error don't allow me to boot. But if I let the 
.dirs stay in the iso then it only delay the boot and allow me to 
have permissions and priv to do changes that I fail to do due to me 
not familiar with using sudo su and such. I am computer challenged. 

So I trust that .dirs or what name it has contains code that is there 
for to protect the "Live Session User" because in Debian distros AFAIK 
all of them have that protection installed and I fail to change it so 
it give me the permission I get from almost all varieties of Ubuntu. 

I love to have this permissions but I do trust that the Devs will change 
next iso so it plug that hole in the code. Which maybe is needed 
but I would love that Devs would allow me to continue to use Ubuntu 
for always as it does now for the first time. So this "bug" is welcome 
by me but most likely a security risk. 

I tested three different Ubuntu today and two of them allowed me to do everthing I needed and one had a restriction on deleting files. 

zeven OS told me it could not create a trash something. 

Netrunner and Linux Mint both allowed me to delete files on NTFS IIRC. 

I boot using a simplistic boot code for grub4dos on NTFS hdd. Frugal iso booting as some name it. 

one extract the casper dir and the preseed dir out of the iso and then put them in a dir with same name as the iso and put the iso on the c:/ 
or mnt/home/ 



 title Netrunner 2011 frugal iso boot of netrunner-3.2.iso 
 find --set-root --ignore-floppies --ignore-cd /netrunner-3.2.iso
 kernel	/netrunner/casper/vmlinuz rw  file=/cdrom/preseed/netrunner.seed boot=casper iso-scan/filename=/netrunner-3.2.iso noeject noprompt 
 initrd	/netrunner/casper/initrd.lz



 title  Linux Mint 12 RC works ramdisk_size=1048576 root=/dev/ram
 find --set-root --ignore-floppies --ignore-cd /linuxmint-12-gnome-dvd-32bit-rc.iso
 kernel	/LM12/casper/vmlinuz rw  file=/cdrom/preseed/mint.seed boot=casper iso-scan/filename=/linuxmint-12-gnome-dvd-32bit-rc.iso ramdisk_size=1048576 root=/dev/ram noeject noprompt 
 initrd	/LM12/casper/initrd.lz
   

The only bad thing is that one need to tell it what time it is and what keyboard one use and the resolution is not optimal. 

setxkbmap se for Sweden

---


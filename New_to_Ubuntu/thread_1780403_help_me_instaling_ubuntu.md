---
title: "help me instaling ubuntu"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by noobda on 2011-06-11
I Have Already Installed win xp sp2
with 4 partitions 
as 
c: d: e: f:

there is windows in c drive 15 gb
backup and softwares in d drive 150 gb
formated for ubuntu e: drive 150 gb
movies and drives in f: drive 150 gb

i have already tried ubuntu on this pc
with same drives

that time it wont ask me to resize when installing ubuntu
due to booting from windows xp cd ma ubuntu crash
so i have decided to reinstall ubuntu again and deleted linux partitions
and use that space in e drive (formated for ubuntu with ntfs)

so i wanna ask when i try to install ubuntu again ,
using install ubuntu alongside microsoft windows xp professional 

next options is 
write previous changes to disk and continue?
before you can select a new partiton size, any previous 
changes have to be written to disk.
You cannot undo this operation
please note that resize operation may take a long time
go back / continue

what do i have to select ?

if i resize will ma windows xp and all data will be still there or will i loose xp and other data which is in ma drives? 
im agree to give e : drive 150 gb for ubuntu can i do this .. if yes then how can i do it?

plz help me

---

### Post by christoph411 on 2011-06-12
The resize will not delete any of your windows files. But, if you use the install alongside it will NOT install ubuntu in the partition you created for ubuntu, but instead it will create a whole new partition! :( 
So, instead of choosing install alongside, choose the "advanced" option. Once in advanced, choose the partition you specially designated for ubuntu (you will be able to identify this partition because the "used" category will be empty) mark it as "/" , and click next. Everything from there on should be normal :D

---

### Post by 3177 on 2011-06-12
> **noobda said:**
> I Have Already Installed win xp sp2
with 4 partitions 
as 
c: d: e: f:

there is windows in c drive 15 gb
backup and softwares in d drive 150 gb
formated for ubuntu e: drive 150 gb
movies and drives in f: drive 150 gb

i have already tried ubuntu on this pc
with same drives

that time it wont ask me to resize when installing ubuntu
due to booting from windows xp cd ma ubuntu crash
so i have decided to reinstall ubuntu again and deleted linux partitions
and use that space in e drive (formated for ubuntu with ntfs)

so i wanna ask when i try to install ubuntu again ,
using install ubuntu alongside microsoft windows xp professional 

next options is 
write previous changes to disk and continue?
before you can select a new partiton size, any previous 
changes have to be written to disk.
You cannot undo this operation
please note that resize operation may take a long time
go back / continue

what do i have to select ?

if i resize will ma windows xp and all data will be still there or will i loose xp and other data which is in ma drives? 
im agree to give e : drive 150 gb for ubuntu can i do this .. if yes then how can i do it?

plz help me
  
select continue.
sp2 is virus ridden, and EATS memory and space.
You seem to want ubuntu and not xp so...
go for it, and don't look back. I sure didn't.
It IS a learning experience, but you can do it.
If you need anything else just ask.;)

---

### Post by nzjethro on 2011-06-12
It's probably easier to do specify partitions manually. I've got a pretty messed up disk (3 primary partitions, one extended with 2 logicals), and manually specifying seems easier. Instead of selecting "Install alongside", hit "Specify partitions manually"> It'll bring up a Gparted-like menu. Identify your e: drive (or whichever one you want to install Ubuntu on) by the size and the location relative to other partitions. Click that partition, and select change. Format to ext4, and choose / as a mount position.

---

### Post by noobda on 2011-06-12
its giving me 
> you have not selected any partitions for use as swap space.
enabling swap space is recommended so that the system can make btter use of availabe physical memory
and so that it behaves better when physical memory is sarce.
you may experience installation problems if you do not have enough physical memory.

if you do not go back to the partitioning menu and assign a 
awap partition, the installation will continue without swap space.

ma c:drive (windows drive) is 15 gb which is almost 11 gb used for windows programs..

what do i do now?

---

### Post by Paqman on 2011-06-12
How much RAM do you have? You may not need to bother with a swap partition.

---

### Post by noobda on 2011-06-12
i have 3gb ram

---

### Post by nzjethro on 2011-06-12
With 3GB, you probably don't need swap. And if you decide you want it later, you can create a swap file inside your Ubuntu partition, you don't need a separate partition. :D

Click past that, and onto the next step.

---

### Post by noobda on 2011-06-12
ok let me try :)
im unsure dat linux will use ma c drive or e drive when installing cos c is logical.
and its too small :(

---

### Post by Paqman on 2011-06-12
> **noobda said:**
> ok let me try :)
im unsure dat linux will use ma c drive or e drive when installing cos c is logical.
and its too small :(

Linux can install and run from logical drives no problem. 15GB is plenty big enough for Ubuntu.

---

### Post by wildmanne39 on 2011-06-12
> **noobda said:**
> its giving me 


ma c:drive (windows drive) is 15 gb which is almost 11 gb used for windows programs..

what do i do now?Hi, here is a guide that will help you out.
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by noobda on 2011-06-12
ok i have installed on e drive .
and now its not giving me boot options and even its not showing drive in xp?
do i have to write some line in boot.ini in windows xp?
 
like when we go to control panel system and in advance tab
statup and recovery?
we get system startup
there we can edit file boot 
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
 
i googled abt it and i guess i can install grub after installing on logical drive?
using windows?

---

### Post by ILoveYorkies on 2011-06-12
Hi there,
You don't say which Ubuntu version you want to install? I've only install Ubuntu 11.4 :Natty" So that's what my advice is based on. If you can't get your install to work , you could reinstall using my advice. below. Personally, I prefer this method of install: 

                                 [SIZE=2]You could try to install Ubuntu to an external hard drive ( or a flash drive like I have done ). You could either install just Grub2 bootloader to the flash or get a 8 or 16 gb thumbdrive and partition it with Gparted from a livecd or liveusb. First while in Windows change the thumbdrive from removeable (to write cache so you have to always use shutdown safely like when using an external hard drive). Then use a livecd choose try Ubuntu not install. If it boots okay then go to apps and pick Gparted and partition the drive giving 300mbs or less to Grub then you need a root (/) partition then a a swapfile and a /home partition. Then use disk utility to double check which is the the dev names so you install to the correct drive so you don't overwrite your Win partitions nor it's mbr. Or you could install grub to a 4gb or less thumbdrive after partitioning your main Win partition most likely c drive, shrinking it so you can make another partition for Linux. If you do that, MAKE SURE YOU BACKUP OR COPY ALL THE DATA YOU NEED TO KEEP! Shrinking your partition with software for Win or using Gparted usually doesn't BUT IT CAN CORRUPT OR ERASE DATA! If you IMPROPERLY INSTALL GRUB YOU COULD MESS UP Windows MBR BOOTLOADER! That's why I use flash drives and use the "other" or manual check box during install instead of allowing Ubuntu to choose everything. I can then choose the devices to partition myself. I just use the key to pause post so I can choose which drive to boot from, In my case I press Esc then F9 and it lists my Grub drive named Sandisk. I have to do that every time  I want to boot Natty but That's just the way I wanted it. If don't then just go into your bios utility and move the Ubuntu drive to 1st place then Windows drive to 2nd place then every it look for your Grub drive to boot from. If it doesn't find it it boot directly into Win again. So far this method has worked for me. [/SIZE] 
 

 [SIZE=2]If you don't want to install to an external hard drive or usb drive at all you can still use these tips. Just ignore the references to the external or usb drive. In other words. Start here: “Then use a livecd choose try Ubuntu not install. If it boots okay then go to apps and pick Gparted and partition the drive giving 300mbs or less to Grub then you need a root (/) partition then a /swapfile and a /home partition. Then use disk utility to double check which is the the dev names so you install to the correct drive so you don't overwrite your Win partitions nor it's mbr. use the "other" or manual check box during install instead of allowing Ubuntu to choose everything. I can then choose the devices to partition myself. If your computer doesn't boot with the Grub boot menu then just go into your bios utility and move the Ubuntu drive to 1st place then Windows drive to 2nd place then every time you boot or reboot your computer it looks for your Grub drive to boot from and if Grub is installed properly you have a menu giving you the option of booting Ubuntu or the Ubuntu recovery, memtest and your version of Windows in your case XP. If it doesn't find XP, you probably overwrote XP's MBR. You will then need to use Fixmbr from recovery cds you made when you first got your computer or if you can boot into XP but not Ubuntu then you may not have installed Grub correctly which can be fixed by reinstalling it from within a livecd session using the cd that you used to install from. Post back to let me know if you need more details on it. I hope this helps.[/SIZE]
 

Do I understand correctly that you can boot into XP but not into your install of Ubuntu? If so skip to numbers 1. and 2.

Here's a few links that might help you: Here's a couple of guides but they are kind of old but most of their instructions and advice still hold true even if the screens from your livecd version look slightly different.
2 older ones: [http://lifehacker.com/5403100/dual+b...erfect-harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") and this one [https://help.ubuntu.com/community/GraphicalInstall ]("https://help.ubuntu.com/community/GraphicalInstall")

1. Here's a couple with Grub2 info:  [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) and
[http://en.wikipedia.org/wiki/GPart](http://en.wikipedia.org/wiki/GPart)

2. This list from [http://en.wikipedia.org/wiki/List_of_live_CDs#Rescue_and_repair_live_CDs](http://en.wikipedia.org/wiki/List_of_live_CDs#Rescue_and_repair_live_CDs) could help you to find a Grub repair software if using the livecd of Ubuntu that you installed from doesn't help. I think reinstalling Grub from your livecd using Gparted should work for you, if not you could try one of these. I suggest trying SysRescueCD first.

**Rescue and repair live CDs**

 
[LIST]
[*][Billix]("http://en.wikipedia.org/wiki/Billix")  – a multiboot distribution and system administration toolkit with the  ability to install any of the included Linux distributions
[*][BootMed]("http://www.bootmed.com/") – a Live CD that was made to help those not familiar with Linux repair or recover their Windows Computer from a Live CD.
[*][Inquisitor]("http://en.wikipedia.org/wiki/Inquisitor_%28hardware_testing_software%29") – Linux-based hardware diagnostics, stress testing and benchmarking Live CD
[*][Parted Magic]("http://en.wikipedia.org/w/index.php?title=Parted_Magic&action=edit&redlink=1")
[*][RIP: (R)ecovery (I)s (P)ossible]("http://en.wikipedia.org/wiki/Recovery_Is_Possible") is a Linux-based CD with partition tool and network tools ([Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29")), based on the 2.6.17 kernel.
[*][System Folder]("http://en.wikipedia.org/wiki/System_Folder") of [Mac OS]("http://en.wikipedia.org/wiki/Mac_OS") on a [CD]("http://en.wikipedia.org/wiki/Compact_Disc") or on a [floppy disk]("http://en.wikipedia.org/wiki/Floppy_disk") – works on any media readable by [68k]("http://en.wikipedia.org/wiki/68k") or [PowerPC]("http://en.wikipedia.org/wiki/PowerPC") Macintosh computers.
[*][SystemRescueCD]("http://en.wikipedia.org/wiki/SystemRescueCD") is a Linux-based CD with tools for Windows and Linux repairs, based on the 2.6 kernel.
[*][Trinity Rescue Kit]("http://en.wikipedia.org/wiki/Trinity_Rescue_Kit") – Mandriva Linux-based CD for use on a Windows or Linux-based system.
[/LIST]

---

### Post by VOT Productions on 2011-06-12
I recommend you delete E:, and use Ubuntu's installer "advanced" partitioning tool. Then create a new partition (make sure to format it in ext4) and choose that to format it.
It will be much better if you use a USB pendrive. Then, you can run fdisk -l and give us the exact disk(s) layout.

---

### Post by Pra_ap on 2011-06-12
> **noobda said:**
> ok i have installed on e drive .
and now its not giving me boot options and even its not showing drive in xp?
do i have to write some line in boot.ini in windows xp?
 
like when we go to control panel system and in advance tab
statup and recovery?
we get system startup
there we can edit file boot 

 
i googled abt it and i guess i can install grub after installing on logical drive?
using windows?



After installation Linux shows options for booting either Linux or windows. Might be in your case boot loader is not installed. I recommend you to to delete your e drive first and re-install Linux with manual partition option and format e drive with ext4. As you are new to Linux you must create a home partition to keep your data safe if you need to re-install Linux again in future.

---

### Post by wildmanne39 on 2011-06-12
> **noobda said:**
> ok i have installed on e drive .
and now its not giving me boot options and even its not showing drive in xp?
do i have to write some line in boot.ini in windows xp?
 
like when we go to control panel system and in advance tab
statup and recovery?
we get system startup
there we can edit file boot 

 
i googled abt it and i guess i can install grub after installing on logical drive?
using windows?
Hi, if you read my post 11 you will see a link with all the instructions you need to install ubuntu with xp.

---

### Post by bk60544 on 2011-06-22
Also having problem installing 10,10 on 3rd partition [XP and ?Win 7 on others]. Selected format and "/" as mounting point. Now at startup I get "Error: unknown filesystem Grub  rescue>"  Now what??

---

### Post by wildmanne39 on 2011-06-22
> **bk60544 said:**
> Also having problem installing 10,10 on 3rd partition [XP and ?Win 7 on others]. Selected format and "/" as mounting point. Now at startup I get "Error: unknown filesystem Grub  rescue>"  Now what??Hi, did you do a complete install? what are your system specs? Run this command from a terminal 
```
sudo lshw
```and also run this boot script separately.
 post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. Put the outcome from the first text in code brackets also.

---


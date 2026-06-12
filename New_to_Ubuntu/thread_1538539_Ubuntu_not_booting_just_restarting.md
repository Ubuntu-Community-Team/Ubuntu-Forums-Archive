---
title: "Ubuntu not booting just restarting"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Truemedia on 2010-07-25
Iv'e heard that windows doesn't play nice with grub and ubuntu but for some reason a day after I updated a few things on ubuntu update manager (I thinks thats what it's called), I went to boot ubuntu from selection at startup "vista or ubuntu", and everytime i select ubuntu my computer restarts with no errors, and acts as if clicking ubuntu means reboot.

I did nothing with vista recently for it to have an excuse to mess with my ubuntu setup, and I'm sick of going back to vista to get my work done when I want ubuntu for that :( any suggestions?

---

### Post by Paddy Landau on 2010-07-25
I think that somehow your Grub (your boot manager) has got confused.

As a first step, I'd try reinstalling it from the Live CD.
[Reinstall Grub]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
Follow the instructions carefully.

---

### Post by Truemedia on 2010-07-25
Ok i'll give this a try thanks

---

### Post by Truemedia on 2010-07-25
Not working right, I tried the first two methods and just comes up with an error when I load windows, and on the last instruction to enter "sudo update-grub" it just says error "cannot find a device for / (is /dev mounted?) and I've tried doing that with and without rebooting. Now I can't load windows or my normal ubuntu and I'm just stuck with the live Cd. Any suggestions where I'm going wrong? :( Without this been fixed I don't have a computer with software I need to work.

When booting up windows it just says "error: file not found. grub rescue>"

---

### Post by nakama85 on 2010-07-25
> **Truemedia said:**
> When booting up windows it just says "error: file not found. grub rescue>"

are you using 2 hard drives?... If so I had this issue but I fixed it by changing the HD boot order in the BIOS

---

### Post by Paddy Landau on 2010-07-25
OK, let's do this step by step. Starting with the [same instructions]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") under SIMPLEST but with a small variation, do the following.

[LIST=1]
[*]Boot from a Live CD.
[*]Open a terminal (Accessories > Terminal).
[*]Enter the following two commands and **tell us what they say**.
```
sudo fdisk -l
sudo blkid
```
[*]**If** [FONT=Lucida Console]fdisk[/FONT] shows [FONT=Lucida Console]/dev/sda1[/FONT], [FONT=Lucida Console]/dev/sda2[/FONT], etc., and one of them is your Ubuntu partition, then enter the following two commands. Replace *[FONT=Lucida Console]/dev/sda1[/FONT]* with the correct partition. **Tell us what they say**.
```
sudo mkdir /mnt/ub
sudo mount */dev/sda1* /mnt/ub
```
[*]If step 4 went OK, enter the command:
```
sudo grub-install --root-directory=/mnt/ub /dev/sda
```Tell us what it says.
[/LIST]

---

### Post by Truemedia on 2010-07-25
Ok, I recognise those functions from the grub installer link you provided before, this is what I get from "sudo fdisk -l"

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf90c5490

Device Boot       Start                End            Blocks                Id       System
/dev/sda1   *                  1              30402     244196344      7     HPFS/NTFSand then this from "sudo blkid"
> /dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1C647E25647E01B6" TYPE="ntfs" My windows and ubuntu installations are on one harddrive (originally using wubi), and Iv'e tried sda1 since it's the only one to show up at all, land after taking the next two steps ike before and results in "Installation finished. No error reported" But it's always the step after this that goes wrong.

EDIT: [wilee-nilee]("http://ubuntuforums.org/member.php?u=906928") told me to use a bootscript to futher list the specs on my harddrive so here is the response on the terminal from that the info contained in the results text file.

              >   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /grub/core.img 
                       /boot/grub/core.img

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,735   488,392,688   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       db7ca70f-144f-46fa-a532-1e1afe0102b4   ext4                                     
/dev/sda1        1C647E25647E01B6                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1c647e25647e01b6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1c647e25647e01b6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c647e25647e01b6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c647e25647e01b6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c647e25647e01b6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c647e25647e01b6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c647e25647e01b6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c647e25647e01b6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1c647e25647e01b6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


  13.1GB: boot/grub/grub.cfg
  21.7GB: boot/initrd.img-2.6.32-21-generic
  22.1GB: boot/initrd.img-2.6.32-23-generic
  22.4GB: boot/initrd.img-2.6.32-24-generic
  21.7GB: boot/vmlinuz-2.6.32-21-generic
  22.1GB: boot/vmlinuz-2.6.32-23-generic
  22.4GB: boot/vmlinuz-2.6.32-24-generic
  22.4GB: initrd.img
  22.1GB: initrd.img.old
  22.4GB: vmlinuz
  22.1GB: vmlinuz.old

---

### Post by Paddy Landau on 2010-07-25
> **Truemedia said:**
> ... "sudo fdisk -l"

Device boot         Start         End       Blocks      Id        System
/dev/sda1   *               1          30402   244196344   7 HPFS/NFTS
Hmm, now that's puzzling. You have only one partition on your hard drive, which as far as I can tell takes up the entire space.

The partition is NTFS.

So...

Are you sure that you installed Ubuntu on this?

Did you, maybe, install Wubi instead? (Wubi has a very different structure from a native install.)

---

### Post by Paddy Landau on 2010-07-25
Right, you posted new information since my last post.

You installed Wubi.

For future note, once you've got this solved, please remember that Wubi is fantastic for trying out Ubuntu and for experimenting, but it's terribly unstable and no good for long-term use.

As far as I know, you cannot fix a boot into Wubi when it goes wrong -- but I may be incorrect. You may want to search this forum for how to restore Grub for Wubi.

Alternatively, do you have a backup of your important Wubi data? If so, then this is what I want you to do:

[LIST=1]
[*]Boot into Windows. (If you can't do this, then post back here.)
[*]Find a Windows tool to restore your boot loader. I once used [EasyBCD]("http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html") to good effect with Vista.
[*]Uninstall Wubi -- you will lose all data in your Wubi (Ubuntu) installation, which is why I asked about a backup.
[/LIST]
This should solve your problem.

If you still want to go ahead with Ubuntu, **back up all your data** and then do a proper native install of Ubuntu, instead of using Wubi. (The install should be safe, but occasionally it has a serious problem, which is why you need to back up your data. You can back up your entire disk drive using [CloneZilla]("http://clonezilla.org/"), so if everything does go wrong, you can simply restore the entire disk.)

---

### Post by Truemedia on 2010-07-25
I guess that by what you just said it means I don't have ubuntu properly installed. Yes I used wubi and It thought that installed ubuntu, but I think I know now that it creates the dual boot grub, and partition in windows.

My main problem is that I can't login in to windows or the wubi ubuntu.

Although I don't have a solution to this yet, is it best to have a liveCD setup for ubuntu where you have the files saved in windows and you boot up using the CD? or is that a bad idea. The reason I still need windows is because there are a few programs I have paid for that have I havn't another option of on ubuntu.

I plan to have a full ubuntu pc and a seperate mac once I can afford one lol as the best solution so far.

---

### Post by Paddy Landau on 2010-07-25
> **Truemedia said:**
> I guess that by what you just said it means I don't have ubuntu properly installed. Yes I used wubi and It thought that installed ubuntu, but I think I know now that it creates the dual boot grub, and partition in windows.
Nearly correct. Wubi doesn't change the partitions at all.

Wubi is "Windows Ubuntu Installation". It installs Ubuntu *inside* Windows, and as such it is dependent on the vagaries of Windows. It's also unstable and unreliable (as you discovered).

A native installation splits your hard disk into two main *partitions* (areas): One for Windows and one for Ubuntu. (There's actually a small, third partition, known as Swap, which Ubuntu uses.) The process shrinks your Windows partition, then creates two new partitions: One for Ubuntu and a small one for Swap (usually less than 4Gb, depending on your RAM).

(Advanced users often recommend yet another partition: 1: Windows. 2: Linux operating system. 3: /home for data. 4: Swap. But do that only if you're confident mucking about with partitions.)

Grub replaces the normal Windows boot, so when your computer starts, you can choose between Windows and Ubuntu.

As you can see, it's hard to tell the difference between Wubi and Ubuntu; the real difference is reliability, speed and stability.

---

### Post by Truemedia on 2010-07-25
Well I definitely want to be able to use ubuntu again, but the experience I have had in such a short amount of time with wubi makes me want to stay clear away from it. My only problem now is restoring the windows boot as I don't have any fully working operating system. So how would I go with restoring it through a livecd ubuntu?

---

### Post by CompEngStudnt on 2010-07-25
Do you have the directions on how to properly install UBUNTU as in Not the Wubi?
I just had a startup failure today and had to reinstall the whole thing over again from my Windows 7 OS. Not fun, and naturally, I lost all data that I didn't back up. I like UBUNTU and I can do without Win.7

---

### Post by Paddy Landau on 2010-07-26
> **Truemedia said:**
> Well I definitely want to be able to use ubuntu again, but the experience I have had in such a short amount of time with wubi makes me want to stay clear away from it.
OK, that's fair. A new operating system always comes with its problems (can you remember the first time you tried to use Windows?)

If you change your mind and wish to try again, we'll be happy to help. But I do recommend that you stay away from Wubi.

> **Truemedia said:**
> My only problem now is restoring the windows boot as I don't have any fully working operating system. So how would I go with restoring it through a livecd ubuntu?
See my previous [post #9]("http://ubuntuforums.org/showthread.php?p=9635792#post9635792"). You won't use the Ubuntu Live CD. You need a Windows program.

---

### Post by Paddy Landau on 2010-07-26
> **CompEngStudnt said:**
> Do you have the directions on how to properly install UBUNTU as in Not the Wubi?
I just had a startup failure today and had to reinstall the whole thing over again from my Windows 7 OS. Not fun, and naturally, I lost all data that I didn't back up. I like UBUNTU and I can do without Win.7
You don't have to get rid of Windows to have Ubuntu. The two can peacefully co-exist on the same computer. Actually, we recommend that you keep Windows just in case you need it. I got rid of my Windows only after about a year of using Ubuntu and not needing Windows.

The instructions are simple.

[LIST=1]
[*]Download the iso.
[*]Check your download's MD5 sum -- too many people have had corrupt downloads.
[LIST]
[*][Windows MD5 How-To]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")
[*][List of MD5 sums]("https://help.ubuntu.com/community/UbuntuHashes")
[/LIST]
 
[*]Make a Live CD. You can find the instructions on the [download page]("http://www.ubuntu.com/desktop/get-ubuntu/download").
[*]Boot from the Live CD. Play with Ubuntu *without* installing. This will let you know if you have any serious hardware incompatibilities.
[/LIST]
If all goes well, then:

[LIST=1]
[*]Reboot into Windows. **Back up all your data!**
[*]Make sure you uninstall Wubi if you haven't already done so.
[*]I recommend an additional backup using [CloneZilla]("http://clonezilla.org/"), because you can back up and restore your entire disk, saving the hassle of reinstallation should something serious go wrong. But you will need an external hard drive to fit the backup onto.
[*]Reboot on the Live CD and choose to install Ubuntu. Follow the instructions. **If in any doubt,** feel free to cancel (before you commit on the final step) and search the forums or, if you can't find an answer, ask in a new thread.
[/LIST]
One more thing. It will be a good idea to [understand about partitions]("http://en.wikipedia.org/wiki/Disk_partitioning") before you begin. It will help you to know what's going on and how to decide to proceed with the actual installation.

---

### Post by Truemedia on 2010-07-26
I made another post on my idea of how to have windows and ubuntu coexist without wubi and it seems feasable.

I just need to know know how to restore the boot so it us windows only so I can uninstall wubi and use windows again.

---

### Post by Paddy Landau on 2010-07-26
> **Truemedia said:**
> I just need to know know how to restore the boot...

See my **[post #9]("http://ubuntuforums.org/showthread.php?p=9635792#post9635792")**.

---

### Post by Truemedia on 2010-07-26
> **Paddy Landau said:**
> See my **[post #9]("http://ubuntuforums.org/showthread.php?p=9635792#post9635792")**.

I cannot physically install that on my computer because **I dont have an operating system that will load**
so how is that possable. Livecd won't let me install software and I don't have a windows cd.

you said to post back here if I cant boot into windows, and I can't.

---

### Post by CompEngStudnt on 2010-07-26
[QUOTE=Paddy Landau;9637616]You don't have to get rid of Windows to have Ubuntu. The two can peacefully co-exist on the same computer. Actually, we recommend that you keep Windows just in case you need it. I got rid of my Windows only after about a year of using Ubuntu and not needing Windows.
 
   Thank you, Paddy. I understand the Partitions. I created one for Win 7 and one for Vista on each of my laptops, just in case I lost a backup.
 
Thanks again for the directions

---

### Post by Paddy Landau on 2010-07-26
> **Truemedia said:**
> **I dont have an operating system that will load**
Right, you hadn't told me that.

EasyBCD should do the trick for you.

[LIST=1]
[*]Boot from the Live CD.
[*]In your browser, go to [EasyBCD's Super Grub Disk page]("http://neosmart.net/wiki/display/EBCD/Linux#Linux-BootingintoSuperGrubDisk") (the title reads "Booting into Super Grub Disk").
[*]Follow the instructions, which start as:
[LIST]
[*]Click on mirror of [Super Grub Disk]("http://neosmart.net/wiki/download/attachments/360461/Super+Grub+Disk.iso.gz") and save to your Desktop.
[*]Extract the archive to your desktop (right-click and select Extract Here).
[*]Delete the archive (not the extract) (click it once, press Shift-Delete). This step is to release RAM for your computer.
[*]Burn the ISO to a CD (right-click and select Write to Disc).
[/LIST]
 
[/LIST]
Continue to follow the instructions.

---

### Post by Truemedia on 2010-07-26
Iv'e  seen something called FreeBIOS while googling around for a solution but it needs windows installed first :(

Anybody got a solution to the boot (last post on this topic)? I am really in need of getting access to my software.
:confused:

---

### Post by Paddy Landau on 2010-07-26
> **Truemedia said:**
> Anybody got a solution to the boot (last post on this topic)?
You might have just missed my [last post]("http://ubuntuforums.org/showthread.php?p=9638667#post9638667"), as we seem to have posted at the same time.

---

### Post by Truemedia on 2010-07-26
Oh totally missed that lol, K i'll try that now thanks.

EDIT: I did what you said and the cd writer seems to be stuck. Iv'e left it for 15 minutes and it still says "preparing to write". I tried adding the cd image to my external hard drive to conserver ram but the livecd can't see it. Would any of this not work if I only have one cd drive?

---

### Post by oldfred on 2010-07-26
You can install a window like boot loader that works with any windows from Ubuntu liveCD.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR


You can & should have a recovery disk for windows. Even after you get it going again.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Paddy Landau on 2010-07-26
> **Truemedia said:**
> I did what you said and the cd writer seems to be stuck...
Sorry, that doesn't seem right at all. Reboot and try again to write to the CD (you have the ISO on your external drive, right?).

Alternatively, you can try [what oldfred said]("http://ubuntuforums.org/showthread.php?p=9638992#post9638992").

---

### Post by Truemedia on 2010-07-26
YEEEEES! \\:D/ Back up and running windows (never thought I'd be so happy about that before) exactly where I left off.

Thank you so much paddy and oldfred, you got me through a harsh time.
Now I am definitely deleting wubi and backing up in the preparation of using my external hard drive as my ubuntu installation.

I will refer to this if the worst happens again, unlikely to repeat itself, and I look forward to really starting to use ubuntu, thanks again :D.

---

### Post by oldfred on 2010-07-26
Glad you got it working.

If you are going to install to a second drive, you need to make sure you install grub to the second drive, it will try to default to sda the internal.
You have to use the advanced button to control where grub installs. Karmic screens are similar to Lucid for the install:

Install karmic Screens shown with advanced button
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives win & 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by Paddy Landau on 2010-07-26
> **Truemedia said:**
> YEEEEES! \\:D/ Back up and running windows...
Good news!

Please remember to mark the thread as Solved.

Further to what oldfred said, installing on an external hard drive is possible but a bit more complex. You can refer to these pages if you want to install on an external hard drive:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1478020](http://ubuntuforums.org/showthread.php?t=1478020)
[*][http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[*][http://ubuntuforums.org/showthread.php?p=9634377#post9634377](http://ubuntuforums.org/showthread.php?p=9634377#post9634377)
[/LIST]

---


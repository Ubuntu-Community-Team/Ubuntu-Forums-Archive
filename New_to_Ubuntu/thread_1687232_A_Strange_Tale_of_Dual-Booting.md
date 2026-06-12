---
title: "A Strange Tale of Dual-Booting"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Andavane on 2011-02-13
I had Windows-7 dual booting with Wubi inside.
Magnificent.
I need Win-7 because I frequently need to access my Amazon Kindle and refer to my books. Wubi Ubuntu used nearly all the time.
Went to India for 3 months.
Slow connection in Internet Café.

One fine day, Wubi makes a major update one day (takes ages to download its files). Asks for reboot.

I select Ubuntu in the Boot manager and am astonished to see it only boots into Windows now. Thinking I miss-keyed, I repeat the process, this time watching closely. Only two lines of text appear in the Linux bit, and again it flicks back into Windows. Again and again and again, it refuses Ubuntu.

I'm dismayed, yet nonetheless am glad I have dropbox and extra backups, so am able to carry on working. Because of the pain of redoing it all there, I determine to attend to it on return to UK, where my connection is better.

So I'm already to do it again tonight, but a small voice whispers "Try Again Before You Uninstall". So I do, again the crippled two line come in  Bootloader and then

BINGO! I'm flicked into the normal booting Menu!!!

Wubi Ubuntu updates itself and reboots just fine!!!

Now my post is, What Happened? What to do if it happens again?

Any clues, technical guys an gals?

One clue: The crippled two-line still appears, then flicks into normal boot display.

INFO: I know nothing about bootloaders and stuff ~ way beyond me!

Kind reagrds,

John

---

### Post by JRV on 2011-02-13
There is a bug in grub2 that causes a wubi installation not to boot after an upgrade.

These threads explain it:

[http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi)

[http://ubuntuforums.org/showthread.php?t=1663404](http://ubuntuforums.org/showthread.php?t=1663404)

To avoid the problem in the first place, when doing an update uncheck grub-pc and grub-common.

---

### Post by Rubi1200 on 2011-02-13
As JRV correctly pointed out, there are issues with Wubi and GRUB updates.

In the main post of the thread he linked to you will find a section called Permanent Fix. Just after that is information on locking the grub packages; you need to do this part.

If you have more questions, feel free to ask.

---

### Post by Jazzy_Jeff on 2011-02-14
> **Andavane said:**
> I had Windows-7 dual booting with Wubi inside.
Magnificent.
I need Win-7 because I frequently need to access my Amazon Kindle and refer to my books.


I am not sure why you need Win-7 for your Kindle. I have a Kindle and have not had any problems accessing it through Ubuntu. I also use a program called Calibre to manage all my books.

---

### Post by Andavane on 2011-02-15
> **JRV said:**
> There is a bug in grub2 that causes a wubi installation not to boot after an upgrade.

These threads explain it:

[http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi)

[http://ubuntuforums.org/showthread.php?t=1663404](http://ubuntuforums.org/showthread.php?t=1663404)

To avoid the problem in the first place, when doing an update uncheck grub-pc and grub-common.

Yes indeed: The first link has it...
> **Rubi1200 said:**
> As JRV correctly pointed out, there are issues with Wubi and GRUB updates.

In the main post of the thread he linked to you will find a section called Permanent Fix. Just after that is information on locking the grub packages; you need to do this part.

If you have more questions, feel free to ask.

Indeed! Thanks for navigating me str8 to the bit I need! :-)
It's still a mystery to me why the wubi should appear broken, and then for no apparent reason just start working again.

PS: > **Jazzy_Jeff said:**
> I am not sure why you need Win-7 for your Kindle. I have a Kindle and have not had any problems accessing it through Ubuntu. I also use a program called Calibre to manage all my books.

Calibre will work just great if the books are out of copyright, but not where there's DRM protection. I'd be very surprised indeed if Kindle for Ubuntu would read the books I have purchased.

---

### Post by Rubi1200 on 2011-02-15
> It's still a mystery to me why the wubi should appear broken, and then for no apparent reason just start working again.
Indeed! We have actually noticed this happen a few times now. Unfortunately, there does not seem to be any conclusive evidence for when or how this happens and the matter has not been fully researched.

Good news is that you have a place to go now should this ever happen again.

---

### Post by Jazzy_Jeff on 2011-02-15
I don't use Calibre to read the books in copyright. You can change the metadata however you like. I like to change the titles of some of the books so that I can put them in order for series. If you want to use a Kindle app then you could use Kindle for PC under Wine which works great. Your choice though.

---

### Post by Andavane on 2011-02-16
>> **Jazzy_Jeff said:**
> I don't use Calibre to read the books in copyright. You can change the metadata however you like. I like to change the titles of some of the books so that I can put them in order for series. If you want to use a Kindle app then you could use Kindle for PC under Wine which works great. Your choice though.
Last time I tried this on Wine, it failed.
There are other reasons fir Win7 over Linux: (i)the part of India I visit has painfully slow connection, & Ubuntu updates a lot, (ii) Mobipocket doesn't make a linux desktop program, and I have books from them too.
Would love to be Ubuntu through and thriugh tho. Win7 is torture when I use it.
> **JRV said:**
> There is a bug in grub2 that causes a wubi installation not to boot after an upgrade.

These threads explain it:

[http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi)

[http://ubuntuforums.org/showthread.php?t=1663404](http://ubuntuforums.org/showthread.php?t=1663404)

To avoid the problem in the first place, when doing an update uncheck grub-pc and grub-common.
Having set it was fixed, it's gone on me again!
All I get when I try to boot into Ubuntu now is something about limited bash commands, then it says
grub>
or something. Then I type exit, then f2 then shut-down (I think, from memory).
I'm beginning ti think I should use "proper" dual-booting to avoid the problem. However I have one spare partition on my disk and some reason Ubuntu gives warning saying it will erase the entire disk when I try dual-booting, so I back off.

---

### Post by Rubi1200 on 2011-02-16
Hi Andavane,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Andavane on 2011-02-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

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
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   625,137,663   624,728,064   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    15,523,839    15,515,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a1004869-b307-4bad-b645-a316246c1ed4   ext4                                     
/dev/sda1        364C88B94C887581                       ntfs       SYSTEM                        
/dev/sda2        7EBA92DFBA92936F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3731-3932                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sdb1        /media/3731-3932         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sda2/Wubi/etc/fstab: =============================

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

================= sda2/Wubi: Location of files loaded by Grub: =================


  26.4GB: boot/initrd.img-2.6.32-24-generic
   1.8GB: boot/initrd.img-2.6.32-25-generic
   2.0GB: boot/initrd.img-2.6.32-26-generic
   2.1GB: boot/initrd.img-2.6.32-28-generic
  11.3GB: boot/vmlinuz-2.6.32-24-generic
  11.4GB: boot/vmlinuz-2.6.32-25-generic
  11.5GB: boot/vmlinuz-2.6.32-26-generic
  11.5GB: boot/vmlinuz-2.6.32-28-generic
   2.1GB: initrd.img
   2.0GB: initrd.img.old
  11.5GB: vmlinuz
  11.5GB: vmlinuz.old
```

---

### Post by Andavane on 2011-02-16
NB: I mailed the Results.txt file to another machine & posted it from there.
Trust this is OK.

---

### Post by bcbc on 2011-02-16
You're missing the grub.cfg file. That would explain why it's not booting - although I'd expect a grub prompt, not a reboot in this case. And it wouldn't explain why it sometimes boots.

So perhaps the file is corrupted.

Boot the live CD, and fsck it:
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk

```
while you there might as well check it:
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
ls /mnt/boot/grub/grub.cfg
ls -l /mnt/boot/grub | wc -l
```

The first command shows whether the grub.cfg exists, the second should output the number 2 showing 2 files in the /boot/grub directory for wubi installs. Otherwise, if it's 29 or thereabouts, you may have the boot problems shown in the Wubi megathread (problem 2, solution 1)

You can follow the solution 1 then, and then reboot into Wubi and run the permanent fix afterwards.

If you get errors along the way stop and report back.

---

### Post by Andavane on 2011-02-20
> **bcbc said:**
> You're missing the grub.cfg file. That would explain why it's not booting - although I'd expect a grub prompt, not a reboot in this case. And it wouldn't explain why it sometimes boots.

So perhaps the file is corrupted.

Boot the live CD, and fsck it:
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk

```
while you there might as well check it:
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
ls /mnt/boot/grub/grub.cfg
ls -l /mnt/boot/grub | wc -l
```

The first command shows whether the grub.cfg exists, the second should output the number 2 showing 2 files in the /boot/grub directory for wubi installs. Otherwise, if it's 29 or thereabouts, you may have the boot problems shown in the Wubi megathread (problem 2, solution 1)

You can follow the solution 1 then, and then reboot into Wubi and run the permanent fix afterwards.

If you get errors along the way stop and report back.

Social commitments prevented me returning to this thread sooner.
Now, I am trying to get this.
The results of typing in the instructions you gave are:

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/win
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/media/win/ubuntu/disks/root.disk: recovering journal
/media/win/ubuntu/disks/root.disk: clean, 246405/1905008 files, 3121696/7614464 blocks
ubuntu@ubuntu:~$ sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
ubuntu@ubuntu:~$ ls /mnt/boot/grub/grub.cfg
ls: cannot access /mnt/boot/grub/grub.cfg: No such file or directory
ubuntu@ubuntu:~$ ls -l /mnt/boot/grub | wc -l
ls: cannot access /mnt/boot/grub: No such file or directory
0
ubuntu@ubuntu:~$ 
I have established that it's problem #2 given in this thread:
[http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi]("http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi")
but can't edit the grub as there is no grub.

How to proceed now?

Thank you for your patience!

---

### Post by bcbc on 2011-02-20
When you boot Ubuntu and end up at the grub command prompt, enter the following:
```
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro 
initrd /initrd.img
boot
```

Then once booted, 
```
sudo mkdir /boot/grub
sudo update-grub

```

Check the output of the last command and make sure that it create the grub.cfg file without errors (less /boot/grub/grub.cfg )

Report any exceptional output.

---

### Post by Andavane on 2011-02-21
@bcbc:
First of all, MAGIC!
Yes that worked great and many thanks!
Unfortunately, in my sheer excitement I forgot the password when booting in, and before going to the other machine to check I shut this HP machine down, which is probably the stupidest thing to do. :oops:

When I repeated the process I got a load of text, some of which I've written down on paper by hand:

> 
initramfs
gave up waiting for root device
Common problems
- Boot args (cat /proc /cmdline)
- Check root delay (did the system wait long enough?)
Chjeck root (did system wait for the right device?)
-Missing modules (cat /proc /modules; ls /dev)
ALERT! does not exist. Dropping to a shell!

 I could've kicked myself for not leaving it on while I checked! ](*,)

Anything I can do or shall I uninstall the Wubi and start afresh? (having learned from this experience, hopefully).

Thanks again.

---

### Post by bcbc on 2011-02-21
> **Andavane said:**
> @bcbc:
First of all, MAGIC!
Yes that worked great and many thanks!
Unfortunately, in my sheer excitement I forgot the password when booting in, and before going to the other machine to check I shut this HP machine down, which is probably the stupidest thing to do. :oops:

When I repeated the process I got a load of text, some of which I've written down on paper by hand:



 I could've kicked myself for not leaving it on while I checked! ](*,)

Anything I can do or shall I uninstall the Wubi and start afresh? (having learned from this experience, hopefully).

Thanks again.

I think you might have some other issue... that's not normal to be able to boot one time and then following that get the initramfs error. At least I cannot explain that... did anything else happen when you booted up? Did you shutdown normally?

Have you had any other weird system problems e.g. blue screens, while booting Windows?

If everything else is normal, try the full booting instructions - just in case:
```
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```

Any errors you see report back. 


PS it doesn't hurt to run chkdsk from Windows now and then, and also defrag. If you decide to reinstall it's a good idea as well.

---

### Post by Andavane on 2011-02-22
@bcbc:

>"I think you might have some other issue... that's not normal to be able to boot one time and then following that get the initramfs error. At least I cannot explain that... did anything else happen when you booted up? Did you shutdown normally?"
I remember panicking when it wouldn't accept my password. After several fruitless attempts at logging in, I shut down using the little icon on the right at the bottom of the log-in window.
Booting up returned me to grub and I repeated the steps you gave me. A mistake I think. I should perhaps have reported back, but didn't like the thought of leaving the machine on at the login window.

>"Have you had any other weird system problems e.g. blue screens, while booting Windows?"

There have been no blue screens on this HP ultra mobile machine.

I ran defrag, but couldn't fing where chkdsk was on Win-7.

The final "just in case" instructions were not successful here. Good idea to try though.

Am off to Win-7 to uninstall the Wubi then install again.

I feel I've learnt a lot here and will be more alert if it happens again.

Ideally though, I'd like to install Windows in the one spare partition on this machine, but am fearful of issues. Using Wubi on a Win machine is OK as I keep all my data on dropbox and on a portable hard drive, so it's no bother really.

Best for me is just a sole dedicated ubuntu machine.

---

### Post by bcbc on 2011-02-22
If you have plenty of RAM you can try running [Ubuntu in virtualbox]("http://www.psychocats.net/ubuntu/virtualbox").  It's useless for me - I don't have enough RAM so it hobbles both Windows and Ubuntu - but it's certainly an option on some of these newer model machines. (I'd say you'd need 1GB or more RAM just for the virtual machine, and at least that amount on Windows to make it run half-decently).

Note: this doesn't show how Ubuntu runs natively - and probably won't have the potential full performance e.g. graphics. But on the other hand, you should't have any problems either.

Chkdsk... I right click on My computer, Properties, Tools, Check disk for errors (select fix automatically). That's XP but it's probably similar for Win7.

---

### Post by Andavane on 2011-02-25
> **bcbc said:**
> If you have plenty of RAM you can try running [Ubuntu in virtualbox]("http://www.psychocats.net/ubuntu/virtualbox").  It's useless for me - I don't have enough RAM so it hobbles both Windows and Ubuntu - but it's certainly an option on some of these newer model machines. (I'd say you'd need 1GB or more RAM just for the virtual machine, and at least that amount on Windows to make it run half-decently).

Note: this doesn't show how Ubuntu runs natively - and probably won't have the potential full performance e.g. graphics. But on the other hand, you should't have any problems either.

Chkdsk... I right click on My computer, Properties, Tools, Check disk for errors (select fix automatically). That's XP but it's probably similar for Win7.

Hi @bcbc:
> **bcbc said:**
> If you have plenty of RAM you can try running [Ubuntu in virtualbox]("http://www.psychocats.net/ubuntu/virtualbox").  It's useless for me - I don't have enough RAM so it hobbles both Windows and Ubuntu - but it's certainly an option on some of these newer model machines. (I'd say you'd need 1GB or more RAM just for the virtual machine, and at least that amount on Windows to make it run half-decently).
Good idea, but I don't have enough RAM I'm sure (I think this machine is 2 Gg, of course they always encourage you to buy more)

Anyway, I got the Wubi up-and-running again, no probs, and actually feel I had a good time with this thread, and learnt some stuff too. Only one thing was last night, this wubi thing seemed totally WEIRD: battery indicator flashing on and off, some of the keyboard letters showing incorrectly ( ? symbol showed as + sign). All very strange; and called my friend oer to check I wasn't seeing things. Left all alone (Instead of posting to here) and today everything working normally, so heaven knows what that was!
I did the chkdsk thing. Buried deep and difficult to find in Win-7, they don't make it easy. Anyway you just right click on the drive u want to check, properties, tools... but they call it "error checking" but it's chkdsk just the same. Anyway all clear in that dept.
Anyway mate, cheers for all the help.
Off to click SOLVED to the thread and hope it doesn't rear its head again.
Will investigate regular dual booting too I think :)

---


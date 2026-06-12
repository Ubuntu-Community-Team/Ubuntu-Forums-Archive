---
title: "Lynx killed Windows 7"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2010-04-29
Hey everyone, so I updated from 9.10 to 10.04 and I restarted my PC. I went to boot into Windows 7 and all I get is a black screen.

I figured Grub went haywire, so I tried a fresh install of 10.04 and Grub. Same problem.

Ideas of how to fix the situation? I'm still configuring this install, but I'm open to suggestions!

:P

---

### Post by Sealbhach on 2010-04-29
Let's check of your Windows partiton is still there. Please run

```
sudo fdisk -l 
```

in a terminal and paste the result here.

.

---

### Post by Lazy-buntu on 2010-04-29
Yeah, Windows 7 is still there. It's at /sda1

I'm able to mount it and my data is still there.

I'm guessing it's a grub problem?

---

### Post by Sealbhach on 2010-04-30
Right, well the next thing I would try is to reinstall grub from the Live CD:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

.

---

### Post by Lazy-buntu on 2010-04-30
Didn't the fresh install of 10.04 install grub again? It removed the extra entries at least.

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> Didn't the fresh install of 10.04 install grub again? It removed the extra entries at least.

I would just try it anyway.  it might give you some more information on the problem. Also,
do

```
cat /boot/grub/grub.cfg
```

```
cat /etc/default/grub
```

and post the results here, so we can see what it looks like. The problem is probably passing from Grub to the chainloader for Windows.


.

---

### Post by Lazy-buntu on 2010-04-30
ubuntu@ubuntu:~$ cat /boot/grub/grub.cfg

cat: /boot/grub/grub.cfg: No such file or directory


ubuntu@ubuntu:~$ cat /etc/default/grub


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by Lazy-buntu on 2010-04-30
I get confused, where should Grub2 be installed? On /sda (the boot hard drive), /sda1 (windows), or /sda5 (ubuntu)

I'm not proficient when it comes to installing grub, but I figure that's a good first step.:)

---

### Post by Objekt on 2010-04-30
> **Lazy-buntu said:**
> I get confused, where should Grub2 be installed? On /sda (the boot hard drive), /sda1 (windows), or /sda5 (ubuntu)

I'm not proficient when it comes to installing grub, but I figure that's a good first step.:)

You seem to only have one hard drive, which GRUB2 calls sda.  That is shorthand for "first SCSI/SATA hard drive I see."  This is a Good Thing, as it simplifies matters.

Seeing the output of fdisk - l will confirm that is the case.  Please post it when you get a chance.

---

### Post by Lazy-buntu on 2010-04-30
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059ad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19123   153602338+   7  HPFS/NTFS
/dev/sda2           19123       32763   109564928    7  HPFS/NTFS
/dev/sda3           32764       80620   384411352+   7  HPFS/NTFS
/dev/sda4           80621       91201    84991852    5  Extended
/dev/sda5           80621       90181    76798701   83  Linux
/dev/sda6           90182       91201     8193118+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026e09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15936   128000000    7  HPFS/NTFS
/dev/sdb2           15936       29576   109568000    7  HPFS/NTFS
/dev/sdb3           29576       77826   387560448    7  HPFS/NTFS

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> ubuntu@ubuntu:~$ cat /boot/grub/grub.cfg

cat: /boot/grub/grub.cfg: No such file or directory



This is strange, you don't have a grub.cfg ?

Run 

```
sudo update-grub
```

and see if it is created.

.

---

### Post by Lazy-buntu on 2010-04-30
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

It cannot find a device for /, so there's something wrong.

I would try to reinstall grub if I were you:, using this method:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Install it to where your Ubuntu is, /sda5 and let us know how it works out.

.

---

### Post by Lazy-buntu on 2010-04-30
It's not being kind to me:

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> It's not being kind to me:

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

Sorry, my mistake, you only need to state /dev/sda

like so
> 
*sudo grub-install --root-directory=/mnt/ /dev/sd**a***

You have already mounted /dev/sda5 so that's fine.

.

---

### Post by Lazy-buntu on 2010-04-30
I did:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

It said it installed without any errors. I rebooted and Windows 7 still doesn't boot. It gives me a black screen with a cursor. I'm rebooting the live cd as we speak.

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> I did:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

It said it installed without any errors. I rebooted and Windows 7 still doesn't boot. It gives me a black screen with a cursor. I'm rebooting the live cd as we speak.

OK, maybe the Windows bootloader is damaged, you could boot up from the Windows DVD and repair the Windows MBR.

.

---

### Post by Lazy-buntu on 2010-04-30
I hope that's not too serious. I'm loading my windows 7 pro install cd now. I'll see what I can do.

Edit: it's only an install CD. No recovery options :(

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> I hope that's not too serious. I'm loading my windows 7 pro install cd now. I'll see what I can do.

It should be easy to do.

Are you getting any options like these?

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

A better how-to here:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

.

---

### Post by Lazy-buntu on 2010-04-30
I saw install and didn't go any further. I'm going to try [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> I saw install and didn't go any further. I'm going to try [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

I linked you to a better how-to, with screenshots

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Yes, you have to press Install, then choose Language and in the screen after that you fix things.

.

---

### Post by Lazy-buntu on 2010-04-30
Yeah, I'm going to go that route now. I was thinking about messing with my computer later on, but at this rate I don't know if I should lol.

---

### Post by Lazy-buntu on 2010-04-30
Followed the tutorial, now I've got no Grub. I'm going to boot the live cd again.

---

### Post by Sealbhach on 2010-04-30
That's as expected, yeah.

.

---

### Post by Lazy-buntu on 2010-04-30
Should I run those two commands before to install grub, or do sudo update-grub?

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> Should I run those two commands before to install grub, or do sudo update-grub?

I'm not sure what you mean, just follow that how-to on reinstalling Grub.

.

---

### Post by Lazy-buntu on 2010-04-30
All right, reinstalled grub. I can boot into ubuntu again. If I try to boot into Windows 7 it restarts the computer.

I booted into ubuntu and did sudo update-grub and it does have a cfg file now.

Tried to reboot into windows and I get the blinking cursor again...

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> All right, reinstalled grub. I can boot into ubuntu again. If I try to boot into Windows 7 it restarts the computer.

I booted into ubuntu and did sudo update-grub and it does have a cfg file now.

Tried to reboot into windows and I get the blinking cursor again...

Ugh, sorry I'm at the end of my knowledge now.

I can only suggest posting a bug report and start a new post here saying what you've done. Sorry it's not working for you.

EDIT: Also look at this thread just posted, looks like a similar issue:

[http://ubuntuforums.org/showthread.php?t=1466824](http://ubuntuforums.org/showthread.php?t=1466824)

.

---

### Post by Lazy-buntu on 2010-04-30
I'm gonna try a fresh install of Karmic. I'm only concerned with getting Windows back at this point. I'll let you know if that fixes the problem.

---

### Post by bcbc on 2010-04-30
> **Lazy-buntu said:**
> I'm gonna try a fresh install of Karmic. I'm only concerned with getting Windows back at this point. I'll let you know if that fixes the problem.

Hold on there is a fix for this... I'm going to find the posts for you

---

### Post by bcbc on 2010-04-30
Here's the relevant post from oldfred showing the fix... [http://ubuntuforums.org/showpost.php?p=9198588&postcount=6](http://ubuntuforums.org/showpost.php?p=9198588&postcount=6)

You can read the entire thread if you want to here [http://ubuntuforums.org/showpost.php?p=9198588](http://ubuntuforums.org/showpost.php?p=9198588)

---

### Post by Lazy-buntu on 2010-04-30
You posted about 5 minutes too late :(

I'm going to see if Karmic fixed it, if not I'll try your method.

Thanks :)

---

### Post by Lazy-buntu on 2010-04-30
Karmic made things worse. Going back to Lucid. I'll try your method in about 10 minutes.

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> Karmic made things worse. Going back to Lucid. I'll try your method in about 10 minutes.

Looks like you're not the only with this. I noticed this bit from what Cappy1 [said about how he/she fixed it]("http://ubuntuforums.org/showthread.php?p=9198588#post9198588"):

 > I did run the Win 7 recovery repair multiple times but that did not fix  the boot record. I dicked around with the bootrec.exe commands and it  wasn't until I did the bootrec.exe /fixboot that I got my MBR back  successfully such that I could boot directly into the windows disk if  that disk was selected first in the PC Bios.

.

---

### Post by Lazy-buntu on 2010-04-30
I don't have any OS on my 2nd hard drive, so our situations aren't exactly similar, but I'll give it a go. I'm running a chkdsk /r for the hell of it. My next steps will be:

BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

I'll let you know how it turns out. So is this a general bug or what? I'm surprised this type of bug made it into the release.

---

### Post by Lazy-buntu on 2010-04-30
> **Lazy-buntu said:**
> I don't have any OS on my 2nd hard drive, so our situations aren't exactly similar, but I'll give it a go. I'm running a chkdsk /r for the hell of it. My next steps will be:

BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

I'll let you know how it turns out. So is this a general bug or what? I'm surprised this type of bug made it into the release.

Executed all of the commands successfully. chkdsk came back with no errors. Still blinking cursor when I go to boot Windows 7.

I'm going to try bootrec.exe /fixboot again and let you know how that turns out.

---

### Post by bcbc on 2010-04-30
> **Lazy-buntu said:**
> I don't have any OS on my 2nd hard drive, so our situations aren't exactly similar, but I'll give it a go. I'm running a chkdsk /r for the hell of it. My next steps will be:

BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

I'll let you know how it turns out. So is this a general bug or what? I'm surprised this type of bug made it into the release.

What I think happens is that grub2 installs itself to the boot sector of the windows partition. In earlier betas, the grub2 upgrade by default installed to every MBR and partition it found (all were selected and you had to manually click off the ones you didn't want). In the release version, it appears they are all checked off by default i.e. grub2 won't install anywhere unless you tell it to.

However, there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996") that seems to indicate that sometimes grub2 is installed regardless of selections. I am assuming that you didn't select to install grub2 to your windows partition, so clearly the bug is still not solved.

---

### Post by Lazy-buntu on 2010-04-30
Running the bootrec.exe /fixboot did not fix my problem. Still blinking cursor.

This is getting frustrating. I'm running out of options :(

---

### Post by Lazy-buntu on 2010-04-30
When I upgraded to 10.04 it said something like install grub on every partition if you're not sure where to install it. I did on every partition on sda, but most failed. That's when I did a fresh install of Karmic.

Does that help narrow down the problem? 

> **bcbc said:**
> What I think happens is that grub2 installs itself to the boot sector of the windows partition. In earlier betas, the grub2 upgrade by default installed to every MBR and partition it found (all were selected and you had to manually click off the ones you didn't want). In the release version, it appears they are all checked off by default i.e. grub2 won't install anywhere unless you tell it to.

However, there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996") that seems to indicate that sometimes grub2 is installed regardless of selections. I am assuming that you didn't select to install grub2 to your windows partition, so clearly the bug is still not solved.

---

### Post by bcbc on 2010-04-30
> **Lazy-buntu said:**
> When I upgraded to 10.04 it said something like install grub on every partition if you're not sure where to install it. I did on every partition on sda, but most failed. That's when I did a fresh install of Karmic.

Does that help narrow down the problem?

OK, that was a mistake. The advice is bad. I do recall seeing the same thing, but I already knew to ignore it. Maybe you should register a bug that the text is misleading. At the very least, the 'install to partition' option should be buried within an 'Advanced users only' button.

So, basically what happened is when you installed grub to your windows partition it pooched windows.

Anyway, first try oldfred's advice - I think he said you may have to do it repeatedly. 

If it still doesn't work, this link will do the trick... 
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Evil Rabbit on 2010-04-30
Hi!

Lazy, have you tried to enter Windows from GRUB command line? I had a same kind of a problem with my XP after installing Lynx. It seems that os-prober is not working correctly for me. Had to manually add a Win entry in the GRUB. I am also wondering what does your grub.conf look like at the moment. But anyways, try this:

When GRUB menu appears, enter command line (type "c") and pass the following commands:

insmod ntfs
insmod chain
set root=(hd0,1)     (this is your Win boot partition, sda1)
chainloader +1
boot

If you are able to boot into Windows, then I can tell you how to set things in Ubuntu... If not, maybe your problem is not related to mine.

---

### Post by Lazy-buntu on 2010-04-30
This gives me the dreaded blinking cursor again :(

> **Evil Rabbit said:**
> Hi!

Lazy, have you tried to enter Windows from GRUB command line? I had a same kind of a problem with my XP after installing Lynx. It seems that os-prober is not working correctly for me. Had to manually add a Win entry in the GRUB. I am also wondering what does your grub.conf look like at the moment. But anyways, try this:

When GRUB menu appears, enter command line (type "c") and pass the following commands:

insmod ntfs
insmod chain
set root=(hd0,1)     (this is your Win boot partition, sda1)
chainloader +1
boot

If you are able to boot into Windows, then I can tell you how to set things in Ubuntu... If not, maybe your problem is not related to mine.

---

### Post by bcbc on 2010-04-30
ok here is a post by meierfra who knows what he is talking about:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Sealbhach on 2010-04-30
make sure to try bcbc's suggestion:

> **bcbc said:**
> 

If it still doesn't work, this link will do the trick... 
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Evil Rabbit on 2010-04-30
OK. So are you positive that both Windows and Ubuntu are on the same disk (sda)? There seems to be Windows partitions also on sdb.

---

### Post by Lazy-buntu on 2010-04-30
> **Evil Rabbit said:**
> OK. So are you positive that both Windows and Ubuntu are on the same disk (sda)? There seems to be Windows partitions also on sdb.

I'm positive, I put in the 640GB drive after the 750 for back ups only. There should only be data on sdb

---

### Post by Lazy-buntu on 2010-04-30
> **Sealbhach said:**
> make sure to try bcbc's suggestion:

Working on it :popcorn:

---

### Post by Lazy-buntu on 2010-04-30
Grub was killed again, I'm going to see if I can at least get windows going based on something on: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

edit: I'm on Step Four: Nuclear Holocaust

Do I proceed?

---

### Post by Evil Rabbit on 2010-04-30
The problem is that fixing the Windows boot loader will overwrite Ubuntu GRUB and reinstalling GRUB in Ubuntu will overwrite the Win data, because the os-prober does not seem to work. So next time you should maybe try to install the GRUB to /dev/sda5 (force it) and add the Windows entry manually.

My favorite scenario is to install Win and Ubuntu do different physical disks with separate GRUBs, so they do not interfere with each other and if problems occur, one can change the boot priority in BIOS.

Hope you'll sort it out.

---

### Post by Lazy-buntu on 2010-04-30
> **Evil Rabbit said:**
> The problem is that fixing the Windows boot loader will overwrite Ubuntu GRUB and reinstalling GRUB in Ubuntu will overwrite the Win data, because the os-prober does not seem to work. So next time you should maybe try to install the GRUB to /dev/sda5 (force it) and add the Windows entry manually.

My favorite scenario is to install Win and Ubuntu do different physical disks with separate GRUBs, so they do not interfere with each other and if problems occur, one can change the boot priority in BIOS.

Hope you'll sort it out.

I did step 4, no luck. I'm going to run a few more commands and boot back into the Lucid live CD.

I really don't want to resort to a fresh Windows install. If I have to do that, I won't bother putting Ubuntu back on that PC.

---

### Post by Evil Rabbit on 2010-04-30
I understand your frustration. I messed up my system when upgrading to 9,10 and had to install XP from scratch. This time the problems were not very serious and easy to fix. Your case seems to be more complicated than mine. The key to your satisfaction lies in rescuing the Win boot loader. I cannot help much with it as I have no experience with Vista / 7.

---

### Post by WitchCraft on 2010-04-30
I'm pretty much in the same situation.
The Nvidia graphics driver crashed and killed the boot partition...

---

### Post by oldfred on 2010-04-30
It sounds like you are going back and forth with grub & windows. So we can see where everything is at run this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by japrime on 2010-04-30
Here's what fdisk shows for my drives, with multiple hard drives in use. Windows 7 appears to still be on sdh1:

john@john-desktop:~$ sudo fdisk -l
[sudo] password for john: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x201ff03d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       65079   522746043+   7  HPFS/NTFS
/dev/sda2           65080       91201   209824965    5  Extended
/dev/sda5           65080       90137   201278353+  83  Linux
/dev/sda6           90138       91201     8546548+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd1135a43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       58444   469451398+   7  HPFS/NTFS
/dev/sdb2           58445       60801    18932602+  12  Compaq diagnostics

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x767102c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2       60801   488376000    5  Extended
/dev/sdc5               2       60801   488375968+   7  HPFS/NTFS

Disk /dev/sdh: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ddc5cd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf46e8cfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x729e94d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sdk: 1048 MB, 1048576000 bytes
64 heads, 32 sectors/track, 250 cylinders
Units = cylinders of 2048 * 2048 = 4194304 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1         250     1023626    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 60) logical=(0, 5, 28)
Partition 1 has different physical/logical endings:
     phys=(319, 63, 32) logical=(249, 63, 32)
Partition 1 does not start on physical sector boundary.
john@john-desktop:~$ ^C
john@john-desktop:~$

---

### Post by Lazy-buntu on 2010-04-30
More great news! My laptop died!

Thanks HP for that great quality hardware. My laptop almost lived to see the three year mark! The nvidia defect strikes again. Not that it has to do with this post, but anyway...


I'll run the script from the computer I'm trying to fix and post it via live cd.

---

### Post by Lazy-buntu on 2010-04-30
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   307,204,739   307,204,677   7 HPFS/NTFS
/dev/sda2         307,206,144   526,335,999   219,129,856   7 HPFS/NTFS
/dev/sda3         526,337,595 1,295,160,299   768,822,705   7 HPFS/NTFS
/dev/sda4       1,295,160,361 1,465,144,064   169,983,704   5 Extended
/dev/sda5       1,295,160,363 1,448,757,764   153,597,402  83 Linux
/dev/sda6       1,448,757,828 1,465,144,064    16,386,237  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   256,002,047   256,000,000   7 HPFS/NTFS
/dev/sdb2         256,002,048   475,138,047   219,136,000   7 HPFS/NTFS
/dev/sdb3         475,138,048 1,250,258,943   775,120,896   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        22DAEF4ADAEF1935                       ntfs       Windows 7 Pro                 
/dev/sda2        CE5C6E535C6E35FD                       ntfs       File Archive                  
/dev/sda3        7F15B5FF291815DB                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4b441fd7-24ac-4241-818f-f173f9189ede   ext4                                     
/dev/sda6        e412c73e-a2ce-4e4d-a9bc-207654621913   swap       swap                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E43EA6F43EA6BEC4                       ntfs       Extra Space                   
/dev/sdb2        324CACA74CAC6777                       ntfs       File Archive 2                
/dev/sdb3        6084B46884B44278                       ntfs       Data 2                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4b441fd7-24ac-4241-818f-f173f9189ede
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4b441fd7-24ac-4241-818f-f173f9189ede
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4b441fd7-24ac-4241-818f-f173f9189ede
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4b441fd7-24ac-4241-818f-f173f9189ede ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4b441fd7-24ac-4241-818f-f173f9189ede
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4b441fd7-24ac-4241-818f-f173f9189ede ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4b441fd7-24ac-4241-818f-f173f9189ede
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 4b441fd7-24ac-4241-818f-f173f9189ede
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 22daef4adaef1935
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=4b441fd7-24ac-4241-818f-f173f9189ede /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e412c73e-a2ce-4e4d-a9bc-207654621913 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 723.4GB: boot/grub/core.img
 676.3GB: boot/grub/grub.cfg
 723.4GB: boot/initrd.img-2.6.32-21-generic
 723.3GB: boot/vmlinuz-2.6.32-21-generic
 723.4GB: initrd.img
 723.3GB: vmlinuz

```

---

### Post by Lazy-buntu on 2010-04-30
So what does that show?

---

### Post by Lazy-buntu on 2010-04-30
Ideas? Do I install grub to sda5 and if so, how?

---

### Post by oldfred on 2010-04-30
I see no errors or files in the wrong place. You should be able to boot windows from the 750GB drive. 

You do not have grub2 installed but once windows boots ok you should be able to install grub and it will let you boot both.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

While in the LiveCD, open terminal and run:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If errors:
sudo grub-install --recheck /dev/sda

Then:
sudo update-grub

---

### Post by Lazy-buntu on 2010-04-30
The problem is, when I boot, now it just sits there. I was wondering if installing grub again would help me.

I haven't been able to boot into windows since the start of this thread :(

---

### Post by Lazy-buntu on 2010-04-30
Grub is back, so I'm back to my original dilemma. I can boot into Ubuntu, but trying to boot into Windows 7 leaves me with a blinking cursor. :confused:

---

### Post by oldfred on 2010-04-30
What drive are you booting from? The results.txt showed windows in the 750GB drive. Have you tried booting from it? Are you installing grub to sdb or sda?

---

### Post by Lazy-buntu on 2010-04-30
Everything I've been doing is to sda. sdb is strictly data / backups.

The 750GB is my boot drive with windows, 2 data partitions, and an extended (ubuntu and swap)

---

### Post by Lazy-buntu on 2010-04-30
Just seen this on Digg: [http://www.downloadsquad.com/2010/04/29/ubuntu-10-04-hit-by-major-bug-on-release-day/](http://www.downloadsquad.com/2010/04/29/ubuntu-10-04-hit-by-major-bug-on-release-day/)

---

### Post by bcbc on 2010-04-30
> **Lazy-buntu said:**
> Just seen this on Digg: [http://www.downloadsquad.com/2010/04/29/ubuntu-10-04-hit-by-major-bug-on-release-day/](http://www.downloadsquad.com/2010/04/29/ubuntu-10-04-hit-by-major-bug-on-release-day/)

I would agree it's a major mess up (putting it politely). 

So, I am assuming you tried [meierfra's fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")? It has worked for a number of people, but I know you've done 'a lot of stuff' and who knows what state your windows is in.

The way I see it, if you haven't already, you might as well give it a shot.

---

### Post by Lazy-buntu on 2010-04-30
> **bcbc said:**
> I would agree it's a major mess up (putting it politely). 

So, I am assuming you tried [meierfra's fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")? It has worked for a number of people, but I know you've done 'a lot of stuff' and who knows what state your windows is in.

The way I see it, if you haven't already, you might as well give it a shot.

I'll give that a go, thanks! :)

---

### Post by Lazy-buntu on 2010-04-30
> If the sixth screen did not have a "BackupBS" tab, it usually means that the original and backup boot sector are identical, and you are probably suffering from a different problem. But it could also mean that your backup boot sector is corrupted, in which case you will of to use "fixboot" from a Windows CD to repair the boot sector.

After you fixed the Windows boot sector, you might have to update the Grub Menu. For Grub 2 just run

  sudo update-grub



This is what happened to me. I've done the fixboot many times and did the update grub to no avail.

---

### Post by oldfred on 2010-04-30
Grub will only boot a working windows, so if windows did not boot with the windows boot loader in the MBR as shown in the results.txt.

The script does not show the problem that bcbc linked to. But it does no harm to run it.

I think you need to run the full set of windows repairs including reinstalling the windows boot loader fixMBR and make sure windows boots, Then reinstall grub.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by Lazy-buntu on 2010-04-30
> **oldfred said:**
> Grub will only boot a working windows, so if windows did not boot with the windows boot loader in the MBR as shown in the results.txt.

The script does not show the problem that bcbc linked to. But it does no harm to run it.

I think you need to run the full set of windows repairs including reinstalling the windows boot loader fixMBR and make sure windows boots, Then reinstall grub.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

Did everything in there already. Even tried step 4 of: [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I can boot into the CD and the auto repair claims there's no problem.

In command line, in addition to the commands above, I tried:
```
bootsect /nt60 all
```
```
bootsect /nt60 sys
```
and
```
bootsect /nt60 C:
```

---

### Post by oldfred on 2010-04-30
All the bootsect commands are just restoring the boot loader to the MBR. But if you cannot boot with the windows boot loader there still is an issue inside windows which all the other commands should fix.

---

### Post by bcbc on 2010-04-30
> **oldfred said:**
> All the bootsect commands are just restoring the boot loader to the MBR. But if you cannot boot with the windows boot loader there still is an issue inside windows which all the other commands should fix.

According to this [link]("http://neosmart.net/blog/2007/bootsectexe-modifies-the-bootsector-not-the-mbr/"), that's not accurate.

---

### Post by DRAGONPOWER on 2010-04-30
my computer just died, had to reinstall everything, by everything i mean lynx (faster than win7).

so yeah, pretty much lynx killed win7

---

### Post by bcbc on 2010-04-30
> **Lazy-buntu said:**
> Did everything in there already. Even tried step 4 of: [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I can boot into the CD and the auto repair claims there's no problem.

In command line, in addition to the commands above, I tried:
```
bootsect /nt60 all
```
```
bootsect /nt60 sys
```
and
```
bootsect /nt60 C:
```
Did you try steps 3 and 4 from [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Lazy-buntu on 2010-04-30
Yes sir, steps 3 and 4 both failed. Not only that, when I did the auto step it finally wanted to repair something.

Still broke :(

---

### Post by bcbc on 2010-04-30
> **Lazy-buntu said:**
> Yes sir, steps 3 and 4 both failed. Not only that, when I did the auto step it finally wanted to repair something.

Still broke :(

That's not good news. Do 'em again, for fun, and then backup what you can and reinstall.

---

### Post by Sealbhach on 2010-04-30
What about this testdisk procedure? it's worked for some people:

[http://ubuntuforums.org/showthread.php?t=1466824](http://ubuntuforums.org/showthread.php?t=1466824)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

.

---

### Post by ed-koala on 2010-04-30
I know how to fix your original problem, if you areback to that point.

The problem is grub can't "see" windows 7 on the disk, so you need to edit a file and add a manual entry for Win 7.  I'll post in a min the solution once I look up an old thread that has it.

---

### Post by ed-koala on 2010-04-30
Here is the thread to look at.

[http://ubuntuforums.org/showthread.php?t=1453700]("http://ubuntuforums.org/showthread.php?t=1453700")

Post number 5 has the answer.  Let me know if you need any help :)

---

### Post by Lazy-buntu on 2010-04-30
Still no success. Blinking cursor when I try to boot windows 7. Grub is working. I'm able to boot into Ubuntu, but if I select windows 7 I get the blinking cursor.

---

### Post by Lazy-buntu on 2010-04-30
I tried: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

When I update grub I get:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
&#8220;Adding Windows&#8221;
Found memtest86+ image: /boot/memtest86+.bin
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
done

```

---

### Post by DeusExM1 on 2010-04-30
if ubuntu killed win 7 on my pc id be happy. no reason to try to fix it imo.:lolflag:

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> I tried: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

When I update grub I get:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
“Adding Windows”
Found memtest86+ image: /boot/memtest86+.bin
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
done

```

OK, so when you reboot, anything?

.

---

### Post by Lazy-buntu on 2010-04-30
Yeah, I booted into the Windows 7 CD, repaired.

Now Windows 7 doesn't appear in GRUB. I'm going to troubleshoot that now.

---

### Post by Lazy-buntu on 2010-04-30
Rebooted, did sudo update-grub

Windows 7 appeared in the list again.

Tried to boot into Windows 7 and same blinking cursor! WTF

Let me try to boot into the Windows 7 cd again and try the bootrec /fixboot

(again)

---

### Post by Sealbhach on 2010-04-30
> **Lazy-buntu said:**
> Rebooted, did sudo update-grub

Windows 7 appeared in the list again.

Tried to boot into Windows 7 and same blinking cursor! WTF

Let me try to boot into the Windows 7 cd again and try the bootrec /fixboot

(again)

This is starting to look like you won't be able to fix it. Something is going wrong when you pass from grub to the windows bootloader and every time you reinstall grub it just messes up the windows mbr. I dual boot with Windows 7 but I've been using Lucid since early Beta so I avoided that Grub bug that appeared a few days ago. It's best to just wait for an update to fix that Grub problem I think.

.

---

### Post by Lazy-buntu on 2010-04-30
I'm starting to think that's the only solution too. Thanks for the help guys, I guess I'll keep an eye out for an update or post about it elsewhere.

:guitar:

---

### Post by Lazy-buntu on 2010-04-30
Is there a way to completely remove grub without damaging anything?

I was thinking: 

1. Get rid of grub
2. Recover/install mbr using Windows 7 disk
3. Install grub again from live CD?

Edit: is there a way to recover my MBR from a windows 7 image I created using windows 7? I've got an old image, that I'd prefer not to revert to, that I made with Windows 7

---

### Post by Sealbhach on 2010-04-30
I was wondering if it's worth looking into removing Grub2 and going back to the old legacy Grub? it says how to here:

[U]
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

[/U] I'm not sure, with Plymouth and all that, if it's feasible, but it's another possibility.

.

---

### Post by oldfred on 2010-05-01
I do not recommend it but some have used easyBCD (from Neosmart) and it has worked. I think they had to use the newest or beta to get it to work.

---

### Post by Lazy-buntu on 2010-05-01
Okay, I'm back on Grub 1.5

I'm going to find out how to add windows 7 to the boot list and hope for the best.

---

### Post by Lazy-buntu on 2010-05-01
I am a tad more proficient in Grub 1.5, not much more, but here's my menu.lst:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4b441fd7-24ac-4241-818f-f173f9189ede ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4b441fd7-24ac-4241-818f-f173f9189ede

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Windows 7 Pro
root		(hd0,0)
makeactive
chainloader	+1

title		Ubuntu 10.04 LTS
uuid		4b441fd7-24ac-4241-818f-f173f9189ede
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=4b441fd7-24ac-4241-818f-f173f9189ede ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS (recovery mode)
uuid		4b441fd7-24ac-4241-818f-f173f9189ede
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=4b441fd7-24ac-4241-818f-f173f9189ede ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

#title		Chainload into GRUB 2
#root		4b441fd7-24ac-4241-818f-f173f9189ede
#kernel		/boot/grub/core.img

title		memtest86+
uuid		4b441fd7-24ac-4241-818f-f173f9189ede
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I'm going to try and boot into Windows, but I'm not holding my breath.

---

### Post by TimCereja on 2010-05-01
Looks to have done the exact same thing to my system. I had been dual-booting Ubuntu 9.10 and Windows 7 x64 with no problem, but after upgrading Ubuntu to the new 10.04, selecting Windows 7 from Grub just gives a blank screen. I've also been trying all kinds of recovery without any success. Hopefully they'll release something to fix this ...

---

### Post by cariboo on 2010-05-01
I haven't read the whole thread, but has anyone tried running:

```
sudo update-grub
```

to redetect the os's?

---

### Post by TimCereja on 2010-05-01
[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

Check out the story. It seems to be well documented by now that a major bug in the release of Ubuntu 10.04 does not allow a computer to boot with any OS other than Ubuntu 10.04, whether it be Windows or a different Ubuntu.

---

### Post by arophous on 2010-05-01
This does seem to be a strange problem. I am wondering whether its actually a problem with a corrupt windows 7 install rather than the boot managers.

---

### Post by Nidwow on 2010-05-01
I have not try 10.04 on my Windows 7 PC yet but I tried with Windows XP PC, same thing Windows XP was not on the menu list. :confused:

Not sure if bug TimCereia is talking about effect Windows XP as well.

---

### Post by adm1968 on 2010-05-01
[FONT="Georgia"]I've read this entire thread, post by post, since my Ubuntu 10.04 also killed my Win 7 installation

I have a very similar setup to that of Lazy-Buntu
Will wait to see if I can find an answer somewhere else, but this definitely sounds like a bug in Lucid

BTW, I've never had this problem with any earlier versions of Ubuntu[/FONT]

---

### Post by Sealbhach on 2010-05-01
> **Lazy-buntu said:**
> I'm going to try and boot into Windows, but I'm not holding my breath.

I wonder what happened?

.

---

### Post by Lazy-buntu on 2010-05-01
The blinking cursor made another appearance. :(

---

### Post by Lazy-buntu on 2010-05-01
> **cariboo907 said:**
> I haven't read the whole thread, but has anyone tried running:

```
sudo update-grub
```

to redetect the os's?

If I do sudo update-grub on grub 1.5, Windows is not detected. When I had Grub2, Windows was detected, but I was faced with the same problem.

---

### Post by Lazy-buntu on 2010-05-01
Still no luck. Flashed my BIOS out of a wild hope that that may help.

I'm going to boot the Windows 7 CD again and see if I can make progress.

---

### Post by Sealbhach on 2010-05-01
I really admire your persistence!

.

---

### Post by Lazy-buntu on 2010-05-01
>  I really admire your persistence! 

I'm determined to have my cake and eat it to. I'm on the verge of scrapping everything, reinstalling windows, and send Ubuntu to the dungeon (a.k.a., a virtual box). I still have hope that I can fix this problem though! I don't know what to do next now.

I've tried, ```
sudo update-grub
``` I've tried every step at: [http://webcache.googleusercontent.com/search?q=cache:_iJbIzb4xcgJ:neosmart.net/wiki/display/EBCD/Recovering%2Bthe%2BVista%2BBootloader%2Bfrom%2Bthe%2BDVD+http://neosmart.net/wiki/display/EBCD/Recovering%2Bthe%2BVista%2BBootloader%2Bfrom%2Bthe%2BDVD&cd=1&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:_iJbIzb4xcgJ:neosmart.net/wiki/display/EBCD/Recovering%2Bthe%2BVista%2BBootloader%2Bfrom%2Bthe%2BDVD+http://neosmart.net/wiki/display/EBCD/Recovering%2Bthe%2BVista%2BBootloader%2Bfrom%2Bthe%2BDVD&cd=1&hl=en&ct=clnk&gl=us)

I've tried the testdisk method: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I've tried all sorts of things from: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I've tried: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

I've tried going from Grub2 to Grub 1.5, I've tried pretty much everything in SuperGrubDisk, I've updated my BIOS, I've done two fresh installs of Ubuntu, I've tried these from the Windows 7 cd:
```
chkdsk /r
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

bootsect.exe /nt60 C:
bootsect.exe /nt60 ALL /force
bootsect.exe /nt60 SYS
```

I'm not sure if I've tried: bootsect /nt60 SYS /mbr
So let my CD back up and give that a go.

---

### Post by kooia on 2010-05-02
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by sixthwheel on 2010-05-02
> I'm on the verge of scrapping everything, reinstalling windows, and send  Ubuntu to the dungeon (a.k.a., a virtual box).

How bout just scrapping Lucid for now, and re-installing Karmic, untill this bug has been fixed.

Canonical knew about this problem in the RC stage, yet they still went ahead and released the LTS to make the self imposed deadline.

Lucid may look better then Karmic, but IMHO I don't see much improvement.

---

### Post by Lazy-buntu on 2010-05-03
I went all the way back to Jaunty. Jaunty was my favorite release (from an ease of installation standpoint - install printer in 4 clicks, etc.).

The problem is, I have to do a fresh install of Windows 7...even though my data is still there. I have tried everything.

Just recently I ghosted my partition, did a partial install to see if I could grab the new MBR. No dice. I did a fully fresh install and saved the MBR using a utility on another live cd. Went to put the old partition back on there plus the restore MBR. No boot.

The weird thing now is Windows 7 doesn't mount the other NTFS partitions on the drive. It sees them as healthy partitions, but doesn't assign them a letter or even say they're NTFS...anyway, let me finish my install of Jaunty.

---

### Post by alzie on 2010-05-03
I read through quickly.  

I found a link to repair MBR for win7,  then I saw you had tried similar commands.  I don't know if it was a typo, but you wrote you had tried ```
bootsect.exe /nt60 C:
```
the command I found was 
```
bootsect /nt60 C:\
```
note the "\" after C: and that is is bootsect not bootsect.exe
I hope this is a help,  I know the frustration of MBR meltdown :(

link: [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by Lazy-buntu on 2010-05-03
Meanwhile, does anyone know how to get the most up to date firefox working on 9.04?

I install firefox 3.5 from synaptic and the related files, but 3.019 is all that launches.

---

### Post by Sealbhach on 2010-05-03
> **Lazy-buntu said:**
> Meanwhile, does anyone know how to get the most up to date firefox working on 9.04?

I install firefox 3.5 from synaptic and the related files, but 3.019 is all that launches.

Install Ubuntu Tweak and add the Mozilla PPA using that. Jaunty was good alright, a solid distro.

.

---

### Post by TimCereja on 2010-05-04
Will Ubuntu be releasing something to fix this bug? I'm really putting off formatting the HD and reinstalling Windows 7 with the hope that an update will correct things.

---


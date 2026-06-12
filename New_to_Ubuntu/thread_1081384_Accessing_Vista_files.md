---
title: "Accessing Vista files"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by suitedaces on 2009-02-26
Apologies if you are sick of answering this, but I can't find a solution that works. Put simply, I'm wondering how to configure my ubuntu 8.10 to read the files I had saved on vista? (now dual booting)

---

### Post by SuperSonic4 on 2009-02-26
It should be in Places as XX GB drive where XX is the vista partition's size. It should ask for your password and then you're in

---

### Post by suitedaces on 2009-02-26
My places are computer, CD/DVD Creator, HP Recovery (a 10 gig partition to reinstall vista if it screws up on me) and CD-RW DVD +RW Drive

---

### Post by THEDARKNESSHASCOME on 2009-02-26
> **SuperSonic4 said:**
> It should be in Places as XX GB drive where XX is the vista partition's size. It should ask for your password and then you're in

and if it is not located in the drop menu you can look up the drives on your computer and simply force mount the partition through terminal

---

### Post by suitedaces on 2009-02-26
> **THEDARKNESSHASCOME said:**
> and if it is not located in the drop menu you can look up the drives on your computer and simply force mount the partition through terminal

Thanks, but I wouldn't know where to begin with that.

---

### Post by THEDARKNESSHASCOME on 2009-02-26
> **suitedaces said:**
> Thanks, but I wouldn't know where to begin with that.


Here is how to get partition list

sudo fdisk -l

Here is how to force mount

sudo mount /dev/(yourdevice) -o force

---

### Post by THEDARKNESSHASCOME on 2009-02-26
i rarely come on as you can see ive logged in maybe 10 times since 2007 so i suggest you try now...

---

### Post by suitedaces on 2009-02-26
Can you identify my vista drive from this? Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ff16d35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13087   105121296    7  HPFS/NTFS
/dev/sda2           13088       14593    12096945    7  HPFS/NTFS



And what do I put into yourdevice?

---

### Post by suitedaces on 2009-02-26
pj@pj-laptop:~$ sudo mount /dev/sda2 -o force
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab

---

### Post by sasquatch74 on 2009-02-26
Have you tired installing ntfs-config?
It allows you to enable reading and writing to windows partitions.
Search for it in Synaptic or
in a terminal:
```
sudo apt-get install ntfs-config
```
Once installed find it under Applications>System Tools>NTFS Configuration Tool.
Then your windows partition should be accessible in Places (you may have to follow the advise above to get it to show up)

---

### Post by suitedaces on 2009-02-26
Done. The only thing it's giving me is HP Recovery.

---

### Post by thtrgremlin on 2009-02-26
You are missing a place to mount the file system. Also, while this is debatable, I would NOT use the "-o force" option unless you know how to recover from when things go wrong. there is a reason why it is called force. On a computer, when it asks if you want to force something, that specifically means "not recommended", but things should still work fine without the force option. The computer probably just isn't setup to automatically mount the drive.

1. Need a place to mount it. Start by making a place to put it:

```
sudo mkdir /media/vista
```

You can actually call it vista, or whatever you want. This is just personal preference. Technically, the folder could be anywhere, but we put it in media for the sake of organization. Also, mounted stuff in /media/ usually show up automatically on the desktop and in your places menu.

2. Gather the info from fdisk

> 255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ff16d35

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13087 105121296 7 HPFS/NTFS
/dev/sda2 13088 14593 12096945 7 HPFS/NTFS

So your hard drive is /dev/sda. notice that the first one (/dev/sda1) has a much larger number of "blocks", this is basically the size. There is also a * under "boot". This is your vista install. sda2 is your recovrey partition.

so mount can only be used by root, so we need to use sudo. typing in 'man mount' gives you instructions on how to use mount, but i'll give you the short version. the first option is what you want to mount. if it is not a normal file system (like ext3), we use the '-t' option to tell it what 'type' it is, in this case ntfs. Lastly, we specifiy where we want to mount it, in this case, /media/vista. So here is out code.

```
sudo mount /dev/sda1 -t ntfs /media/vista
```

Just so not to worry, adding the '-o force' option is unlikely to harm anything alone, but it does require 'mount' to make some changes to the disk. The most common reason to need the '-o force' option is when windows didn't shut down properly, and if it was in the middle of writing files, windows would have fixed any problems the nest time it started up. By default, 'mount' checks to see if a disk was improperly shut down, so if it sees windows was planning on fixing something, by default it will NOT mount it so you don't change anything before windows has had a chance to look at it.

Also, remember that message where it said:<quote>mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab</quote>This is because when you don't specify where to mount it, there is a place where it automatically checks for a mount point, and when there was no entry for /dev/sda1, it reported he error. If you add an entry to fstab, then it will try to mount it every startup. If at startup it sees an error and does not mount it, then if you want to over ride its warning, you can just use "sudo mount /dev/sda1 -o force", and it will mount "normally". Another good option to remember is "sudo mount -a" where it will look in /etc/fstab and try to mount everything that isn't already mounted.

If you are feeling adventurous, this is how you add an entry to fstab:
```
sudo gedit /etc/fstab
```

make the window wide enough so each entry has its own line. To note, any line that begins with '#' is skipped. Everything else is an "entry". You may notice in there not everything is a hard drive, but don't worry about that.

The important thing for you is what is at the top, telling yo how to add an entry (sort of):
> 
<file system> <mount point> <type> <options> <dump> <pass>

Think of these as:
File system) What you are mounting, in this case: /dev/sda1
mount point) Where you want to mount it, in this case: /media/vista
type) this is the file system type or driver to use, in this case: ntfs
options) These are not the options given to mount, they are special for fstab. You are going to want to use: defaults. However, one other possibility is 'ro' which would mount it as 'read-only', so nothing could be changed. Remember, you need 'sudo' to change system stuff, and this would protect your entire vista install from being tampered with, if you are feeling so paranoid. Honestly, if you are interested in such things, do a little more thorough research regarding how to mount file systems.
dump/pass) Not doing any thing fancy or making this disk an important part of the system, you want to use 0 0.

So here is the line you would add:
```
/dev/sda1 /media/vista ntfs defaults 0 0
```

Good luck!

---

### Post by thtrgremlin on 2009-02-26
> Done. The only thing it's giving me is HP Recovery.

As mentioned in my longer post, in the fdisk -l output, there was a disk with a large number of blocks, and another with a smaller number. The smaller one is your recovery disk used by tools from HP that came with the computer, the other is where your Vista system and files are.

---

### Post by suitedaces on 2009-02-26
> **thtrgremlin said:**
> You are missing a place to mount the file system. Also, while this is debatable, I would NOT use the "-o force" option unless you know how to recover from when things go wrong. there is a reason why it is called force. On a computer, when it asks if you want to force something, that specifically means "not recommended", but things should still work fine without the force option. The computer probably just isn't setup to automatically mount the drive.

1. Need a place to mount it. Start by making a place to put it:.............

After those 3 steps, what should the outcome be? I have done all 3 and rebooted, no improvement.

---

### Post by suitedaces on 2009-02-27
Any other ideas guys? Much appreciated.

---

### Post by yther on 2009-02-27
Just curious here, you said you are dual-booting.  Yet "fdisk -l" only shows one drive with two volumes, both of them NTFS.  Where is your Ubuntu installed, or did you just clip that part of the list?

The procedure thtrgremlin posted seemed to cover everything.  Can you paste what happens when you do this?

```
sudo mount -t ntfs /dev/sda1 /media/vista
```

If it doesn't print anything after you do that, the operation was successful (or so it thinks) and "ls /media/vista" should return a large list of stuff.  No need to paste all that in here, it's just so you can tell.  :)

---

### Post by suitedaces on 2009-02-27
It's wubi installed, does that change things?

---

### Post by suitedaces on 2009-02-27
> **yther said:**
> Just curious here, you said you are dual-booting.  Yet "fdisk -l" only shows one drive with two volumes, both of them NTFS.  Where is your Ubuntu installed, or did you just clip that part of the list?

The procedure thtrgremlin posted seemed to cover everything.  Can you paste what happens when you do this?

```
sudo mount -t ntfs /dev/sda1 /media/vista
```

If it doesn't print anything after you do that, the operation was successful (or so it thinks) and "ls /media/vista" should return a large list of stuff.  No need to paste all that in here, it's just so you can tell.  :) [B]Is this what you mean? autoexec.bat            Mp3 Output         SwSetup
boot                    MSDOS.SYS          System.sav
bootmgr                 MSOCache           System Volume Information
config.sys              pagefile.sys       ubuntu
CVS                     Poker Application  ubuntu-backup
Documents and Settings  ProgramData        Users
hiberfil.sys            Program Files      WINDOWS
HP                      $RECYCLE.BIN       wubildr
IO.SYS                  Restoration        wubildr.mbr
IPH.PH                  resycled[/B]


I get that, yet still can't access the files.

---

### Post by Mark Phelps on 2009-02-27
Having a multi-boot machine (Vista and other OSs), I would suggest the following:
1) Use ntfs-3g instead of ntfs in the mount command. May need to install the ntfs-3g package if it's not already there.
2) Mount the Vista partition read-only.  Very important!! If you mount it read/write, you run the risk of file system corruption.  Should this happen, you will then have to boot from your Vista DVD and run a Startup Repair to get Vista working again.  You DO have a Vista DVD, right?

---

### Post by suitedaces on 2009-02-27
> **Mark Phelps said:**
> Having a multi-boot machine (Vista and other OSs), I would suggest the following:
1) Use ntfs-3g instead of ntfs in the mount command. May need to install the ntfs-3g package if it's not already there.
2) Mount the Vista partition read-only.  Very important!! If you mount it read/write, you run the risk of file system corruption.  Should this happen, you will then have to boot from your Vista DVD and run a Startup Repair to get Vista working again.  You DO have a Vista DVD, right?

pj@pj-laptop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/vista
fuse: mount failed: Device or resource busy

HP didn't supply a DVD, just a recovery partition.

---

### Post by yther on 2009-02-27
Yes, I think the fact that you installed with WUBI *does* change things.  Here's what WUBI does, as I understand it.

It makes a giant file on your drive, *inside* your Windows drive.  Then when you boot up, you (should) get an option to start Ubuntu.  When you do that, it performs some trickery to load the file into memory as if it were a hard drive.  (Here's [an article]("http://en.wikipedia.org/wiki/Wubi_(installer)") with a bit more info.)  I'm not sure what effect this will have on your trying to access your Windows files from inside your WUBI system.

As we can see above, you can at least *see* the files.  What do you mean when you say you can't access them?  Technically speaking, you have already "accessed" the file system, but I'm guessing you want to read those files.  You should be able to do that now, using Nautilus or whatever you like.  To make the change stick, you'll need to change your **/etc/fstab** as suggested above.  I'm not sure if it works the same way on a WUBI system, because I've never done that.

---

### Post by suitedaces on 2009-02-27
"nautilus action configuration"?

---

### Post by suitedaces on 2009-02-27
D'oh. Right, thanks for your help everybody, and sorry for wasting time. They were there the whole time, under file system/host/ etc.

---

### Post by yther on 2009-02-27
Hey, no worries!  I learned something, too.  ;)

---

### Post by suitedaces on 2009-02-27
Part of me wants to delete this to save embarassment, but hopefully it'll turn up in a search to help someone with the same problem.

---


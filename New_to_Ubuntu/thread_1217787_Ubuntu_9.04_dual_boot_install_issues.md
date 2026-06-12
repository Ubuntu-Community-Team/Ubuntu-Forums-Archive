---
title: "Ubuntu 9.04 dual boot install issues"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Binary.tobis on 2009-07-19
I just re-installed windows, and partitioned most of my hard drive for it. I left about 20% for ubuntu, and I tried installing 9.04 from the cd. When I start up my computer, then start the ubuntu installation, it goes through the loading bar then goes to a "Can not display" screen on my monitor. Is there a way to fix this and install ubuntu? Thanks in advance!

---

### Post by laffinet on 2009-07-19
You might want to try the alternate install CD.

Also considering changing the thread title, your problem is not dual boot, but a display issue. Consider something like "can not display when trying to install" or so.

---

### Post by Binary.tobis on 2009-07-20
I tried it a few more times and Found a "Safe Graphics Mode" option. Thanks for the reply!

---

### Post by Binary.tobis on 2009-07-20
Can anyone tell me how to edit that boot menu when I start my computer? Right now it lists it like:

Ubuntu
Ubuntu (safe)
some other ubuntu
Other OS:
Windows

And I want it to look like:

Windows
Ubuntu
Whatever

Is that possible? Thanks for any help!

---

### Post by 4Orbs on 2009-07-20
Use Synaptic Package Mgr to install the program Startup Manager, then you can change boot order and even switch backgrounds on the Grub screen.

EDIT: Well, it doesn't actually change the boot order, but you can select either os option as the default bootup, and you can change the countdown timer, too.

---

### Post by syrrus on 2009-07-20
I'm a total Linux noob and wanted to install Ubuntu on an extra HD I had and try it out. I swapped out the Drive windowz was on and  installed Ubuntu on it. Then realised that I'd much rather have a dual boot (Windows and Ubuntu), than swapping out HDs when I wanted to mess around with Linux. What is the best way to go about this. I've read about manually changing the GRUB menu list, but that hasn't worked for me. I'm hoping that if I post fdisk info that someone might be able to help me out to manually get this done. If I need to post more info, let me know....

Cheers,

Here it is: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x008a008a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdef5def5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       16708   103490730    f  W95 Ext'd (LBA)
/dev/sdb3           16709       60801   354177022+   7  HPFS/NTFS
/dev/sdb5            3825       16708   103490698+   7  HPFS/NTFS

---

### Post by laffinet on 2009-07-20
The easiest option is to have both drives installed while installing Ubuntu, that way the installation process takes care of installing and setting up GRUB.
So assuming that you probably haven't done much customising I'd suggest you install both drives and reinstall Ubuntu (just be careful when you get to the partitioning step to choose the right partition/hard drive so you don't erase your windows installation).

If you don't want to reinstall things get a bit more complicated, since you need to install GRUB to your primary boot drive. For that I would suggest using "super grub disk" (google it).

---

### Post by syrrus on 2009-07-20
Part of me wants to do it the hard way and not re-install, but I know that's probably a dangerous idea, given my current knowledge. Advice noted. I'll let you know how it went (re-install)....now I can go back to sleep....I was dreaming about fixing the problem. lol Cheers Laffinet.

---

### Post by presence1960 on 2009-07-20
don't remove a perfectly good OS! make sure your BIOS has your 120 GB drive set to boot first in the hard disk boot order. Then do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.you should get (hd0,0) according to your fdisk -l table you posted.
5. Type "root (hd0,0)" 
6. Type "setup (hd0)", to install GRUB to MBR, 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When you reboot if GRUB doesn't have a windows entry or a windows entry that does not work, boot into Ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
Scroll to the bottom and make your windows entry look like this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows <your version>
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

That is a lot less work than installing an OS. Why would you want to remove a perfectly good OS and reinstall it when in 5 minutes you can get your system running?

This way or with super grub disk is the easy way, reinstalling is the hard way!

---

### Post by syrrus on 2009-07-21
Damn, I wish I'd got this message before I'd re-installed the "perfectly good OS." :( Oh well, I"ll make note of this advice, presence1960. However it now works fine and will dual boot properly. I'm glad to both of you for your responses.

Cheers,
S.

---


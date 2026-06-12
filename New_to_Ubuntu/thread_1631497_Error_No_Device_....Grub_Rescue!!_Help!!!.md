---
title: "Error: No Device ....Grub Rescue?!?! Help!!!"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by sperman13 on 2010-11-26
Hey guys, 

Very new to the whole linux system and I've had my wonderful ubuntu for o month and now my first problem :( 

So  first some background I guess: 

I installed Ubuntu on my LG Netbook x110 through WUBI and things were going great. But yesterday the update manager came up and told me to install a bunch of updates which I always do. The only thing out of the ordinary was that one of the updates had to do with the grub loader and it asked me if I wanted to proceed..big mistkae. So it installed everything and told me to restart the computer to make the changes effective. So when I restart the computer I'm greeted by this message: 

Error: No such device: af9251f2-3174-48c1-a75f-b06bd29962bf
grub rescue> 


Help?!

---

### Post by bcbc on 2010-11-26
You need to reinstall the windows bootloader.

That's an unfortunately misleading grub 'bug' that has been around since April this year. It has led you to install grub to the drive master boot record, which should contain Windows for wubi installs.

To fix, boot from a Windows repair disc/usb and run "fixmbr" for XP, or "bootrec.exe /fixmbr" for Vista/7.

If you can't do this, you can also boot an Ubuntu cd/usb in live mode (Try without installing) and use lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Ignore the huge warnings you get - they relate to using lilo to boot a linux system.

---

### Post by sperman13 on 2010-11-29
I am currently in the Ubuntu Live USB trial mode. I did the lilo commands and I thought everything had worked but when I restarted I got to the page where I can chose to either boot into xp or ubuntu and if i choose ubuntu it shows a screen for a split second and restarts :S what to do!

---

### Post by zeiz on 2010-11-29
+1

Using Ubuntu since 6. Though it's the best in the Linux world.
Still believe it is when you know what you are doing.

My daughter ruined the system I installed for her in other city.
She complains now that after trying something with Skype (no updates, she said) the computer hanged. After forced reboot she got something like the thread starter's:
```
Error: No such device: af9251f2-3174-48c1-a75f-b06bd29962bf (different hash of course)
**grub rescue>**

```
I tried to help over the phone but nothing works: the only command accepted was **ls** and only once. Trying **ls (hd0,3)** returns:
**"unknown file system"** (same respond for other partitions).
Install CD fires Ubuntu Live but it sees only Windows Xp partition and one more fat32 Storage partition. Ubuntu (10.4 LTS) partition has gone!

I didn't have much time for googling but it's clear that not too much info on that "stuff". The most valuable I got was : ...you don't want to see that"

Is somebody around here who really knows what that error is about and how to fix it? I meant except reinstall?

If there is a prompt there must be at least a list of commands for it or at least **help** must help (makes sense). But: "unknown command"
During short time I googled out a bunch of same complains and none of answers that help.
Does somebody really knows what to do with this "prompt" or at least how to know what commands it accepts?

Thanks a lot in advance.

---

### Post by drs305 on 2010-11-29
Ok, some brief background (simplified, I won't cover each step along the boot process, some of which you can't control anyway): When you install *lilo* and run the commands, you are rewriting the MBR. That is all you are doing (unless you fully install lilo, which we don't do with the given commands). So now the MBR is instructed to pass control over to files in the partition with the boot flag (Windows).

This should allow you to boot Windows. Once you get to the Windows menu, it's going to offer Windows or Ubuntu. This is still a Windows function (boot.ini I believe, at least on the earlier Windows). When you select Ubuntu, it finally passes control to Grub (on Wubi).

If you get to this point and get a "no such device" message, try highlighting the first entry and pressing "e". This should open the menuentry for editing.

Use the cursor keys to move to the start of the "search" line. Use the DEL key to remove the entire line.

On the next line, part of the commands include "root=/dev/sdXY". XY should be your Windows partition, normally sda1 or sda2. If it points to the correct partition, press CTRL-x and it should begin to boot Ubuntu.

If it does, once you are on the Desktop open a terminal and run "sudo update-grub".

---

### Post by sperman13 on 2010-11-29
Well I installed the lilo and i get to the windows boot menu where I pick ubuntu and it doenst load the grub insteadi t shows a black screen and it says No Wubildr or something like that:( What now?

---

### Post by drs305 on 2010-11-29
> **sperman13 said:**
> Well I installed the lilo and i get to the windows boot menu where I pick ubuntu and it doenst load the grub insteadi t shows a black screen and it says No Wubildr or something like that:( What now?

You can boot into Windows to find the wubildr file; I am not a wubi expert so I don't know how the file disappeared in the first place. It should be in C:\ubuntu\winboot\wubildr. Copy it to C:\ and try to boot again.

---

### Post by sperman13 on 2010-11-30
gah wuibldr is already in C:/ ive tried adding different files like the wuibldr.cfg and nothing. I think I'll just have to reinstall the ubuntu :( There goes all my files.

---

### Post by bcbc on 2010-11-30
> **sperman13 said:**
> gah wuibldr is already in C:/ ive tried adding different files like the wuibldr.cfg and nothing. I think I'll just have to reinstall the ubuntu :( There goes all my files.

Use [ext2read]("http://ext2read.blogspot.com/") to pull your data off the root.disk (point it at c:\ubuntu\disks\root.disk)
Before uninstalling - this permanently deletes the root.disk

---


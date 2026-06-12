---
title: "How to remove GRUB from NTFS sda1."
date: 2010-11-12
forum: New to Ubuntu
---

### Post by DM was on fire! on 2010-11-12
So, I've officially decided I probably will NOT be experimenting with Linux anymore. It's getting me into too much trouble, and this last bit of fun almost gave me a heart attack (then I mounted sda1 and saw my files were atleast still there). 
So I was putting Ubuntu on my thumb drive, and I had expected it to have put the boot loader on sdb1. Nope. It went on sda1. Now whenever I turn my computer on, GRUB rescue is like "uhh where's your kernel. can't find your kernel man."
Thankfully, I have another Linux drive I'm using right now for my computing needs; and even more thankfully, the files are still there and I can work from them.
How do I fix this? Is there a way to fix this? I read somewhere that if I put my XP disc in (but I have to see if it's a real XP disc or if it's one of those "we'll take your computer back to the way it was when you bought it, including the 100 hours of dial-up no one ever uses" discs since my computer is a Dell -- if not, we've got an XP disc I can use), go into the recovery console and type **fixmbr** or **fdisk /mbr** (which scares me even more with the words FDISK in it) that would solve the issue, but I'd rather go away from the XP disc and work on Ubuntu.
Is there anyway how?

---

### Post by Zzl1xndd on 2010-11-12
You will want to use the Windows disk and use the fixmbr method. Unfortunately there is no way (that I know of) to replace the windows Boot loader from Linux.

---

### Post by Amente on 2010-11-12
So you want to remove grub from your hard disk partition sda1,here is what you can do
1. boot from a your linux drive ,(I assume it is ubuntu if not use a live CD)
2.open terminal,and type this
```

sudo mkdir /mnt/tmp # or any temporary directory
sudo mount /dev/sda1 /mnt/tmp
sudo for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/tmp
root@yourpcname:/#apt-get purge grub grub-pc grub-common

```
This will completely remove grub from sda1 :)

---

### Post by Zzl1xndd on 2010-11-12
> **Amente said:**
> So you want to remove grub from your hard disk partition sda1,here is what you can do
1. boot from a your linux drive ,(I assume it is ubuntu if not use a live CD)
2.open terminal,and type this
```

sudo mkdir /mnt/tmp # or any temporary directory
sudo mount /dev/sda1 /mnt/tmp
sudo for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/tmp
root@yourpcname:/#apt-get purge grub grub-pc grub-common

```
This will completely remove grub from sda1 :)

I could be wrong but won't this also leave him/her without a Bootloader?

---

### Post by coffeecat on 2010-11-12
> **tweakedenigma said:**
> Unfortunately there is no way (that I know of) to replace the windows Boot loader from Linux.

Fortunately, there is. :)

@DM was on fire!, have a look here:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by Zzl1xndd on 2010-11-12
> **coffeecat said:**
> Fortunately, there is. :)

@DM was on fire!, have a look here:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

Awesome, good to know (Thanks CoffeeCat).

---

### Post by coffeecat on 2010-11-12
Or if the OP wants to use the XP install disc (it has to be a Microsoft one - not an OEM or Dell) and use the repair console, the fixboot - not fixmbr - command seems to be the one needed here. More on this page:

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by DM was on fire! on 2010-11-12
> **tweakedenigma said:**
> I could be wrong but won't this also leave him/her without a Bootloader?

Thank you for not automatically assuming I am a he. lol

coffeecat, does that link apply if my sda1 is not partitioned? I noticed the step there where it says to edit boot.ini and change the partition number. It already says that. I looked at my boot.ini first to see if that was editable but it's thew same thing. 
I do appreciate that link; but I think at the moment it's too much for me to comprehend. lol

---

### Post by coffeecat on 2010-11-12
> **DM was on fire! said:**
> coffeecat, does that link apply if my sda1 is not partitioned? 

I don't quite follow you. sda1 is the first partition on the first hard drive, sda. If sda had no partitions, there would be no sda1 - if you see what I mean.

From your first post I assumed that grub had overwritten the Windows boot sector in your Windows C: partition, again making an assumption that your C: drive was on the sda1 partition. I have a bad habit of making assumptions :wink: so let's see what is really going on. Have a look here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Run that script either from a live CD or from your hard drive Ubuntu install - not from a live USB which confuses the device descriptors for us. Then post the contents of RESULTS.txt in code tags as described there.

One question: do you have a Microsoft XP installation CD? Your first post suggests you do. Because, depending on what the bootscript shows us, it might be simpler to run fixboot from the repair console of the XP disc.

---

### Post by oldfred on 2010-11-12
The author of the boot script (meierfra.) and coffeecat's link to using lilo was posting so many times he created a web page with many fixes.

So many times when installing to an external device, grub would install to the internal drive and this is a fix for both MBRs:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

---

### Post by DM was on fire! on 2010-11-12
> **coffeecat said:**
> One question: do you have a Microsoft XP installation CD? Your first post suggests you do. Because, depending on what the bootscript shows us, it might be simpler to run fixboot from the repair console of the XP disc.

I do have an XP installation CD. It came with my father's computer. 

I'm not entirely sure how I ended up with my hard drive being sda1. But it has no other operating systems on it, and when I went to install Ubuntu the other night and it showed me the graph for sda1, it only showed XP. Not anything else. It's confusing to me too, so no worries. lol

I think it would probably just end up being best if I ran fixboot on a CD. But will I risk losing any parts of my system?

ETA - Oh.
This is the screen I get if I don't boot with my thumb drive: [http://i56.tinypic.com/wlen3p.jpg](http://i56.tinypic.com/wlen3p.jpg)

---

### Post by uRock on 2010-11-12
You can use an ubuntu LiveCD to install the Lilo boot manager, which can boot Windows seemlessly without you ever knowing it was there.

Here's how;> **presence1960 said:**
> You can repair the MBR to a windows MBR from ubuntu or the ubuntu live CD. Install lilo by running in terminal ```
sudo apt-get install lilo
```Ignore the warning and next run in terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your disk/device, i.e. sda, sdb,sdc, etc

---

### Post by coffeecat on 2010-11-12
> **DM was on fire! said:**
> ETA - Oh.
This is the screen I get if I don't boot with my thumb drive: [http://i56.tinypic.com/wlen3p.jpg](http://i56.tinypic.com/wlen3p.jpg)

That's grub in the mbr looking for a partition that it can't find. The long string of goobledegook is the UUID of the partition that's gone walkabout.

> **DM was on fire! said:**
> I think it would probably just end up being best if I ran fixboot on a CD. But will I risk losing any parts of my system?There's two possible issues and fixes here. If you have only XP on that drive and want to restore the Windows mbr then you need fix**mbr** from the repair console of the XP disc.

If by chance grub has installed itself to the partition boot sector of the Windows partition, then you need to run fix**boot** to repair the Windows boot files that are inside the partition. The mbr is the first 400 bytes or so of the disc, long before any of the partitions start.

I sympathise with the problems you have with a thumb drive. I was trying to install Ubuntu to a thumb drive yesterday using another thumb drive with the live installer and I was nearly driven mad by sda changing into sdb and sdc into goodness knows what. Grub went into the oddest places. :( And I've been using Linux for over 5 years.

Forget what I said about not using the live USB. Boot up with the live USB and run the bootscript and post it. It will muddle the device descriptors, but we can sort that out well enough. Then we can see exactly what has been installed where and what you need to do.

---

### Post by DM was on fire! on 2010-11-12
The Live USB is dead. I actually reformatted it because I couldn't get it to load. Now I'm seeing that wasn't such a smart move.

I'd install LILO, but the problem is that computer is offline, and plus I don't have Ubuntu on there, or as I said, my thumb drive.

> There's two possible issues and fixes here. If you have only XP on that drive and want to restore the Windows mbr then you need fixmbr from the repair console of the XP disc.

If by chance grub has installed itself to the partition boot sector of the Windows partition, then you need to run fixboot to repair the Windows boot files that are inside the partition. The mbr is the first 400 bytes or so of the disc, long before any of the partitions start.

Would it hurt if I ran both? I would probably restart after the first command to see if it worked, and then if it didn't work try fixboot. I'd be afraid what running them in succession would do.

I appreciate all your help everybody. :)

---

### Post by coffeecat on 2010-11-12
> **DM was on fire! said:**
> Would it hurt if I ran both? I would probably restart after the first command to see if it worked, and then if it didn't work try fixboot. I'd be afraid what running them in succession would do.

First, I may have introduced a red-herring by referring to fixboot. I was going by your comment in your first post about the grub bootloader going on sda1. It's not uncommon for someone to make a mistake with the installer and install grub to the partition boot sector of a partition. Re-reading your posts I think the situation is simpler and you just have to repair the mbr. I apologise if I complicated things unnecessarily.

It won't hurt to run both but if you are sure that there is only Windows on sda, it might be an idea to  run fixmbr from the XP disc only. If that sorts things, then well and good. If not then reboot the XP disc and run fixboot.

---

### Post by DM was on fire! on 2010-11-12
It's fine. I was probably no help and was making it complicated myself.
Even if it's Windows, that computer is my baby and I'm worried about killing it. 
I'll try fixmbr once I can muster the courage to boot from the CD and do it (the Windows install CDs always scare me with that lifeless blue screen). Thank you for your help. :)

---

### Post by coffeecat on 2010-11-12
> **DM was on fire! said:**
> I'll try fixmbr once I can muster the courage to boot from the CD and do it (the Windows install CDs always scare me with that lifeless blue screen)

The Vista and Windows 7 ones are at least a bit prettier. Just a bit!

Hopefully, fixmbr will do nothing more than fix the mbr. Or nothing at all. A few years ago I was doing a bit of "stress-testing" of bootloaders for my own education. The Win XP install CD happily repaired the mbr on one computer but didn't on another. It didn't do any damage. It just didn't do anything. I never did find out why. Let's hope that doesn't happen to you.

Good luck and I hope this episode doesn't put you off Ubuntu for ever. There are other ways than installing it to a thumb drive. When things have settled perhaps you might want to try a different approach.

---

### Post by Amente on 2010-11-13
> **tweakedenigma said:**
> I could be wrong but won't this also leave him/her without a Bootloader?
ya! you are right,It will ,my bad! So what he can do next is install grub in partition that he wants
by typing 
```

apt-get install grub-pc grub-common # select the appropriate options when asked


```

---


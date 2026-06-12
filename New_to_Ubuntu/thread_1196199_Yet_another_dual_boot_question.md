---
title: "Yet another dual boot question"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by NAys on 2009-06-24
I have 2 disks and sometimes I detach my second one (where ubuntu is ) and my grub loader stops working(error 21) which I assume is normal.
I win xp disk is the bigger (and newer) one and never gets detached. 

My question being how do I make the win xp the default disk so even if I detach the smaller one I can still log onto the bigger one.


Another non related question - I installed wine and am trying to install a win program from a dvd but it tells me "access denied". I don't even get to type my password or anything . Is there an easy fix for that? ( I thought scott ritchie.gpg was suposed to do something about access) edit: I tried going to properties and it says I'm not the owner of install.exe - says the owner is user 503 from a group dialout.

Also I tried editing the menu.lst file (so default option is win xp although I doubt that would fix it and it tells me I cannot save the file since I don't have permission. (absolute noob here)

---

### Post by presence1960 on 2009-06-24
put GRUB on the MBR of the windows disk. make the windows disk boot ahead of the ubuntu disk in BIOS.

---

### Post by LewRockwell on 2009-06-24
perhaps the easiest thing to do would be to install ubuntu on your primary hard drive and then use the USB hard drive as a back-up

without knowing your system information I can't really offer more specific suggestions

---

### Post by LewRockwell on 2009-06-24
> **presence1960 said:**
> put GRUB on the MBR of the windows disk. make the windows disk boot ahead of the ubuntu disk in BIOS.

Grub is on the MBR of the primary(windows)hard drive

that's why there is a grub error as opposed to a "non-boot" error message


the menu.lst file is on the USB (ubuntu) drive and works fine when the drive is plugged in so there is no reason to edit the menu.lst


I'd like to have the information requested in my signature area so I can attempt to provide more insight into this situation

---

### Post by presence1960 on 2009-06-24
> **LewRockwell said:**
> Grub is on the MBR of the primary(windows)hard drive

that's why there is a grub error as opposed to a "non-boot" error message


the menu.lst file is on the USB (ubuntu) drive and works fine when the drive is plugged in so there is no reason to edit the menu.lst


I'd like to have the information requested in my signature area so I can attempt to provide more insight into this situation

sorry there lewrock, i misunderstood. I stand corrected! Thanks.

---

### Post by egalvan on 2009-06-24
One way of having GRUB work when the second drive is disconnectred is to create a separate GRUB partition on the first drive.

herman over at hermanzone has a tutorial on this

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

It isn't newbie-freindly, you'll have to read it all...
and post questions about it.

Also, do as LewRockwell suggested and post more info.

caljohnsmith and meifera have an excellent "boot_info" script which will extract a lot of info...

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)


post #3 at this thread has the man himself, take a look at it...

[http://ubuntuforums.org/showthread.php?t=1155246](http://ubuntuforums.org/showthread.php?t=1155246)

---

### Post by NAys on 2009-06-24
title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        70bf9607-92e0-4a5c-963c-0c40c256fde8
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=70bf9607-92e0-4a5c-963c-0c40c256fde8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic

I guess that's my  Ubuntu version. And as long as both drives are plugged in I have no problems whatsoever(btw it's not a USB drive, just a normal old ide drive). But if I decide to unplug the second drive (or god forbid uninstall linux - that's just a guess ) my windows drive stops working and I get the error 21.  I read in help somewhere that unplugging the second drive should make me just boot to windows but it doesn't happen. 
For now it's not really a problem but it would become one if I decide I don't want second drive or linux anymore...

The solution I've read of was to just load from win installation cd and run mbrfix or w/e it's called. But then I'm betting I'm left without linux. Maybe next install I'll just unplug 1 and plug the other one. God I feel like a monkey with a club.


Oh yes Egalvan that's exactly what I need a grub partition on the first drive. Btw any idea how can I get access to make changes to my own files? Lol - linux doesn't work too well for noobs like me :). I now feel like that same monkey with a loaded gun.

---

### Post by Miljet on 2009-06-24
I don't understand why you are disconnecting your second drive. You can't use it somewhere else because it doesn't have grub installed to the MBR. If you disconnected it just to see if Windows would still boot, you now have your answer - it won't.

If you decide to remove Ubuntu at some time, you will need to run fixmbr to restore the Windows manager to the MBR of your first disk. And you are correct that it will replace GRUB and you will no longer be able to boot Ubuntu.

As for your permission problems, have you tried to put "sudo", without the quotes, in front of the command you are using? Or if you are using Nautilus to install, start nautilus from the terminal with "gksu nautilus".

---


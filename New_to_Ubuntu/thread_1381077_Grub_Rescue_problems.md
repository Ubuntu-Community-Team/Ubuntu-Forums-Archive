---
title: "Grub Rescue problems"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by DamianDDDDD on 2010-01-14
Hello, i'm new to Ubuntu and i have a problem.

I've installed Ubuntu on a USB flash drive, but i can't boot any of my drives, as i get the following error:

GRUB loading
error: no such disk
grub rescue>

Although i don't really mind the fact that Ubuntu doesn't work, i am very displeased with the fact i can't boot Windows XP from my primary hdd. I really need the Windows partition, so i hope someone on this forum has the solution to get me booting into Windows :)

---

### Post by tom.swartz07 on 2010-01-14
> **DamianDDDDD said:**
> Hello, i'm new to Ubuntu and i have a problem.

I've installed Ubuntu on a USB flash drive, but i can't boot any of my drives, as i get the following error:

GRUB loading
error: no such disk
grub rescue>

Although i don't really mind the fact that Ubuntu doesn't work, i am very displeased with the fact i can't boot Windows XP from my primary hdd. I really need the Windows partition, so i hope someone on this forum has the solution to get me booting into Windows :)

Im confused, you installed ubuntu ON the usb drive, or did you install it on your computer FROM a usb drive?

Either way, theres a link in my signature to help you get back up and running; grub2. just follow the guide step by step.

You need to boot to a liveCD version. be it liveusb or livecd- it doesnt matter. once you get up and running, that guide will cover it.

If you have any questions, ask first before you do- you might end up breaking it more if you act before checking.

hope this helps!

---

### Post by DamianDDDDD on 2010-01-14
I've installed Ubuntu on my USB drive with a little help of a burned CD :P

I will try to fix it and post my results.

---

### Post by Dreakon on 2010-01-14
I'm not sure how this works with Windows XP, but I had a similar problem when I would removed the Ubuntu partition from my hard drive and try to load Windows again.  I had Windows 7 though and not Windows XP... so hopefully it works for you.

If you want XP back, try this and let me know how it works...

Load the Windows XP installation CD (boot with it).  Even a recovery disk given to you from the PC manufacturer could get the job done.
Somewhere in the installation setup (usually in the first few windows) look for something along the lines of "Repair Windows".
Somewhere in there look for something like "Command Line".
Whatever it says, just make sure you get to the command window lol.  For all I know it may not be possible with the Windows XP installation, but again, this is what I did to fix Windows 7 when I had this problem...

In the command line, type in:

bootrec.exe /fixboot

Press Enter.  Then type in:

bootrec.exe /fixmbr

Press Enter again.  Then X out of the command line window and get out of the Windows installation.  Take the CD out and try loading Windows again.  Hopefully it'll work for you!  Good luck!

---

### Post by DamianDDDDD on 2010-01-14
I am lost. The keyboard doesn't work in the menu on the disc. Any advice?

---

### Post by audiomick on 2010-01-14
Hi.
either enable "usb legacy" in bios, or use an old (what was it called again, PS2? ) keyboard that is not usb.

---

### Post by tom.swartz07 on 2010-01-14
> **DamianDDDDD said:**
> I am lost. The keyboard doesn't work in the menu on the disc. Any advice?

could you be more specific?
What menu? the gray panel at the top, or the boot selection menu?

---

### Post by DamianDDDDD on 2010-01-14
Sorry, never mind. The keyboard didn't work in the first menu, but it automatically booted Ubuntu from the CD. I will try your instructions :3

---

### Post by DamianDDDDD on 2010-01-14
>   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sda2            9730       19457    78140160    f  W95 Ext'd (LBA)
/dev/sda5            9730       19457    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
255 heads, 63 sectors/track, 1948 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d63c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1860    14940418+  83  Linux
/dev/sdb2            1861        1948      706860    5  Extended
/dev/sdb5            1861        1948      706828+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ I guess sda2 is my USB flash drive, because i didn't format it to HPFS/NTFS. I only need to mount sda1, sda2 and sda5. right? Do i need to install Grub on just sda (not sda2)? Sorry for asking so many questions, but i'm very new to this kind of stuff.

---

### Post by tom.swartz07 on 2010-01-14
> **DamianDDDDD said:**
> I guess sda2 is my USB flash drive, because i didn't format it to HPFS/NTFS. I only need to mount sda1, sda2 and sda5. right? Do i need to install Grub on just sda (not sda2)? Sorry for asking so many questions, but i'm very new to this kind of stuff.

It looks like you installed ubuntu on a separate disk? Possibly a flash drive, or do you have 2 internal hard drives?

Thats not right.


sda1 is windows, sdb1 is Linux.

Try going through the instructions mounting those two partitions and see if it works. If not, just mount sda1 and do the instructions. 



Its never recommended that you install an operating system on a removable drive, particularly when the bootloader looks for it when you turn your computer on.

You might have to go through the install again and physically put it on your hard drive installed 'side by side' to work.

---

### Post by DamianDDDDD on 2010-01-14
When i try to mount sda1:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy

When i try to mount sdb1:

ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ 

What to do now? :(

---

### Post by tom.swartz07 on 2010-01-14
> **DamianDDDDD said:**
> When i try to mount sda1:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy

When i try to mount sdb1:

ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ 

What to do now? :(

did you run the mount command for sda1 twice, or were you writing to the partition? 

just to check if its mounted you could run
```
ls /mnt
```
and see whats listed there.

Either way, you could continue with sdb mounted- as thats your linux partition.

---

### Post by DamianDDDDD on 2010-01-14
I didn't use the Windows partition. When i use ls /mnt, i get the following words:

bin, boot, cdrom, dev, etc, home, initrd.img, lib, lost+found, media, mnt, opt, proc, root, sbin, selinux, srv, sys, tmp, usr, var, vmlinuz

On which sdXY should i install Grub2? Or do you have another solution?

---

### Post by tom.swartz07 on 2010-01-14
> **DamianDDDDD said:**
> I didn't use the Windows partition. When i use ls /mnt, i get the following words:

bin, boot, cdrom, dev, etc, home, initrd.img, lib, lost+found, media, mnt, opt, proc, root, sbin, selinux, srv, sys, tmp, usr, var, vmlinuz

On which sdXY should i install Grub2? Or do you have another solution?

you still didnt say whether you installed it on a usb key or not...



Personally, Either way I would reboot the computer and boot the livecd again, and follow this guide to install on my internal hard drive. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Instead of using the entire disk, select side-by-side. 


That would clear up any problems you have with your bootloader, and it would assure that you have Ubuntu installed on a permanent location.



If you are worried about extra room on your drive, we could fix it after the OS is installed and we could boot your computer without 'life support' :P


Good luck.

---

### Post by DamianDDDDD on 2010-01-14
I did install Ubuntu on my new USB key/flash drive/stick. I'm not sure if i have enough space on the other drives and i'm afraid to make a new partition. Is there another solution to get it fixed? Is there a way to delete Grub from my pc? :(

---

### Post by tom.swartz07 on 2010-01-14
> **DamianDDDDD said:**
> I did install Ubuntu on my new USB key/flash drive/stick. I'm not sure if i have enough space on the other drives and i'm afraid to make a new partition. Is there another solution to get it fixed? Is there a way to delete Grub from my pc? :(

Best way to fix it now is to use a Windows recovery cd. I think someone mentioned it before, but ill post a link here again. 

[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)

it takes some digging, so I'll summarize here.. 
> Obtain a bootable Windows CD, and use it to boot.
I waited through all the Bill-messages until I got the first prompt. Choose R to repair an existing installation.
It searched and prompted me for the Windows installation, showing me:
1) C:\WINDOWS
I chose 1, and it asked for the Admin password. Heh, I guess the previous owner never set one, so I just pressed Enter and got my
C:\WINDOWS>
Now, from the sad_iq link:
C:\WINDOWS> CD ..
C:\> FIXBOOT C:
C:\> FIXMBR
C:\> BOOTCFG /rebuild

After the BOOTCFG, itll ask if you wanted to add the Installation it found, and to be safe answer "Y".
Good Luck!

---

### Post by tom.swartz07 on 2010-01-14
If you still want to run linux on a USB, follow the guides here: [www.pendrivelinux.com](www.pendrivelinux.com)

They show you how to get your USB key set up so that you could run ubuntu on it no problem.

Sorry about the confusion. The main problem came from the fact that your hard drive was looking for an OS that wasnt were it was supposed to be.

Once you get back up and running, Def look into the liveusb versions. theyre really good, and they run on 2 gig keys.

Hope this helps

---

### Post by DamianDDDDD on 2010-01-14
Is it a problem if i use a Windows 7 disc to repair my XP install? Will it work?

---

### Post by tom.swartz07 on 2010-01-14
> **DamianDDDDD said:**
> Is it a problem if i use a Windows 7 disc to repair my XP install? Will it work?

hmm. not so sure.
I havent fixed a windows install in a while. maybe someone else would know.


My gut reaction would be to say, no. If youre really stuck, PM me- i have a partnership with IEEE that allows me to create windows rescue discs- I could send you one.

Ask around first. Im sure someone has an XP disc somewhere, considering how much of a flop vista was! :P

---

### Post by Dreakon on 2010-01-14
> **DamianDDDDD said:**
> Is it a problem if i use a Windows 7 disc to repair my XP install? Will it work?
You could try it.  I gather having some sort of bootloader will make Windows happier then none.  The first thing the Windows 7 installation will do (for me at least) is see if you have any previous installations on your hard drive.  If it notices the Windows XP installation and you select it, maybe it'll be smart enough to try and do things right for you.

As long as you get to some sort of command line prompt, I'd say you're on the right track.

Oh... but don't take anything I say as actual intelligence.  I can't be blamed if anything goes wrong in doing this lol.  I'm probably the newest person here...

---


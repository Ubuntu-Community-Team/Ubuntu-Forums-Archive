---
title: "Intallation failed. Windows not working either. Oops."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Fidelio on 2009-01-27
Hi,
I've been using ubuntu for well over a year on my 'home pc' but I decided to install it on the pc in my audio studio as a dual boot with Windows XP.
I have two separate drives, both running XP, so it's a dual boot system already, but both are XP. I attempted to install Ubuntu on one of these drives by resizing the NTFS partition. Everything looked fine, but when I rebooted I just got the same two windows boots as an option. And one of them doesn't work. It gives me an error message saying 'hal.dll is corrupt or missing'
Any ideas what went wrong and how to fix it?
Thanks
F

---

### Post by SOULRiDER on 2009-01-27
I had to fix that error at work. Its a windows problem, I believe you had toe dit c:/boot.ini which is similar to /boot/grub/menu.lst
Thats what I can remember, do a google search for more info.

Good luck.

---

### Post by caljohnsmith on 2009-01-27
As SOULRiDER all ready mentioned, you may need to modify your Windows boot.ini file, because that is the common cause of a hal.dll missing error. Did you resize the Windows partition from the beginning to make room for Ubuntu, or did you put Ubuntu physically after the Windows partition on the drive? How about posting:
```
sudo fdisk -lu
```
So we can get an idea of your current partitions.

---

### Post by Fidelio on 2009-01-28
Hi. I did the guided resize existing partition option during installation, and installed ubuntu into the new partition.
I'd love to be able to post my fdisk info, but as I said, I can't get into ubuntu. I don't get a grub at boot-up just the same choice of my two xp installations.
But my disks are a 250gb SATA disk, which I resized to a 200gb NTFS partition and the rest for the Ubuntu installation.
A 120gb eide disk, partitioned into 50gb System and 70gb data, both NTFS.

---

### Post by caljohnsmith on 2009-01-28
How about booting your Live CD, choose the "try Ubuntu without making changes" option, and once you get to the Ubuntu desktop, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by Nightstrike2009 on 2009-01-28
I am unsure as to if this will be useful or not, but ive found when my dual-boot breaks I can get XP back by booting from windows xp cd, selecting recovery console, and typing FIXMBR. This usually gets my XP back leaving me to just install Ubuntu again. This may only work with a corrupted Master Boot Record though (Stupid Grub errors), not sure if it helps but maybe worth a try. :-)

---


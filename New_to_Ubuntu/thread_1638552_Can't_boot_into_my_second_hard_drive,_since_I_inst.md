---
title: "Can't boot into my second hard drive, since I installed Ubuntu 10.04?"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Bad Wolf 12345 on 2010-12-05
Firstly, I know nothing about Ubuntu and can't use it whatsoever. I am great with Windows, so I would prefer to do everything in Windows, unless I have a great step-by-step instructions on how to do it using Ubuntu. Ok, this is a long story to bear with me. I have searched through so many threads; some are similar, but not enough to be helpful.

Firstly I began with having one hard drive which I took out of my old Compaq desktop; an IDE which is 80GB which had Windows XP installed. I then bought a 1TB SATA hard drive, and built a PC which contained this new 1TB SATA HDD, and my old 80GB IDE HDD from my old Compaq desktop. I then copied my IDE hard drive to my new SATA hard drive. It worked perfectly, and I continued using it for about 5 months with no problems; until I thought of trying Ubuntu 10.04.
So I downloaded Ubuntu 10.04 and created the live CD. I then installed it onto my SATA hard drive onto a separate partition. I was having many problems, as I did not know how to connect to the internet through a dial up connection. So I rebooted and booted into Windows XP (on my SATA drive), and used EASEUS Partition Master to delete the partition which Ubuntu was on. When I booted into my SATA HDD, it said ‘error: no such partition. Grub Rescue>’. When I booted into my IDE drive, it said ‘error: no such device: 23d99b21-268a-41e0-9c58-b62389293782. Grub Rescue>’ 
I have been trying for weeks to get it back to the way it was, where it just boots straight into the OS of whichever drive I boot from. So I reinstalled Ubuntu using the Live CD, so that I can use GRUB 2 to get back into Windows. Now all I can do is boot into my SATA HDD, but not my IDE 80GB hard drive. 
Now, the only way I can get into any OS is by having Ubuntu and Grub installed. When it is installed, it gives me the following options:

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (Recovery Mode)
(memtest86+)
(memtest86+, Serial Console 115200)
Microsoft Windows XP Home Edition (/dev/sda1)
Windows NT/2000/XP (/dev/sda2)
Windows NT/2000/XP(/dev/sdb1)

I can boot into Ubuntu (top option) which takes me to Ubuntu (obviously). I haven’t tried the next three, as I don't really know what they are. When I choose the fifth option ( Microsoft Windows XP Home Edition (/dev/sda1)), it gives me the option to go into Windows XP Home Edition, or Windows XP Recovery Console. If I choose the Windows XP Home Edition, it gets to the Microsoft Windows XP loading screen (blue screen, with the Windows logo) and stools, so I have to restart. If I choose the Recovery Console, it asks me which Windows installation:
1: E: \WINDOWS
2: C: \WINDOWS
3: D: \MiniNT
4: D: \I386

When I choose the sixth option (Windows NT/2000/XP (/dev/sda2)), another Windows Recovery Console starts loading, and gives me the same options as when I booted into the Recovery Console of /dev/sda1.
When I choose the last/seventh option, Windows starts fine, as that is what I am on now. 

I really don’t know what is going on, and all I want to do is get it back to the way it was, I.e. It boots into the OS (Windows XP) of whichever HDD I choose to boot into in BIOS.
I have searched for so long for the solution with no success. I do not have the Recovery disks, and I cannot make them as I cannot boot into my original IDE drive which has the original Windows XP Home Edition on. I can't make them in the SATA hard drive (which I coppied Windows XP to), as I do not think it coppied the partition which had the recovery image on. 

Thank you so much for your time, and any help would be much appreciated.

---

### Post by drs305 on 2010-12-05
Try doing this from the LiveCD. It will (partially) install lilo, another bootloader. If the boot flag is still on your Windows OS, and it's files haven't been corrupted, this should allow Windows to boot. I am assuming the SATA drive is sda in the following commands. Again, this will work if the Windows booting hasn't been corrupted - all you are doing is pointing to the Windows partition with the boot flag from the MBR. If you aren't sure if Windows will boot, you may not want to do this. If it fails, you will have to reinstall Grub2.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot.

---

### Post by wannacme16 on 2010-12-05
As much as you might like to use windows to fix this issue my suggestion is to boot into Ubuntu (first option at boot screen) and go to system, administration, disk utility. From here you have access to all internal hard drives and also external drives. You can mount any of these drives and examine, copy, etc.. From your post you didn't specify tool you used to make copy of XP for moving from IDE to SATA. My suggestion google linux alternative to your tool that copied XP. If you want to try Ubuntu without any connection to Windows installation try wubi or have 2 disks (1 for Windows and 1 for Ubuntu) and when you install Ubuntu have your hard drive with Windows disconnected. When you reboot hit the boot menu key (F12 in mine) and chose Windows or Ubuntu. When you do an update in Ubuntu that involves a kernel have your Windows disconnected or you may have similar problems again. If you can stick with Ubuntu and learn your way around as you have with Windows you will be better, trust me I started with Windows and wouldn't go back for nothing. Freedom is a wonderful commodity.

---

### Post by Bad Wolf 12345 on 2010-12-05
Just discovered soething interesting. I took out my IDE drive, rebooted and there were the same options in Grub:

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (Recovery Mode)
(memtest86+)
(memtest86+, Serial Console 115200)
Microsoft Windows XP Home Edition (/dev/sda1)
Windows NT/2000/XP (/dev/sda2)
Windows NT/2000/XP(/dev/sdb1)

So there must have never been a boot option for my IDE drive... So if I put ONLY my IDE drive in, how can I make the drive a boot option?

Thanks again.

---


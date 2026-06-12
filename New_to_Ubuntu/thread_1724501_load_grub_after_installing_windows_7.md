---
title: "load grub after installing windows 7"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-04-08
I had ubuntu and then installed new windows 7 but now the grub does not load and i can't start ubuntu. How do I start ubuntu?

---

### Post by lindsay7 on 2011-04-08
[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by RobikShrestha on 2011-04-08
I do not have a ubuntu live cd. Can't I do something from windows 7? Does it not recognize ubuntu?

---

### Post by coffeecat on 2011-04-08
> **RobikShrestha said:**
> I do not have a ubuntu live cd. Can't I do something from windows 7? Does it not recognize ubuntu?

No. You need to reinstall grub to the mbr. You cannot do this from Windows. Windows does not use grub. Can you download an Ubuntu ISO to burn a CD, or do you have limited bandwidth?

---

### Post by Rubi1200 on 2011-04-08
If you don't have a LiveCD, how did you install Ubuntu in the first place?

---

### Post by RobikShrestha on 2011-04-08
What is the size of ubuntu iso? I can if it is under 300 MB but i guess it would be much larger. I knew I should have done an iso before but too lazy to do so.

---

### Post by RobikShrestha on 2011-04-08
I have mint-8 iso file. But I want ubuntu. Will it help if i create a live usb?

---

### Post by RobikShrestha on 2011-04-08
@rubi: I borrowed it from a friend. But now the CD is scratched

---

### Post by coffeecat on 2011-04-08
The ISO is about 680-690 MB. It's certainly worth having a live CD of Ubuntu even if you don't have an immediate need to re-install grub. It is too valuable as a repair utility to not have it available.

---

### Post by coffeecat on 2011-04-08
> **RobikShrestha said:**
> I have mint-8 iso file. But I want ubuntu. Will it help if i create a live usb?

Mint 8 is based on Ubuntu 9.10 (Karmic) I believe. What version of Ubuntu are you running? You really need to reinstall grub from the same version of Ubuntu as you are running - or he equivalent Mint. The minor differences between the versions of grub2 in Lucid, Maverick and Natty can cause problems.

Live CD or live USB - makes no difference. The ISO version matters.

---

### Post by RobikShrestha on 2011-04-08
I had ubuntu 10.04 and now i have iso files for mint 7 and 8

---

### Post by RobikShrestha on 2011-04-08
I have another question. I now have two windows 7's. But i can start only the newest one. How do i get rid of the previous one. Should i just delete windows.old directory? I am really beginning to hate this windows 7 - selfish. Why does not it support linux file system?

---

### Post by coffeecat on 2011-04-08
What do you mean you have two Windows 7's? Do you have two partitions with separate Windows installations on them? If you have just one and you have a windows.old folder in it, that is simply the version of Windows you upgraded from. When you upgrade some versions of Windows, it creates a windows.old folder to put the obsolete files in. If you had Windows 7 before and you have Windows 7 now and you have a windows.old folder, then it sounds as though you upgraded from Windows 7 to Windows 7!

Windows doesn't support Linux filesystems because it has no need to.

---

### Post by RobikShrestha on 2011-04-08
Can i just simply shift+delete the windows.old folder (because program files are useless) or is there another procedure?

---

### Post by rosencrantz on 2011-04-08
You can use the SuperGrub disk to boot Ubuntu, it's much smaller than the LiveCD.
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)
When Ubuntu is up and running, follow the instructions from the Ubuntu wiki to restore your Master Boot Record.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
This is for Vista, but it might help in cleaning up your install:
[http://support.microsoft.com/kb/930527/en-us](http://support.microsoft.com/kb/930527/en-us)
And there are third-party drivers for Linux file systems for Windows - but they won't help you in restoring your MBR.

---

### Post by RobikShrestha on 2011-04-08
I do not have a cd or dvd but can i make use that iso file through pen drive?

---

### Post by rosencrantz on 2011-04-08
Sure. Use Unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
There's just one thing with loading grub from a pendrive:
Your hard drive order will change, with the pendrive as the first and your primary hard disk as the second one.
I'm on grub1, so I can't give specific instructions. 
Try selecting the Ubuntu grub entry after SuperGrub has loaded it and press 'e' to (temporarily) edit. Replace all occurrences of (hd0,x) with (hd1,x) - x being probably 4 or 5 - and boot.

(You won't have that issue with a CD boot)

---

### Post by RobikShrestha on 2011-04-08
it says it can't find ubnkernel
i tried to install supergrub into usb via unet, it shows many menus
with grub=>mbr (auto) etc. but takes a long time and i do not think it is working, i do not what is happening

---

### Post by rosencrantz on 2011-04-08
Hm, difficult to say, as I can't see your screen and I haven't used grub2 a lot. 
Did you download the right version? it has to be SuperGRub2 and not SuperGrub.
Did SuperGrub find your grub? If it can't find the kernel, I'd assume it's the disk order issue.

---

### Post by wilee-nilee on 2011-04-08
Here is a multiboot loader for a thumb that you can use in Windows to load the supergrub.
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

So down load specifically the supergrub2 disc from here and use the yumi loader above, to load the thumb, it has a load an iso from the computer function, rather then a net load. With this super grub2 just boot it and choose detect any OS and you will see the linux boot in and reload the mbr from the Ubuntu terminal.
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

If your hard drive is sda to load the mbr with grub run these two commands.

sudo grub-install /dev/sda
then sudo update-grub

---

### Post by RobikShrestha on 2011-04-08
Thank you all of you!! The problem is finally solved. I have my grub back.!

---

### Post by rosencrantz on 2011-04-09
Great! Now mark your thread as solved for the benefit of others.
[http://ubuntuforums.org/showthread.php?t=524404](http://ubuntuforums.org/showthread.php?t=524404)

---


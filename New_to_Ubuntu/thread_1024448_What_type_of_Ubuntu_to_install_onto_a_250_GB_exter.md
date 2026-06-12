---
title: "What type of Ubuntu to install onto a 250 GB external HD?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by PwnCakes193 on 2008-12-29
I want to install Ubuntu onto my External Hardrive thats 250 GB so i can use it on any computer I plug it in to. How would I do this? I was thinking of Unetbootin, but does that make it a "persistent" install? I want to keep documents, and be able to save changes to it too.

Thanks for your input

---

### Post by bumanie on 2008-12-29
Have a look at the links on [this site]("http://www.pendrivelinux.com/") - you should find a method that suits your needs

---

### Post by PwnCakes193 on 2008-12-29
Yes,Ive used that before, but have had problems with running out of memory. Is UNetBootin persistent?

---

### Post by neu2buntu on 2008-12-29
i would try the ubuntu 8.10 live cd made from the downloadable .iso [http://www.ubuntu.com/getubuntu/download ]("http://www.ubuntu.com/getubuntu/download")
from here ,           and do a full install to your external hdd...   and make sure you put the bootloader on that hdd also.   i can walk you through this if you need!!!

---

### Post by albinootje on 2008-12-29
> **PwnCakes193 said:**
> I want to install Ubuntu onto my External Hardrive thats 250 GB so i can use it on any computer I plug it in to. How would I do this? I was thinking of Unetbootin, but does that make it a "persistent" install? I want to keep documents, and be able to save changes to it too.

I suggest you do a normal Ubuntu installation on it on a machine without any other hard disk or usb-stick or usb-disk attached, to prevent Grub problems.

---

### Post by DGortze380 on 2008-12-29
> **PwnCakes193 said:**
> I want to install Ubuntu onto my External Hardrive thats 250 GB so i can use it on **any computer** I plug it in to. How would I do this? I was thinking of Unetbootin, but does that make it a "persistent" install? I want to keep documents, and be able to save changes to it too.

Thanks for your input

Not possible. Computers have different architectures and hardware. You're welcome to try, it may even work on a couple of machine that support booting from USB, but it certainly won't work on every machine you plug it into, or even most for that matter.

---

### Post by mlentink on 2008-12-29
> **DGortze380 said:**
> Not possible. Computers have different architectures and hardware. You're welcome to try, it may even work on a couple of machine that support booting from USB, but it certainly won't work on every machine you plug it into, or even most for that matter.

+1

Though it is entirely possible to install ubuntu on an external drive without messing with your internal set-up (This is how i test out new releases and other distros), such an install is machine-specific. You will run into difficulties if you use it on other configurations.

For a LiveUSB approach you will not need 250Gigs. A USB flash-drive is more than enough.

---

### Post by snowpine on 2008-12-29
> **DGortze380 said:**
> Not possible. Computers have different architectures and hardware. You're welcome to try, it may even work on a couple of machine that support booting from USB, but it certainly won't work on every machine you plug it into, or even most for that matter.

This is not totally correct. An Ubuntu install is not machine-specific; it detects hardware every time you boot up. If the hardware is capable of running an Ubuntu Live CD and also capable of booting from USB, your USB hard drive install will work just fine.

To answer the original question, any "flavor" of Ubuntu will be equally suited for your task. Whichever you prefer. 250gb is plenty of space. Don't use Unetbootin. Use an Ubuntu Live CD and simply install to the USB drive just as you would to an internal HDD, but with one exception: When you get to the last step of the installer, click Advanced Options and install the Grub bootloader to the correct device (for example /dev/sdb) instead of your internal drive.

---

### Post by mlentink on 2008-12-29
> **snowpine said:**
> This is not totally correct. An Ubuntu install is not machine-specific; it detects hardware every time you boot up. If the hardware is capable of running an Ubuntu Live CD and also capable of booting from USB, your USB hard drive install will work just fine.
True. And I agree with the caveat: it will only work when the target system is capable of running ubuntu in the first place. Which, unfortunately, is not every system around, or only with extra tweaking.
> **snowpine said:**
> To answer the original question, any "flavor" of Ubuntu will be equally suited for your task. Whichever you prefer. 250gb is plenty of space. Don't use Unetbootin. Use an Ubuntu Live CD and simply install to the USB drive just as you would to an internal HDD, but with one exception: When you get to the last step of the installer, click Advanced Options and install the Grub bootloader to the correct device (for example /dev/sdb) instead of your internal drive.

Please also do not forget to edit the /boot/grub/menu.lst file on the USB-drive after installation to reflect the 'true' drive setup.

---

### Post by Pobega on 2008-12-29
> **DGortze380 said:**
> Not possible. Computers have different architectures and hardware. You're welcome to try, it may even work on a couple of machine that support booting from USB, but it certainly won't work on every machine you plug it into, or even most for that matter.

This is a pretty pointless post, honestly. 90% of desktop computers today use the x86 architecture, and with on the fly hardware detection thanks to init ramdisks you could at least get ethernet to work on most computers the same way that the Ubuntu LiveCD autodetects everything; and really, even wireless isn't that hard to do.

As for PowerPC computers, you could always put a 5GB partition on the drive with a PPC installation of Ubuntu.

---

### Post by Bigbob22 on 2008-12-29
I am pretty sure that you can put Ubuntu on the external HD, but it will work only with the computer you initially installed Ubuntu on the external HD. Please correct me if I'm wrong.

Edit: Nvm, I was wrong. I forgot to look at previous replies.

---

### Post by snowpine on 2008-12-29
> **mlentink said:**
> 
Please also do not forget to edit the /boot/grub/menu.lst file on the USB-drive after installation to reflect the 'true' drive setup.

Can you explain this last part a little more?
My USB installs always seem to book ok, maybe I'm doing something wrong. :)

---

### Post by mlentink on 2008-12-29
> **snowpine said:**
> Can you explain this last part a little more?
My USB installs always seem to book ok, maybe I'm doing something wrong. :)

Depends on how you install. Do you usually disconnect all internal drives when installing to the the USB-drive? If so, no prob.
I usually install with everything attached, including my internal harddisk. Then i install to the external harddrive, hd1 rather than hd0. GRUB will reflect that, so you need to 'reset' it to be able to boot from that drive afterwards. No big deal, a simple matter of changing drive designations around.

---

### Post by PwnCakes193 on 2008-12-29
> **neu2buntu said:**
> i would try the ubuntu 8.10 live cd made from the downloadable .iso [http://www.ubuntu.com/getubuntu/download ]("http://www.ubuntu.com/getubuntu/download")
from here ,           and do a full install to your external hdd...   and make sure you put the bootloader on that hdd also.   i can walk you through this if you need!!!

Can you? That would help so much, I tried doing a Wubi install, only to realize that the bootloader only worked on my laptop and no other computer. If you need to contact me outside of this thread, email me at [email]xblaze93@gmail.com[/email] or PM me here, or post on this thread.

And guys, I know that I can only do it to machines that use USB booting, which is basically any computer I use so that is no problem. Any other help is greatly needed

---

### Post by albinootje on 2008-12-29
> **PwnCakes193 said:**
> Can you? That would help so much, I tried doing a Wubi install, only to realize that the bootloader only worked on my laptop and no other computer. If you need to contact me outside of this thread, email me at [email]xblaze93@gmail.com[/email] or PM me here, or post on this thread.

And guys, I know that I can only do it to machines that use USB booting, which is basically any computer I use so that is no problem. Any other help is greatly needed

Wubi is kind of "Ubuntu via Windows".

I would again recommend to install Ubuntu on the usb-disk directly.
That should work fine on different machines which can boot from usb directly.
You might come across machines where the resolution is far from perfect, or unusable, but usually it should be fine.
Think of it as using a Linux Live CD which you try on several different machines.

---

### Post by PwnCakes193 on 2008-12-29
What I did was I installed Wubi to My F: disk. the ubuntu files were on the External Hardrive but GRUB was on my C: Drive

---

### Post by neu2buntu on 2008-12-30
ok i will do this as a step by step tutorial 

(1) go here [http://www.ubuntu.com/GetUbuntu/download ]("http://www.ubuntu.com/GetUbuntu/download")
and choose desktop 8.10 edition i386 (usually 32 bit) 
(2)click on begin download button,this will open a window on your computer,choose save file,click ok ...this will download the .iso cd image
(3) once downloaded,right click on the image and open with cd/dvd creator ,choose burn to disk ,choose slowest speed place blank cd-r in tray and burn
(4) reboot and press f2 or esc and in bios choose boot and choose boot from cdrom drive first save changes and exit...have your external hdd plugged in also on reboot...and newly burned cd-r in drive
(5) on the cd menu you can choose install or try live cd,if you pick try live cd thats ok once loaded there is an icon for install on desktop,double click it
(6)there are questions for username,password,location,keyboard ,etc cant remember if they are first but this is all straightforward
(7) you will be prompted about partitioning the disk , choose GUIDED -USE ENTIRE DISK and make sure to choose (sdb) the make of your externall hdd should also be shown here (sda) will/should be your internal hdd ....click FORWARD 
(8)there are 7 steps of install, and this is the most important bit to get right, in step 7 choose advanced and in this box make sure to put the bootloader onto disk (sdb) and if there is no (sdb) on its own choose (sdb1) then install
(9) after install reboot (you will be prompted to remove cd and hit return) and as in step (4) goto bios settings choose to boot first from external hdd 
(10) the boot menu in your new installation will show whatever is installed on your computer ,this is easily removed by editing the menu.lst file if you dont want it there .....  to edit this file goto terminal and type ```
sudo gedit /boot/grub/menu.lst
```... but if you are to use the external hdd mostly on your own computer i would leave it alone

well thats it ,hope this helps ok  (probably could have been shorter but i got carried away a bit...lol)

---

### Post by gn2 on 2008-12-30
USB hard drives do not always make good bootable devices because they do not always spin up in time to be detected by the BIOS at boot.

Flash drives are far better for this purpose.
You would be better with a combination of persistent USB flash drive for the OS and a 2.5" hard drive for file storage mounted as /media

---

### Post by RealG187 on 2008-12-30
Unetbootin for Live CD
I think Pendrive Linux for persistent

If you have Ubuntu installed on a USB device, wouldn't there be  different drivers and stuff for different computers, so would it boot on any computer? And if so would it be buggy?

---

### Post by PwnCakes193 on 2008-12-30
> **neu2buntu said:**
> ok i will do this as a step by step tutorial 

(1) go here [http://www.ubuntu.com/GetUbuntu/download ]("http://www.ubuntu.com/GetUbuntu/download")
and choose desktop 8.10 edition i386 (usually 32 bit) 
(2)click on begin download button,this will open a window on your computer,choose save file,click ok ...this will download the .iso cd image
(3) once downloaded,right click on the image and open with cd/dvd creator ,choose burn to disk ,choose slowest speed place blank cd-r in tray and burn
(4) reboot and press f2 or esc and in bios choose boot and choose boot from cdrom drive first save changes and exit...have your external hdd plugged in also on reboot...and newly burned cd-r in drive
(5) on the cd menu you can choose install or try live cd,if you pick try live cd thats ok once loaded there is an icon for install on desktop,double click it
(6)there are questions for username,password,location,keyboard ,etc cant remember if they are first but this is all straightforward
(7) you will be prompted about partitioning the disk , choose GUIDED -USE ENTIRE DISK and make sure to choose (sdb) the make of your externall hdd should also be shown here (sda) will/should be your internal hdd ....click FORWARD 
(8)there are 7 steps of install, and this is the most important bit to get right, in step 7 choose advanced and in this box make sure to put the bootloader onto disk (sdb) and if there is no (sdb) on its own choose (sdb1) then install
(9) after install reboot (you will be prompted to remove cd and hit return) and as in step (4) goto bios settings choose to boot first from external hdd 
(10) the boot menu in your new installation will show whatever is installed on your computer ,this is easily removed by editing the menu.lst file if you dont want it there .....  to edit this file goto terminal and type ```
sudo gedit /boot/grub/menu.lst
```... but if you are to use the external hdd mostly on your own computer i would leave it alone

well thats it ,hope this helps ok  (probably could have been shorter but i got carried away a bit...lol)

Thank you So Much!!!! I Finally go it working and all that jazz! I am so grateful for this.

---

### Post by neu2buntu on 2008-12-31
happy days man,glad you got it sorted.... the ubuntu forums are here to help...hope you enjoy your new install of ubuntu!!!!

---


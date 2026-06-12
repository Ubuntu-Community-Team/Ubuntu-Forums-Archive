---
title: "ubuntu 10.04 doesn't work after fresh install"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by theWildHunt on 2011-07-02
Hi,   after the the succesfull installation of Windows 7 on hdd 1 and Ubuntu 10.04 (64 bit) on hdd 2 I encountered a problem running Ubuntu.   After selecting Ubuntu in the Grub boot manager the login form fires up but the screen is split in two by a black column at the center of my monitor (I can move the mouse to the border on one side and it appears on the other). If I enter the correct password nothing happens. I tried to run Ubuntu trough the recovery option in Grub but it only shows a purple screen and is freezing up. Windows works fine btw. I have already reinstalled Ubuntu once with the same results. I have no idea what's wrong or how to fix it, please help.    My system config:  Intel E6600 Dual-core 6  GB ram amd hd6870  hdd 1 1TB  hdd 2 250GB

---

### Post by IWantFroyo on 2011-07-02
Have you tried burning a new disc? Installation discs generally should be burned at 16X or lower.

---

### Post by wildmanne39 on 2011-07-02
> **theWildHunt said:**
> Hi,   after the the succesfull installation of Windows 7 on hdd 1 and Ubuntu 10.04 (64 bit) on hdd 2 I encountered a problem running Ubuntu.   After selecting Ubuntu in the Grub boot manager the login form fires up but the screen is split in two by a black column at the center of my monitor (I can move the mouse to the border on one side and it appears on the other). If I enter the correct password nothing happens. I tried to run Ubuntu trough the recovery option in Grub but it only shows a purple screen and is freezing up. Windows works fine btw. I have already reinstalled Ubuntu once with the same results. I have no idea what's wrong or how to fix it, please help.    My system config:  Intel E6600 Dual-core 6  GB ram amd hd6870  hdd 1 1TB  hdd 2 250GB
Hi, this link should get you fixed up.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by theWildHunt on 2011-07-02
Thanks for the replies.  Still not working though. I installed Ubuntu from an usb drive like described [here. ]("http://www.ubuntu.com/download/ubuntu/download")
I tried the 'nomodeset' parameter in grub. If I boot with ctr+X it gives me a black screen, with F10 it gives me the command prompt. However I have no idea how to proceed from there.

---

### Post by wildmanne39 on 2011-07-02
> **theWildHunt said:**
> Thanks for the replies.  Still not working though. I installed Ubuntu from an usb drive like described [here. ]("http://www.ubuntu.com/download/ubuntu/download")
I tried the 'nomodeset' parameter in grub. If I boot with ctr+X it gives me a black screen, with F10 it gives me the command prompt. However I have no idea how to proceed from there.Hi, get into recovery and try these two commands.
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Bucky Ball on 2011-07-02
What happens if you go through recovery and at the final screen of options hit 'Failsafe X'?

Also, if you get to a prompt, login in the terminal and then 'startx'. Does that get you to a desktop?

---

### Post by theWildHunt on 2011-07-02
> Code:
     sudo rm /etc/X11/xorg.conf      > Code:
     sudo dpkg-reconfigure xserver-xorg The first command returns an error 'no such file or directory'.
The second command doesn't return anything, no error or any other message.


If use startx I get 'Fatal server Error: no screens found'.
Edit: It also says: Failed to load module "fglrx"(module does not exist, 0); [KMS] drm report modesetting isn't supported; and RADEON(0):Chipset:"AMD Radeon HD 6800 Series" CChipID = 0x6738 ) requires KMS; Screens found, but none have a usable configuration.

---

### Post by Bucky Ball on 2011-07-02
The result of 'startx' gets us somewhere. As suspected, graphics. 

I would add back the nomodset and try a few other options when editing the kernel line, perhaps 'acpi=no'. There maybe a specific one for your setup and Ubuntu. I'd identify the graphics card and start digging. 

Entering via Recovery kernel and then choosing 'Failsafe X' doesn't get you to a desktop with low graphics? That would at least give you a chance to fix in a GUI (and install fglrx).

---

### Post by theWildHunt on 2011-07-03
Ok, some updates.

It seems that my graphics card (hd6870) isn't supported properly by linux open source drivers. Therefore I downloaded the amd cs drivers via command line. However when I try to install the drivers (sudo ati-driver-installer.run) I get the following error:

```
./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.38-8-generic:;make sure the version is being correctly set by --iscurrentdistro

```Any thoughts?

EDIT: Is there a way to change the title of the tread? I think we've narrowed down the problem to the graphics drivers so it would be in order to change it to "Ubuntu (64) driver problems with amd radeon hd6870".

EDIT2: Nevermind. I solved the problem. I used update/upgrade in command prompt and rebootet afterwards. I was then able to get to the desktop via recovery option. Image was still shifted and flickered seizure inducing but I was able to start up Firefox, download the latest amd drivers and install it with terminal. After the reboot everything seems to work as intended. Thanks for the support.

---

### Post by Bucky Ball on 2011-07-03
No problems and good job. Enjoy the learning curve and the OS. ;)

---

### Post by createdcreature on 2011-07-03
Install it from a CD. USB drive never worked for me. Now, let's stop the poem.

---

### Post by Bucky Ball on 2011-07-03
OP, please let us know how you solved your issues so others may benefit from your experience. ;)

---


---
title: "Error with installing Ubuntu 10.10 on a USB"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by RedRooster on 2010-12-10
Hi everyone. I'm new to the forum. 
I have recently been playing around with Ubuntu 10.10 installed on my laptop and enjoying it very much (especially all the cool compiz animation stuff).
 
But I have been trying to find out how to install Ubuntu 10.10 onto a USB.
Now don't get me wrong - I don't want to install it FROM a USB, I want to run it from a USB - From what I've read, a persistent installation.
 
If you have a look at this video - [http://www.youtube.com/watch?v=TZQet3HNm_Y](http://www.youtube.com/watch?v=TZQet3HNm_Y)
 
Which seems quite easy to do, here's where I am having some trouble.
 
I have been able to choose my USB flash drive as the drive for installation, but nowhere did I find and option to select the where to install the boot loader as described in the video at 3:01. 
 
Is this feature not an option in v10.10?
 
This installation completed, but now my laptops OS doesn't boot - I get error message
"error: no such device: f2a5c24-81ca-4056-8cb2-4d432c31c761.
grub rescue>"
 
This doesn't bother me as I was using a test laptop.
 
What I would like to know is - Where during the Ubuntu 10.10 installation can I change the boot loaded installation to the USB?

---

### Post by beew on 2010-12-10
It seems that you have installed the boot loader in your laptop's hard drive. Yes, the option is there, but you have to choose "advanced" in the last step or one of the steps (can't remember which one, as the sequence for 10.10 and 10.04 are a bit different) I have installed both 10.10 and 10.04 into an external drive and a thumb drive so I know it works. However, the flash drive installation is  kind of slow though (much slower than a live usb which runs out of ram) You can make it faster by adding a swap partition and set vm.swappiness=20 or something.

---

### Post by amjjawad on 2010-12-10
While the USB is plugged into your machine (please make sure your BIOS can read it), please post the result of:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Here and don't forget to wrap up the text with "#" or "CODE" tags.

---

### Post by amjjawad on 2010-12-10
> **RedRooster said:**
> What I would like to know is - Where during the Ubuntu 10.10 installation can I change the boot loaded installation to the USB?

I can't remember where exactly (what step) you'll see that option but there must be "advance" button and when you click that, you'll get an option to install the bootloader. I know where it's with 10.04 but I remember 10.10 has a different look.

---

### Post by tajiknomi on 2010-12-10
[SIZE=2]Their is an option "***Boot-loader***" but you forgot that step, theirfore boot is installed on your Hard-drive,Check out the attached pic, and you will see that advanced Option...[/SIZE]

[SIZE=2]That option is at the ***bottom*** of the attached pic.[/SIZE]..

---

### Post by C.S.Cameron on 2010-12-10
> **tajiknomi said:**
> [SIZE=2]Their is an option "***Boot-loader***" but you forgot that step, theirfore boot is installed on your Hard-drive,Check out the attached pic, and you will see that advanced Option...[/SIZE]

[SIZE=2]That option is at the ***bottom*** of the attached pic.[/SIZE]..

You need to choose manual partitioning to get to this step.

---

### Post by tajiknomi on 2010-12-10
> **C.S.Cameron said:**
> You need to choose manual partitioning to get to this step.

[SIZE=2]+1 , i Forgot that step;)[/SIZE]

---

### Post by philinux on 2010-12-10
> **RedRooster said:**
> Hi everyone. I'm new to the forum. 
I have recently been playing around with Ubuntu 10.10 installed on my laptop and enjoying it very much (especially all the cool compiz animation stuff).
 
But I have been trying to find out how to install Ubuntu 10.10 onto a USB.
Now don't get me wrong - I don't want to install it FROM a USB, I want to run it from a USB - From what I've read, a persistent installation.
 
If you have a look at this video - [http://www.youtube.com/watch?v=TZQet3HNm_Y](http://www.youtube.com/watch?v=TZQet3HNm_Y)
 
Which seems quite easy to do, here's where I am having some trouble.
 
I have been able to choose my USB flash drive as the drive for installation, but nowhere did I find and option to select the where to install the boot loader as described in the video at 3:01. 
 
Is this feature not an option in v10.10?
 
This installation completed, but now my laptops OS doesn't boot - I get error message
"error: no such device: f2a5c24-81ca-4056-8cb2-4d432c31c761.
grub rescue>"
 
This doesn't bother me as I was using a test laptop.
 
What I would like to know is - Where during the Ubuntu 10.10 installation can I change the boot loaded installation to the USB?

All you need is the iso file and your usb plugged in. Then System>admin>startup disk creator.

Simples.

---

### Post by tajiknomi on 2010-12-10
> **philinux said:**
> All you need is the iso file and your usb plugged in. Then System>admin>startup disk creator.

Simples.

[SIZE=2]I think he wants to install Ubuntu ***ON*** flash-Drive, not ***from*** flash-drive[/SIZE]:p

---

### Post by amjjawad on 2010-12-10
> **philinux said:**
> All you need is the iso file and your usb plugged in. Then System>admin>startup disk creator.

Simples.


> **RedRooster said:**
> Now don't get me wrong - I don't want to  install it FROM a USB, I want to run it from a USB - From what I've  read, a persistent installation.

:)

---

### Post by 000Mist000 on 2010-12-10
[Deleted Post]

---

### Post by philinux on 2010-12-11
> **tajiknomi said:**
> [SIZE=2]I think he wants to install Ubuntu ***ON*** flash-Drive, not ***from*** flash-drive[/SIZE]:p

Thats exactly what startup disk creator does. Installs ON the flash drive. with persistence as an option.

---

### Post by RedRooster on 2010-12-11
> **tajiknomi said:**
> [SIZE=2]Their is an option "***Boot-loader***" but you forgot that step, theirfore boot is installed on your Hard-drive,Check out the attached pic, and you will see that advanced Option...[/SIZE]

[SIZE=2]That option is at the ***bottom*** of the attached pic.[/SIZE]..

Thanks @tajiknomi! This is what I was looking for :D

---

### Post by beew on 2010-12-12
> **philinux said:**
> Thats exactly what startup disk creator does. Installs ON the flash drive. with persistence as an option.


That is not an installation into a usb, That is a usb with persistence, it is fomatted in FAT, not ext3 or ext4 and it doesn't support kernel updates, installation of proprietary graphic drivers etc. Any change on a system level will break it. It is also limited to 4 G because you can't have more with FAT. To me installing into a usb means a full blown installation like you would in an internal drive, only smaller and portable. :)

This distinction is important for me because I have a few installations like this to test hardware like graphic cards on computers I will install Ubuntu into and I must be able to do kernel updates if needed and install propietary drivers. A live usb with persistence simply can't do the job.

---

### Post by tajiknomi on 2010-12-12
> **RedRooster said:**
> Thanks @tajiknomi! This is what I was looking for :D

[SIZE=2]You are welcome :p,if issue is Solved > you can mark*** thread-as-solved*** in ***thread-tools*** above[/SIZE].

---


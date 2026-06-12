---
title: "Install Error &quot;unable to find a medium containing a live file system&quot;"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by freeprince on 2011-03-06
I have a sony vaio and I have been trying to install ubuntu on it all afternoon using both the proceedures on the ubuntu website and using unetbootin for a usb install. I keep getting the same error.

(initramfs) Unable to find a medium containing a live file system.

I know im not the only one who has this problem though I havent been able to make sense of what specifically is wrong and what needs to be done. 

Sorry if i sound ignorant im a complete noob i admit. Can anyone help remedy this issue for me?

Thanks

---

### Post by Rubi1200 on 2011-03-07
Hi and welcome to the forums :-)

The first thing to do is check the integrity of the downloaded image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by freeprince on 2011-03-08
Hi, i did that and the checksums match. Any ideas as what to do next?

---

### Post by Rubi1200 on 2011-03-08
Did you burn at the lowest possible speed? Is BIOS set to boot from the CD drive and/or USB drive?

How many primary partitions do you have on the computer?

These are the kind of steps to check when working through this.

But, sometimes, you just need to download the image again and burn to a better quality CD.

---

### Post by freeprince on 2011-03-09
Ive been using a USB drive to boot ubuntu, not a cd. The bios settings are all right and Ive tried downloading the ISO a few times. Still getting the same error.

---

### Post by Rubi1200 on 2011-03-09
When you start the computer and try and boot from the USB, what exactly happens?

If you choose the option to try without installing can you get to the live desktop?

If you can, then please do the following:

go to Applications > Accessories > Terminal and run this command:

```
sudo fdisk -lu
```

Copy the results from the terminal and post it here.

What graphics card do you have and how much RAM is installed?

---

### Post by terrox on 2011-03-10
I get these errors too when I try to use Ubuntu from USB. First boot works fine, second boot gets this error.
If I change USB ports sometimes I can get it to load again, but after that it wont load anymore.

I just want to install Ubuntu 10.10 onto a USB drive as a normal install, doesn't seem to be a simple method for that. All the USB boot tools like UNetBootIn just copy a LiveCD to the USB so I have a LiveUSB installer, I'm after a USB OS.

---

### Post by freeprince on 2011-03-13
> **Rubi1200 said:**
> When you start the computer and try and boot from the USB, what exactly happens?

If you choose the option to try without installing can you get to the live desktop?

If you can, then please do the following:

go to Applications > Accessories > Terminal and run this command:

```
sudo fdisk -lu
```Copy the results from the terminal and post it here.

What graphics card do you have and how much RAM is installed?

So I am using unetbootin from a USB to try installing ubuntu. I select the option, "try ubuntu netbook without installing" ...

-first I get a purple screen that says ubuntu 10.10 with the 4 progress dots underneath it
-then after a moment here's what it says:

Busybox v.1.15.3 (ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a liste of built-in commands.
(initramfs) Unable to find a medium containing a live file sytem
  (then underneath it is a flashing dash for a command prompt)

My sony vaio has 2 gigs of ram.
The graphics card is a "Intel graphics media accelerator 500, with an intel GMA 500 graphics controller, Internal LVDS, External SDVO" 762mb total memory.

---

### Post by freeprince on 2011-03-15
Any ideas anyone? I even tried using the desktop ISO.

---


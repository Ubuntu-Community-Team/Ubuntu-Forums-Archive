---
title: "Problem with installation"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by UUUnicorn on 2011-05-08
Hello, ev'ryone; how're you? I'm a new newbie here. Happy Springtime, and Happy Mums' Day. :)

Please, I have an MSI Wind netbook (U100-432US) with Windows XP Home Edition installed on the internal hard drive. I had Linux Mint 9 Xfce "Isadora" installed on a portable external hard drive.

I tried to install Xubuntu 11.04 "Natty Narwhal" onto the external hard drive to replace Mint entirely.

Now, after the first screen showing the MSI logo and the options to either press the Del key to enter "Setup" or F11 to enter "Boot Options", I get a black screen with white type stating the following:

error: no such device: e7448157-337c-4d39-a108-d8670930fd85.
grub rescue>

:(

I very much appreciate any and all advice and help. Thank you very much, and I apologise if I've eradicated my netbook.

---

### Post by candtalan on 2011-05-08
> **UUUnicorn said:**
>  Now, after the first screen showing the MSI logo and the options to either press the Del key to enter "Setup" or F11 to enter "Boot Options"

Hi, and Welcome!

I am not clear about this - did you press the F11 'Boot Options' and choose usb drive?
The error message suggests that on the face of it the drive with the installation on it cannot be seen during the boot process.

---

### Post by UUUnicorn on 2011-05-08
Okay--I mistakenly had the external hard drive unplugged from my netbook. I plugged it back in.

Pressing F11 again, I tried to boot into the internal hard drive (where Windows XP is). This is what the screen showed:

error: no such device: e7448157-337c-4d39-a108-d8670930fd85.
grub rescue>

I decided to try rebooting, this time booting into the external hard drive (where I tried to install Xubuntu 11.04). This is what the screen showed:

                GNU GRUB version 1.99~rc1-13ubuntu 3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

---

### Post by UUUnicorn on 2011-05-08
I've decided to try again to install Xubuntu 11.04 onto my external hard drive. Hopefully, this will correct when I power on/boot up my netbook.

---

### Post by UUUnicorn on 2011-05-14
Installation seems to have been successful; however, booting up the computer is weird now.

When the MSI splash screen appears, I press "F11" repeatedly. When the "Boot Options" screen appears, I boot into the external hard drive, even if I want to boot into Windows XP (on the internal hard drive). The next screen after that--which, I believe, is the GRUB bootloader, I select either Ubuntu 11.04 (actually Xubuntu 11.04) or windows.

In order to boot into even Windows on the internal hard drive, I have to have the external hard drive connected. Wish it weren't this way, but I don't know how to fix this now.

---


---
title: "Please help me install Ubuntu Netbook Remix!"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Raazka on 2009-04-26
Hello everyone,

I have a 701-model Asus EEEPC currently running Ubuntu-eee (which was recently changed to Easy Peasy), and am trying to put on a clean install of the latest Ubuntu Netbook Remix.

I created a bootable USB key without trouble, and my EEE recognises it and boots from it. However, when I select the "Install" option, after seeing "Loading, please wait..." I end up at a screen saying "BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)" and the prompt "(initramfs)".

Is this part of the actual installation procedure? If so, how do I use it?

Thanks,
Raazka

---

### Post by Grimface on 2009-05-04
The same thing happened to me last night, and it means the install idn't work for some reason.

I re-loaded the Ubuntu image onto my USB key using a different method* and then tried again and this time it got all the way through the install ok.

*First I used a utility called "Unetbootin" for windows, which I'd previously used to load ISO images onto USB. The second, [successful method]("https://help.ubuntu.com/community/Installation/FromImgFiles") was using a command-line on my Apple iMac.

Hope that helps.

---

### Post by theozzlives on 2009-05-04
> **Grimface said:**
> The same thing happened to me last night, and it means the install idn't work for some reason.

I re-loaded the Ubuntu image onto my USB key using a different method* and then tried again and this time it got all the way through the install ok.

*First I used a utility called "Unetbootin" for windows, which I'd previously used to load ISO images onto USB. The second, [successful method]("https://help.ubuntu.com/community/Installation/FromImgFiles") was using a command-line on my Apple iMac.

Hope that helps.

Unetbootin should work fine, what problems are you experiencing?

---

### Post by Raazka on 2009-05-05
Grimface and thozzlives, I loaded the image onto the disk using the usb-imagewriter, if that helps.

I guess that I'll try the command line, and unetbootin if that doesn't work, and see how that goes.

Thanks for the help!

---

### Post by jlbr21 on 2009-05-17
So what happened in the end? Im having the exact same problem and have not been able to solve it.

---

### Post by Raazka on 2009-05-17
As of yet I'm still trying different utilities to create the USB startup disk. I've already tried the usb-imagewriter and unetbootin, and I'm stuck for a while. I wonder if the problem is that the image available for downloading is an .img file, and the diskwriters are set up for .iso files.

I'll keep trying, but it may be a while before anything works.

---

### Post by beast-o on 2009-05-20
I've also had this problem. 
I've recently bought an acer aspire one netbook which came linpus lite preloaded.  I've found this to be very restrictive and I've been trying to put ubuntu net remix on the netbook, however I'm hitting my head against a wall in how to get round this problem. I've used the Unetbootin to put the image file onto a usb pen. I'm a total novice with linux and I've no idea whats going on or how to fix this.

---

### Post by lainen on 2009-05-22
I've also tried to install Ubuntu Netbook Remix from a USB-stick and gotten the same "error". The computer i've tried to install it on is an Acer Aspire One ZG5/AOA150.

There's no problem installing Ubuntu 9.04 Desktop on it from a USB-stick but the Netbook Remix always halts with the following info on screen:

"Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)"

I used unetbootin to create the bootable USB-stick, i'm going to try to create the USB-stick with imagewriter now. We'll see how that goes...

---

### Post by lainen on 2009-05-22
For me it worked fine when i created the bootable USB-stick on Ubuntu 9.04 with Imagewriter. I tried to create it 4 times with Unetbootin on Windows XP (with different USB-sticks) and never got it working that way.

Strange but atleast it works for me now.

---

### Post by desertdog on 2009-05-30
Same problem here on a eee 701.

---

### Post by Raazka on 2009-07-11
Well, I finally installed UNR on my EEE. I completely uninstalled usb-imagewriter on my desktop (which is running 9.04), reinstalled it and wrote the image to the USB. This time it worked, so far it looks fine.

---

### Post by killabee44 on 2009-09-04
Guys,

I am having the exact same problem. No matter how many times I reinstall imagewriter, it still won't work. If anyone can help it would be appreciated. Thanks.

---

### Post by Raazka on 2009-09-04
Does anyone know why it's so difficult to write usable usb images?

---

### Post by killabee44 on 2009-09-04
Sad. I ended up resorting to a windows machine to format the flash drive :). Worked great though. Used a program called Win32Diskimager. You can get it here:

[https://wiki.ubuntu.com/Win32DiskImager](https://wiki.ubuntu.com/Win32DiskImager)

---

### Post by pjcdawkins on 2009-10-29
The USB stick must first be formatted (fat16 or fat32) before running Unetbootin

---

### Post by amphore on 2010-12-27
problem solve for me using ubuntu-10.10-netbook-i386 using Aspire One 8.9"

i got the same error as you.


first you can try: copy the iso with the software to usb key directly from a port on your mainboard. usualy where you plug your keyboard and mouse.. not the extension on your front panel.

i first burn the iso with unetbootin-windows-377.exe and **got the error**.

now updated the software to unetbootin-windows-494.exe **_and now working_**

also try another software (Universal-USB-Installer-1.8.2.0) and got error too.

I hope it can help some of you

---

### Post by ubaidillah on 2010-12-27
> **Raazka said:**
> Hello everyone,

I have a 701-model Asus EEEPC currently running Ubuntu-eee (which was recently changed to Easy Peasy), and am trying to put on a clean install of the latest Ubuntu Netbook Remix.

I created a bootable USB key without trouble, and my EEE recognises it and boots from it. However, when I select the "Install" option, after seeing "Loading, please wait..." I end up at a screen saying "BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)" and the prompt "(initramfs)".

Is this part of the actual installation procedure? If so, how do I use it?

Thanks,
Raazka

Same problem here when installing Ubuntu Netbook Remix into Lenovo S10-3 laptop. I found this link [http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html](http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html) from google search. Let us know when it's work

---

### Post by jasonodoom on 2010-12-27
No its not part of the installation.

---


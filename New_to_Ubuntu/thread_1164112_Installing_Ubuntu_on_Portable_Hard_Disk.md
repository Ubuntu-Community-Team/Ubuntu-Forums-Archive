---
title: "Installing Ubuntu on Portable Hard Disk"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-05-19
Hello
I just wanted to ask that if it is a good idea to install Ubuntu 8.10 on a 320GB Portable Hard Disk which uses only one USB cable to connect to the computer and is there any problems with doing this.

---

### Post by shadow120 on 2009-05-19
as long as your pc can boot from usb it should work

---

### Post by Crandom on 2009-05-19
It's absolutly fine - just install as you normally would; I have installed ubuntu on a 500Gb external usb hard drive tens of times with no problems. Obviously, performance will be slightly worse than on an internal hard drive, but this is hardly anything to worry about.

And why 8.10? Ubuntu 9.04 is out and is **far, far, far** superior to the previous version - it's much faster, has ext4 support and generally has less bugs/crashes less and has greater hardware support.

I you plan to do this so you can use it on multiple computers, you may have trouble with some of the configurations as the hardware changes for each use (particularly with graphics and wifi drivers).

---

### Post by ChrisB111 on 2009-05-19
I am currently posting from my 120gb hard disk and it works fine. There are a few things you should think about before installing though.
[LIST]
[*]Can your computer boot from usb (most new ones can but I have to use a floppy to boot mine)
[*]Make sure you know how you are going to partition (split up) your hard drive as you probably will want a bit you can use with windows.
[*]Install it carefully if you don't want to override you computers BIOS with Grub.
[/LIST]
I would do some surfing on the net to find out more or wait until someone more knowledgeable than me comes along.

Chris

---

### Post by mosaabJ on 2009-05-19
And does installing Ubuntu on Hard disk formats everything on it

---

### Post by louieb on 2009-05-19
> **mosaabJ said:**
> And does installing Ubuntu on Hard disk formats everything on it
It can - you can get it to use the whole drive or just a part of it. 

One word of caution about installing on an external drive. Ubuntu by default will put the GRUB stage1 program in the MBR of the internal drive. What that means is the external will have to be plugged in when you boot or the machine will get a GRUB error.

To get around that - on the installation summary screen there is an advance button. By clicking it you can tell the installer to put the GRUB stage1 in the MBR of the external drive.

---

### Post by mosaabJ on 2009-05-19
Sorry i didn't understand you alot. Do you mean that if installing Ubuntu the normal way will it mean that the My machine will not boot unless my Hard disk is plugged.

---

### Post by Astarroth on 2009-05-19
> **mosaabJ said:**
> Sorry i didn't understand you alot. Do you mean that if installing Ubuntu the normal way will it mean that the My machine will not boot unless my Hard disk is plugged.

That is correct. The External hard drive will have to be plugged in unless you tell the grub to install to the external drive.

---

### Post by mosaabJ on 2009-05-19
Okay I get it now now thank you

---


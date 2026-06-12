---
title: "Welcome? screen is dead"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by Jonalt on 2011-05-06
Hi
I want to try out Ubuntu 11.04 on a 8GB usb stick. I boot from the stick and get a black screen with ubuntu written in the middle. Underneath there are 5 dots that change from white to red and back again. Eventually, they are just red. Nothing else happens and I can't do anything except move the mouse around!. I have to switch off the PC and boot Windows.
I would be grateful of help.

---

### Post by computerandu on 2011-05-06
> **Jonalt said:**
> Hi
I want to try out Ubuntu 11.04 on a 8GB usb stick. I boot from the stick and get a black screen with ubuntu written in the middle. Underneath there are 5 dots that change from white to red and back again. Eventually, they are just red. Nothing else happens and I can't do anything except move the mouse around!. I have to switch off the PC and boot Windows.
I would be grateful of help.



I guess its a very general problem with Ubuntu 11.04 installed with a usb stick...i had the same problem and i see many people on the forum having the same trouble...

well the quick and dirty solution is to burn the iso on a dvd and reinstall it...(the same iso which doesn't work on usb works on cd...strange...but true..)

---

### Post by Jonalt on 2011-05-06
Thanks for reply.
However, I just put the iso image onto a _**CD** _and the outcome was **exactly** the same.

Could it be because I didn't use the checksum and there is a fault? [Seemed complicated.]

Or, could it be that part of my pc doesn't like ubuntu? 

Also, I put Mint onto a DVD and tried it, and exactly the same thing happened.

I put Puppy onto a usb drive the other day, and it seems fine.
Further help needed!

---

### Post by Rubi1200 on 2011-05-06
It might also be a graphics issue. What card do you have installed?

It is also worth checking the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Jonalt on 2011-05-06
The details of my Graphics Card are:-

PLE1900WS (1024x768@75Hz)
256MB CONNECT 3D RADEON X700 (Connect3D)

I hope this helps you to help me!

---

### Post by Rubi1200 on 2011-05-06
Well, this page doesn't specifically mention your card, but you should take a look anyway at general requirements for Unity and 11.04:
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

Now, take a look at this post for how to set options as you boot from a LiveCD:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Start with the nomodeset option and see if that helps.

---

### Post by Jonalt on 2011-05-06
I have just checked the MD5 checksum of the downloaded iso file and it is **correct**.

---

### Post by Jonalt on 2011-05-06
Thank you very much.
[http://ubuntuforums.org/showpost.php...97&postcount=1]("http://ubuntuforums.org/showpost.php?p=10069997&postcount=1")   had the answer. I selected nomodeset as you suggested and it worked! I'll try the same procedure with the usb drive and see if it works. I'll put the result on this thread later. It is now time for tea!

---

### Post by Rubi1200 on 2011-05-07
Okay, that is good news. Let us know if you need any other help.

---

### Post by Jonalt on 2011-05-07
The same procedure did **not** work on the usb drive. If I install ubuntu 11.04 alongside my Windows XP to try it out, will I have the same problems? Also, if I decide I don't like Ubuntu can I remove it from my hard drive without affecting the XP OS?
As a newbie, would I be better off using the version you [Rubi1200] use? ie 10.04?

---

### Post by rx007 on 2011-05-07
Well if the latest version doesn't work out for you, try the previous stable one here.

[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

it maybe one of your hardware driver isn't working. :)

---

### Post by Rubi1200 on 2011-05-07
> **Jonalt said:**
> The same procedure did **not** work on the usb drive. If I install ubuntu 11.04 alongside my Windows XP to try it out, will I have the same problems? Also, if I decide I don't like Ubuntu can I remove it from my hard drive without affecting the XP OS?
As a newbie, would I be better off using the version you [Rubi1200] use? ie 10.04?
Hmm, I am surprised it didn't work with the USB.

I am assuming you have not installed Ubuntu to the hard-drive and are just testing the live versions right?

I think there are a few options available to you:

1. if you have enough disk space and RAM, consider installing something like VirtualBox on Windows and run Ubuntu as a virtual machine. For best effects, you need at least 2GB of RAM.

2. install Ubuntu **inside** Windows using Wubi. The advantage of Wubi is no worries about partitioning and, unlike virtualization, it has direct access to all your hardware including graphics.

3. I am not sure if there is such a thing as better for a newbie. I use 10.04 because it is an LTS release, meaning it is supported with updates for a longer period than other releases. And, I prefer stability over bleeding edge, but that is just a personal choice.

Finally, if you install Ubuntu on the drive you need to be aware of a few things:

1. its bootloader will control the boot process. If you remove Ubuntu you will need to restore the Windows bootloader.

2. for fine-grained control, it is best to use the option of manual partitioning when installing. Plan ahead of time and know how much space to devote to Ubuntu and what the partition designation is before starting (e.g. sda5)

3. in theory, if you install to the drive and later remove the Ubuntu partition nothing can happen to Windows. However, always make backups before making major changes to your setup and make sure you have the Windows and Ubuntu CDs available in case you need them for repair/recovery.

These links will show you more and hopefully prove useful:
[http://www.virtualbox.org/](http://www.virtualbox.org/)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Jonalt on 2011-05-07
Yes... this is correct:-
*"I am assuming you have not installed Ubuntu to the hard-drive and are just testing the live versions right?"*
Thanks for help.

---


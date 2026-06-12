---
title: "Ubuntu on a computer for children - with minimal administration"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by quitenewbie on 2008-12-04
Hello, 

For some years i've been the "local tech support"-guy and with all the viruses and trojans on Windows it's become less and less interesting. 

So i got a request to set up a computer for some dangerous children. But i really do not want to mess around with Vista and problems such as virus, trojans and spyware so i'm considering ubuntu.

What I hope ubuntu can provide for me is:

1. Minimal administration - i really hope there is no need to touch the computer after initial setup for let's say max 2 times a year. This then naturally includes the possibility of updates being installed 

2. No problems in terms of regular users (the children) being able to mess up the entire system - messing up only being limited to their own accounts. 

And if the messing up of a user account can set it to a state of it being unusable - some easy way of restoring/resetting the account settings.

Can Ubuntu be the salvation for this task? I know windows certainly isn't.

---

### Post by malathion on 2008-12-04
Yes, ubuntu can potentially solve these problems for you.

But, if you are not already familiar with linux, then it will be a learning experience to figure it out at first. If you are not already running it yourself, I would suggest installing it so you can get yourself acclimated. Good luck!

---

### Post by nakama85 on 2008-12-04
Yes ubuntu would be prime for this. Furthermore it is highly unlikely that these "dangerous children" as you put it would be able to mess the system up. Unless they have Linux knowledge and access to a live cd. However Listen to those who spoke before me. It will be a challenging experience for yourself if you don't have any knowledge of ubuntu (linux). The key to remember is to take your time and do it right.

---

### Post by quitenewbie on 2008-12-04
thanks alot for reassuring answers. Are there any guides for how to harden ubuntu - e.g. remove some programs or change settings before i unleash it to them?

---

### Post by nakama85 on 2008-12-04
> **quitenewbie said:**
> thanks alot for reassuring answers. Are there any guides for how to harden ubuntu - e.g. remove some programs or change settings before i unleash it to them?

Just remember if you ever have any questions take a look at the collective mind within the forums.

Also it may be wise to crosss check the system specs of the computers you will be using with the forums. This way you will be well aware of any problems you may run into. If you do have these problems you are likely to already have the answers to them by doing this.

---

### Post by Elfy on 2008-12-04
There's a link here for bodhi zazen's security page [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

That in itself is peppered with links to more resources. Settle down with a pot of coffee...

---

### Post by Kellemora on 2008-12-04
Hi QN

One thing you MIGHT consider is EDUBUNTU.  It's geared to children in a classroom type environment.  Almost any computer can be connected to EDUBUNTU, meaning using a bare bones cheap thin client instead of a good computer.  You can keep the server locked up inside a desk or cabinet out of the reach of prying fingers.  It wouldn't matter what they did at their own computer since it's nothing more than a dumb terminal.

I downloaded the .iso to help me learn a little bit about how servers work, and EDUBUNTU works right out of the box, all standard settings come already set up as the default condition.  The only thing I added was a GUI so I could see what was going on in a way I could understand it, and use it for other things as well.

You can pick up used bare bones computers for around 50 bucks each or less all over the place.

TTUL
Gary

---

### Post by LowSky on 2008-12-04
> **quitenewbie said:**
> 
1. Minimal administration - i really hope there is no need to touch the computer after initial setup for let's say max 2 times a year. This then naturally includes the possibility of updates being installed 
Yes and no, yes if you turn the automatic security updates. No for only one reason, you need admin rights to install anything. So make sure you know that before getting into anything. most basic programs are installed by default, but a few you may need later, so bear that in mind.

> **quitenewbie said:**
> 2. No problems in terms of regular users (the children) being able to mess up the entire system - messing up only being limited to their own accounts. 
only if they have root access ( sudo) if they don't your ok you can install anything without sudo in Ubuntu

> **quitenewbie said:**
> And if the messing up of a user account can set it to a state of it being unusable - some easy way of restoring/resetting the account settings.
when you install creat a seperate /home partition, this way all the data is stored to a seperate part of the hard drive, this way if the install goes bad, all they files are stored on a serate and safe part of the drive. You can even create a way to back up that partition if you like...

---

### Post by Paqman on 2008-12-04
> **quitenewbie said:**
> thanks alot for reassuring answers. Are there any guides for how to harden ubuntu - e.g. remove some programs or change settings before i unleash it to them?

It's not really difficult enough to need a guide, IMO.

Linux is designed from the ground up as a multi-user system, unlike Windows which was a single-user system that had multi-userness thrust upon it.

If you create a user account that doesn't have admin privileges they will be unable to run (or even see) any of the admin programs, and they cannot write to any file or folder outside of their /home folder. So their ability to cause any damage is very minimal. They're basically sandboxed. I would advise installing /home to a seperate partition, as this will effectively act as a disk quota, and stop excessive user downloads from maxing out the disk and affecting the system side.

I'd advise setting security updates to happen silently, but decline any further updates. Using Ubuntu 8.04 (which is a Long Term Support release) that will result in a very stable system. Only security updates will happen, and it'll all happen behind the scenes. 8.04 security updates will continue until April 2011, after which you can upgrade to the next LTS version and start the cycle again. Potentially you'd only need to touch the system every three years to upgrade between LTS's.

One tool you may want to take a look at is startupmanager. It'll let you take some further steps like removing the recovery mode (which boots into an admin console) from the GRUB bootloader. I'd also password lock the BIOS and make sure they can't boot from the optical drive or USB, otherwise they could use a LiveCD or LiveUSB to get into the system.

---

### Post by LowSky on 2008-12-04
> **Paqman said:**
> 
One tool you may want to take a look at is startupmanager. It'll let you take some further steps like removing the recovery mode (which boots into an admin console) from the GRUB bootloader. I'd also password lock the BIOS and make sure they can't boot from the optical drive or USB, otherwise they could use a LiveCD or LiveUSB to get into the system.

Actually a good idea, I wouldn't remove recovery mode though, note you can also passowrd protect grub, which would be more  helpful if you really need recovery mode.

---


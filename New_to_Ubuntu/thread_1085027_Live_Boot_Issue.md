---
title: "Live Boot Issue"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by King Roach on 2009-03-02
Hi,

I've encountered a right problem with using the Ubuntu 8.10 Live Boot CD.

Basically I downloaded the image from Ubuntu's site, burnt it and it works perfectly, was able to run Ubuntu first time no problem. 

However, whilst using Ubuntu OS it crashed out when I tried to open a .txt file, (which is 100% certified to be virus free incidentally), I think I may have just had a little too much running at one time. This resulted in a complete system freeze where I had no alternative but to manually turn off my pc. This caused no problems and my Windows XP SP2 OS still boots and works fine.

The thing is... now Ubuntu won't boot from the CD any more! It gets to about 80-85% through the loading bar and then freezes and the CD stops.

I have tested the CDs integrity and it's fine, I've tried running the boot disc through both of my CDROM drives and I get the same problem. It seems as though it has corrupted some kind of temporary file that it may have installed (temporarily stored) when I ran (and then crashed) the Linux OS the first time.

Is there anyway that I can flush all traces of Ubuntu and Linux from my pc, from within Windows XP, in order to run the live CD again? As I think that this may be the cause.

Incidentally, I do not have room on any or my HDDs in which to install Linux at present. So a boot CD is my only option and is essential for my university work.

Any suggestions would be much appreciated.

---

### Post by RetchingRabbit on 2009-03-02
> Is there anyway that I can flush all traces of Ubuntu and Linux from my pc, from within Windows XP, in order to run the live CD again? As I think that this may be the cause.
If you didn't install Ubuntu to your hard drive, there is nothing to remove. It DOES NOT write to the hard drive. If you want to remove all traces, power off your machine for a few minutes. That should clear the ram.
That said, I think your problem lies elsewhere. 
Perhaps if you could post the output of ```
lspci
``` we could have a look at your hardware....

---

### Post by Ben Crisford on 2009-03-02
So you have started installation I assume?

Thats not good, but on ubuntu I can access my windows partition, so I assume it may work the other way around.

Have a look round on the C:\ drive.  Be sure to view hidden folders and be careful not to delete any important files!

---

### Post by TJCIB on 2009-03-02
You could use a LiveUSB instead of CD, then it would save your files and keep your settings...if you used the persistent mode.

Most computers these days can boot from USB, and if not there are way around that problem too...

[http://www.pendrivelinux.com]("http://www.pendrivelinux.com") has everything you need for that task.  It is VERY easy with 8.10.

---

### Post by King Roach on 2009-03-02
Firstly thank you guys for your advice.

In response, I can't run lspci, as correct me if I'm wrong as Im new to Linux, but isn't that a Linux until? As the problem is that I can't access Ubuntu I unfortunately can't try this to give you a full spec. However I can tell you what I'm running:

Windows XP Pro SP2
AMD Athlon 64 2Ghz
1GB RAM
Geforce 6600 AGP
225GB of mixed SATA and ATA HDD
Am not using any other PCI devices other than a USB addon that came with the motherboard.

As for looking through my C:\ drive, etc, I've done this and can't see anything untoward. But I didn't try installing Ubuntu, simply ran it from the CD.

I heard rumours of Ubuntu creating a micro partition somewhere is it what lead me to believe that it may have got corrupted some how, but could only see ways to access this through Linux, which is obviously not possible right now.

I'm going to go and try running Linux from a USB now, fingers crossed.

---

### Post by TJCIB on 2009-03-02
The LiveUSB should work well.  I find it much more comfy to take a picture of my son as my desktop everywhere I go instead of the generic LiveCD theme...

If you have questions, feel free to message me.

---

### Post by egalvan on 2009-03-02
> **King Roach said:**
> 
I heard** rumours** of Ubuntu creating a micro partition somewhere is it what lead me to believe that it may have got corrupted some how, but could only see ways to access this through Linux, which is obviously not possible right now.


**rumors** is true.

The LiveCD DOES NOT TOUCH THE HARD DRIVE unless you tell it to.

That said,

did you confirm a good download with the md5sum?

did you burn the cd at a low speed (4x-8x)?
higher speed burns can be problematic.

did you run the "check media for errors" boot option?

Have you tried making another cd?

We can go from here.

---

### Post by King Roach on 2009-03-02
I've since tried a USB boot stick idea and the progress of Ubuntu loading got further than before. It managed to finish the loading bar and then sat at a blinking cursor in the top left corner and didn't get any further. Did all the installation as per the instructions, but will repeat this again tomorrow.

> **egalvan said:**
> **rumors** is true.

The LiveCD DOES NOT TOUCH THE HARD DRIVE unless you tell it to.

That said,

did you confirm a good download with the md5sum?

did you burn the cd at a low speed (4x-8x)?
higher speed burns can be problematic.

did you run the "check media for errors" boot option?

Have you tried making another cd?

We can go from here.

I've checked the media for errors and it came out fine. However I will burn it at fresh cd to ensure slow burn speed and such. 

Thank you for all of your suggestions.

---

### Post by TJCIB on 2009-03-04
You may want to reconsider downloading the .iso again and checking the m5dsum just to be sure.

If the .iso is the problem, it doesn't matter what you do, it won't work.  I would try a new one.

---

### Post by egalvan on 2009-03-05
OK, if the "check media for errors" boot option said you had a good
CD, then it 99.99% you have a good CD.

We can basically eliminate that problem.

One more thing to try from the boot options...

memtest


let it run at least 24 if possible.
if not , then give it overnight.

And before you say "but Windows runs OK on this machine"
realize that Microsoft products are NOT a good indicdator of bad hardware.
I speak from painful, time-wasting experience on this.
I have had defective CD drives, hard drives, RAM and cables...
ALL of which Microsoft happily ran on....
but Linix crashed.
So TEST THAT HARDWARE.

(at the moment I have a Dell GX280, P4 @ 2.8, 512M.
I can install Ubuntu 8.04.2 just fine, but when I do ANYthing at the desktop, it crashes.
It will sit all day, no problem.
Command-line runs all day, no problem.
Click on the desktop, and ka-boom.
Go figure)

---


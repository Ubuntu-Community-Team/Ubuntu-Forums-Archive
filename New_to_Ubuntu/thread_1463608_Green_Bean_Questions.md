---
title: "Green Bean Questions"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by wgh87 on 2010-04-27
Hi there,
 
I'm a long term user of windows fill with virus, trojan, etc. and I was thinking about jumping over to ubuntu. Since my computer is very old and probably won't handle the new windows.
 
My specs
CPU: P4 3ghz
Ram: 2gb DDR
GPU: 9200se 256mb AGP
HDD: 500Gb IDE
 
Will it take long to start up?
Will it run videos such as divx, flv, rmvb, without any problems?
Does it have something similar to a windows IMEpad?
Can it run the same software that I use in windows? office, flash, acobat, etc.
 
Do you recommend that I switch?
 
Thanks for the help!

---

### Post by CharlesA on 2010-04-27
Ubuntu should run fine.

There are office apps, pdf readers and (mostly working) flash.

I don't know about divx or any of the other codecs, but there probably are some written for Linux.

Just keep in mind that Linux is not Windows, then download a livecd and try it out to see if you like it.

---

### Post by 3rdalbum on 2010-04-27
> **wgh87 said:**
> Hi there,
 
I'm a long term user of windows fill with virus, trojan, etc. and I was thinking about jumping over to ubuntu. Since my computer is very old and probably won't handle the new windows.
 
My specs
CPU: P4 3ghz
Ram: 2gb DDR
GPU: 9200se 256mb AGP
HDD: 500Gb IDE
 
Will it take long to start up?

No, Ubuntu 10.04 is very fast to start.

> Will it run videos such as divx, flv, rmvb, without any problems?

All those file formats you have mentioned are patented. Ubuntu will play them if you install the "ubuntu-restricted-extras" package and the "w32codecs" package from Medibuntu.org's repository. This will make more sense to you when you're running Ubuntu.

I'm assuming that your Realvideo files are not DRM-encrypted; that's a showstopper. But it's unlikely that you've got any of those unless you've used an online music store a few years ago.

> Does it have something similar to a windows IMEpad?

Many of us don't use Windows and so don't know what it is you're referring to. Could you explain what it is?

> Can it run the same software that I use in windows? office, flash, acobat, etc.

Flash Player and Acrobat Reader are available on Linux. Ubuntu comes with Openoffice.org which is compatible with Microsoft Office files, and has probably 90% of the features.

**Don't expect Windows software to run**, this is a different operating system entirely. You may be able to run SOME Windows software using a program called Wine, but I'd highly recommend adopting Linux-native software instead of trying to use your existing programs in Wine. **Wine is a last resort**.

As for whether I think you should switch, well I don't know your circumstances, but your questions haven't shown anything that's really keeping you on Windows. It's not an all-or-nothing question either - the Ubuntu installer will give you the option of "dual-booting" - that is, installing Ubuntu alongside Windows so you can boot into either one.

I dual-booted for almost two years while I waited for video editing and conversion to become usable on Linux. When it was ready, I removed Windows. My father still dual-boots.


EDIT: Just an advance warning for you. ATI doesn't support your graphics card anymore, and as such there are no official Linux drivers for it. However, the Linux community still cares about your card, and when you start Ubuntu you will be using the open-source driver that the community has developed for it. You might find that the 3D desktop effects won't work, or that 3D games won't work; but we're still working on it. It's enough to get you started anyway. On the upside, at least you don't have the bother of installing a driver for it - the open-source driver is activated by default.

---

### Post by ubunterooster on 2010-04-27
Your specs are fine but Xubuntu and Lubuntu are better for older systems, I reccomend you see which one you like. :)

For all newcomers: due to 64-bit's not having flash by default, you need to install it manually.

---

### Post by fromthehill on 2010-04-27
your hardware is definitely fast enough to run ubuntu

the best way to check if your graphicscard is supported is to run the livecd and check if ubuntu can find any drivers with system > administration > hardware drivers (you can't install them on a live cd as you need to restart the system)

I'd just stick with the 32-bit(default) version to be sure things like flash work properly
version 10.04 will be out in 2 days if you want the newest software

---

### Post by coffeecat on 2010-04-27
> **ubunterooster said:**
> Your specs are fine but Xubuntu and Lubuntu are better for older systems, I reccomend you see which one you like. :)

The OP has a 3GHz single-core processor and **2GB** RAM. Ubuntu/gnome will run just fine with that. No need for a lightweight desktop unless the OP prefers one.

---

### Post by Crazedpsyc on 2010-04-27
Just keep in mind when trying the live CD, it will be much faster when you run it from your hard drive! 
OOo (OpenOffice.Org) is definitely the best Office alternative, and it as well as a pdf reader come installed. 
just open those videos with totem (comes installed) and it should be able to find a suitable plugin to play them.
I have had huge issues with various flash runners, but found the Adobe Flash Plugin in the repositories, and it works great! (if you use Mozilla) open System>Administration>Software Manager
and it should install no-prob

---

### Post by philinux on 2010-04-27
> **ubunterooster said:**
> Your specs are fine but Xubuntu and Lubuntu are better for older systems, I reccomend you see which one you like. :)

For all newcomers: due to 64-bit's not having flash by default, you need to install it manually.

His specs are fine for regular Ubuntu.

It has 32 bit flash by default, which can be buggy. The Manual install of 64 bit is the way to go.

And manual install means downloading one file extracting one file and moving it to the appropriate folder. Simples.

---

### Post by mal1958 on 2010-04-27
> **ubunterooster said:**
> Your specs are fine but Xubuntu and Lubuntu are better for older systems, I reccomend you see which one you like. :)

For all newcomers: due to 64-bit's not having flash by default, you need to install it manually.

Just to let you know, My system is older then his and I have Ubuntu 9.10 installed with no lag or problems.  


[LIST=1]
[*]P3 1 gig
[*]512 meg ram
[*]2 60 gig HD
[*]Invidia GeForce 6200 AGP
[*]SB Audigy sound card
[*]Lite-On CD-RW
[*]DvD rom drive
[/LIST]
  I am running a dual boot system with Windows XP on the primary and Ubuntu Karmic Koala on the second drive.  No problems and I notice no lag, on the Ubuntu side, Windows is another matter, though.  

   With the specs you gave I would think that straight Ubuntu would be fine.  Or you could even try Kubuntu if you want the KDE version. 

Mike

---

### Post by maizuddin35 on 2010-04-27
Your computer will be run just fine. with ubuntu.There will no problem at all. If there is, feel free to ask us here.
My laptop, had tried Linux mint helena, ubuntu jaunty,
and now Im running with xubuntu 9.10 and im loving it because it fast and lightweight.
My laptop spec is 512 mg ram, 40gig hadisk, Intel pentium 1.6ghz.
and it run just great.:D
If you install xubuntu, it will not have openoffice install but abiword.But still you can install openoffice from the Add/Remove Application.

---

### Post by norm7446 on 2010-04-27
With this spec, I would say that you could run all and more of the Windows Aero aspects of an Ubuntu set up with comipz fusion, no probs. As per boot up if you wait another few days for the Final Releace of Lucid Lynx, you will be more upto date than Windows7 which is still waiting for SP1.

---

### Post by wgh87 on 2010-04-27
Thanks guys,
 
Just an explation about the windows IMEpad, it's just a language program that allows you to write asian character and it will recognise.
 
Also there is alot of linux os, whats the different, and which one is the best for entertainment/mild gamming

---

### Post by ubunterooster on 2010-04-27
Um, Ubuntu is best because of the large community. I'm not sure which to use as a gamer...I'm going to install Debian soon. Sabayon is very good once set up. This kind of question leads to marathon threads.

Assuming you have the answer, it would be helpful if you mark the thread as solved.

I've tried nearly 40 different flavors and like debian based distros. Fedora's .rpms still needed work last I checked, I don't like SUSE's YAST, and slackware takes a while to configure. Get the following via synaptic, xubuntu-desktop, lubuntu-desktop, and kubuntu-desktop. log out. When you go to log back in you can click the "sessions" menu and choose one of the choices. I prefer xcfe. Not a different distro, but still a very different feel.

---


---
title: "Intel 845G Screen Resolution"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Fleetwood on 2011-03-24
Hello all,

Firstly, I must state that I am new to Linux / Ubuntu (this is my first day of using it) but I am competent with Mac OS / Windows and am willing to learn!

I am testing Ubuntu 10.10 Maverick Meerkat 32-bit on an old eMachines 3230 desktop PC which has the following specification:

CPU: Intel Pentium 4 2.8GHz
Motherboard: MS 6714 Ver. 5
Graphics: Intel 845G (Integrated)
     RAM: 512MB PC2700

I do not have a standalone monitor as my main computer is a laptop, which I connect to a 47" LCD TV when required. I am currently using the 3230 with that TV but can't adjust the resolution above 1024x768 pixels, which as you can imagine, is not ideal with a 47" screen.

Now, I can imagine that my choice of motherboard is not ideal in terms of support, and am fully expecting to have driver issues. The question is: How do I increase the screen resolution to enable me to test-out the operating system properly with multimedia applications?

Any help will be much appreciated,

Fleetwood

---

### Post by coffeecat on 2011-03-24
Hi, and welcome to the forum.

> **Fleetwood said:**
> 
Now, I can imagine that my choice of motherboard is not ideal in terms of support, and am fully expecting to have driver issues.

I regret to say that you are right. This is the problem:

> **Fleetwood said:**
> 
 Graphics: Intel 845G (Integrated)

It's an old graphics chipset. As the xserver (the underpinnings to the GUI) and the Intel driver have been developed to keep pace with newer Intel graphics chipsets, the 8** series have become problematic with the newer version of xserver/driver. More here with the version of Ubuntu that you are using:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

It seems that your system has probably defaulted to the fbdev driver in an effort to avoid system freezes, and this leaves you with only one video resolution - as you have found.

There are a couple of options there - to enable the Intel or the vesa driver - but as you can see there are tradeoffs. If you want to try one or both, the way you create an /etc/X11/xorg.conf file (which is missing in a default installation) is to open a terminal and run:

```
gksudo gedit /etc/X11/xorg.conf
```Be careful to get case right. X11 = capital-X, eleven. A text editor will open with root privileges showing an empty file. Simply copy and paste the text in that link (either the Intel or vesa text - don't use both simultaneously) and save the file, and then reboot.

As you can see, the Intel option may very well lead to system freezes. Also - I once had an Emachine with that graphics chipset in the days when it was better supported in Linux. Even then I was not able to get widescreen resolutions - only 4x3. And I think the same may be true of the vesa driver - although I could be wrong.

An alternative for you is to fit a separate graphics card with a more suitable graphics chipset. Unfortunately, it is difficult to get hold of decent AGP cards these days and it is possible that your motherboard doesn't even have an AGP slot. Mine didn't - I could only fit a PCI (not PCIe) graphics card, and they are nearly impossible to obtain now.

---

### Post by mikewhatever on 2011-03-24
You could try adding different resolutions manually. A 47 inch TV probably has something like 1920x1080, and I have serious doubts a ten year old controller can output something this high. Anyway, good luck, and post an update.
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

---

### Post by Fleetwood on 2011-03-24
coffeecat,

Thanks for the explanation. Luckily, I do have a stockpile of old AGP graphics cards at work...I just need to sit and test them before use - hopefully I can fit one that's better supported (I can confirm that this board does have an AGP slot). - As I am a Linux newbie and am still learning the basics, I don't really think it wise to make modifications to the software that are likely to cause instability...at least until I'm more comfortable with the OS. :wink:

> **mikewhatever said:**
> You could try adding different resolutions manually.

Thanks for the link. :cool: I'll try that in the meantime (as I can't access an AGP card tonight) and post back with the results.

> **mikewhatever said:**
> A 47 inch TV probably has something like 1920x1080, and I have serious doubts a ten year old controller can output something this high.

:lolflag: Yes...it would be silly to expect the old desktop to use the TV to it's full potential - I'm just hoping for something a little higher than 1024x768 so that I don't go cross-eyed looking at the screen!

---

### Post by coffeecat on 2011-03-24
> **Fleetwood said:**
> coffeecat,

Luckily, I do have a stockpile of old AGP graphics cards at work...I just need to sit and test them before use - hopefully I can fit one that's better supported (I can confirm that this board does have an AGP slot). 

That's good news. Rather than you plough through them one-by-one, why not post a list of what you've got? Some of the older legacy nvidia and ATI cards can be challenging, and other makes possibly best avoided, but there should be something there that will work nicely for you.

---

### Post by Fleetwood on 2011-03-24
> **coffeecat said:**
> That's good news. Rather than you plough through them one-by-one, why not post a list of what you've got? Some of the older legacy nvidia and ATI cards can be challenging, and other makes possibly best avoided, but there should be something there that will work nicely for you.

Will do - I can't remember what's there offhand, but I should be able to find something. I realise though that this is an old system. When the current issue with Intel's Sandy Bridge boards is fixed, I intend to build myself a new i7 desktop, so in the worst case scenario I'll limp along with this system until then.

---


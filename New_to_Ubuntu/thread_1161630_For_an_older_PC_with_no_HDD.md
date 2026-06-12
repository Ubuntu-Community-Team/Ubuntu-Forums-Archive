---
title: "For an older PC with no HDD"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by winjeel on 2009-05-16
I've got an older laptop, with a dead hard drive. After taking a look at the local electronics stores here, they don't have any HDDs small enough for it (it is a really small and very slim model from Sharp). I wonder, if I can get a 8Gb USB memory stick (now selling reasonably cheap here), and put on an Ubuntu OS, would that work? If so, which variety?

Oh, it has a 256mb RAM capacity, and all other features are regular, but no internal CD drive. Also, when I try to start it, it comes on, and sometimes it says "Operating System not found" (probably physical damage to the HDD). I've just checked, and USB Boot is 'Enabled'.

As always, thanks in advance.

---

### Post by charliehorse55 on 2009-05-16
For a Pc with those specs - I recommend Xubuntu. If that isn't light enough, you may want to have a look at puppy linux. ([http://www.puppylinux.org/home/overview](http://www.puppylinux.org/home/overview))

You should be able to follow [these]("https://help.ubuntu.com/community/Installation/FromUSBStick") Instructions. 

You might need a second smaller USB stick to install the files onto the larger USB stick. 

Good Luck.

---

### Post by theozzlives on 2009-05-16
I've got a full install of 9.04 on a 8 GB stick with plenty of room for updates and whatnot. People say Xubuntu, Puppy, or DSL but I'm the kinda guy that'll run full blown Ubuntu on 256 MB.

P.S. Question is can your machine boot USB????

---

### Post by winjeel on 2009-05-16
Thanks for the replies.

> **theozzlives said:**
> ...

P.S. Question is can your machine boot USB????

It says that it's "Enabled", so there's only one sure way to find out, I guess.

I'm just about to head into town, and so I'll pick up an 8Gb memory stick and give it a go later in the week (really, ultra busy week this will be). I'll let you know how it went, but I'll give Xubuntu a go, first. :p

---

### Post by Sir Jasper on 2009-05-17
Hi,

Knoppix (linux) will load and configure automatically from a CD or DVD and it does not, I'm 99.99% certain, need a hard drive.

The DVD has 8 GB of compressed programs and will run slower than the CD which will be slower than using a hard drive (except, in the unlikely event you have about 800 MB RAM).

If you are going to use a USB stick, the read and write speed may be important to you (and you will need USB 2 else things will crawl).

My regards

---

### Post by lisati on 2009-05-17
Puppy Linux can be run from CD. I'm not sure if it can be installed on USB.

---

### Post by ugm6hr on 2009-05-17
You'll need 2 USB drives:
1 to boot from (as a LiveUSB) and 1 to install on to.  The former needs to be 1GB, and 8GB should be fine for the latter.

But yes, it should work.

---

### Post by winjeel on 2009-05-18
> **ugm6hr said:**
> You'll need 2 USB drives:
1 to boot from (as a LiveUSB) and 1 to install on to.  The former needs to be 1GB, and 8GB should be fine for the latter.

But yes, it should work.

Interesting you should say that. On this (regularly working computer), I've used WinDisk32Imager to add the 9.04 Notebook remix to the usb memory stick. I've then tried the memory stick straight onto the computer, but got nothing, absolute nada.

So, If I have just the remix (direct from download) on one usb memory stick(stick A), and plug in the one I want everything installed onto and be like a regular HDD (stick B), then start up the computer, I would then be able to install it and get it to work? So, in the future, after installation, I can just use stick B whenever I want to use the computer?

---

### Post by ugm6hr on 2009-05-18
> **winjeel said:**
> So, If I have just the remix (direct from download) on one usb memory stick(stick A), and plug in the one I want everything installed onto and be like a regular HDD (stick B), then start up the computer, I would then be able to install it and get it to work? So, in the future, after installation, I can just use stick B whenever I want to use the computer?

Yes.

Except, NBR requires 386MB RAM to use the LiveCD (I think).

If the USB you installed to actually works, you should still get the initial boot screen.  Getting past that might be harder though...  Try the LiveUSB you created on a fully functional computer to see if it actually works at all (i.e. is it a problem with the USB stick or the computer).

---

### Post by winjeel on 2009-05-19
I want to avoid using a Live CD, as that'd mean that I'd also have to carry an external cd drive with me when I go places, hence the preference for using a usb stick.

I have tried the usb stick on another computer for my first go at it, but it didn't work.

So, just to make clear what I did on both attempts.

First:
1. Downloaded 9.04 notebook remix
2. Used Win32DiskImager to add the freshly downloaded (untouched) 9.04 to a memory stick.
3. inserted the memory stick to the laptop (the one with the broken HDD)
4. Turned on the laptop, but nothing happened. The screen lit up, waited, waited, and waited, then the normal "No Operating System Found" message.

Second:
1. Downloaded another 9.04 notebook remix
2. Copied it freshly downloaded (still warm and untouched) to the memory stick
3. Inserted the memory stick to the laptop
4. Turned on the laptop and again nothing happened.

Though, the normal Sharp start up screen with "Press F2 for Setup" showed. I have tried both attempts above with various start up settings, turning off the HDD, setting it to Auto, and to User. Made sure that USB was set for booting. However, the info displayed said that it can accept FD and CD for booting. Though, I'm not sure if it can use a USB stick inplace of an FD or CD drive. 

Thoughts?

---

### Post by Sir Jasper on 2009-05-19
Hi,

My machine is old and I cannot boot from a USB stick.

Have a look in your BIOS and, if you can, make the setting there.

My regards

---

### Post by Sir Jasper on 2009-05-19
Hi again,

Many older machines, like mine, can boot from a Floppy (which could be more easily carried a pocket, or even stay permanently in its drive).

---

### Post by jerrrys on 2009-05-19
hello Sir Jasper...

i see you found a fix for your aging windows os...

---

### Post by winjeel on 2009-05-21
> **Sir Jasper said:**
> Hi,

My machine is old and I cannot boot from a USB stick.

Have a look in your BIOS and, if you can, make the setting there.

My regards

I've tried that. Is there some bit of software that I might need t add to the bios for it to utilised a usb memory stick?

---

### Post by Sir Jasper on 2009-05-21
Hi,

I think you are probably out of luck with your last question.

My only other thought is:
have you seen the small CDs (about the size of a floppy)?
they do exist (I've had some, advertising products).
No idea, if one would hold enough for your needs;
alternatively  couldn't you leave a normal size CD 
permanently in its drive?

My regards

---

### Post by gn2 on 2009-05-21
> **ugm6hr said:**
> You'll need 2 USB drives:
1 to boot from (as a LiveUSB) and 1 to install on to.  The former needs to be 1GB, and 8GB should be fine for the latter.

But yes, it should work.

Or one big one partitioned....?

---

### Post by Sir Jasper on 2009-05-21
Hi gn2,

As I recall (perhaps wrongly) he didn't want to carry a normal size CD about and he can't (as I can't) boot from a USB stick (partitioned or not).

My regards

---

### Post by fluxlizard on 2009-05-21
If you can boot from the usb stick, you should be able to do a puppy linux install to the stick and run from there. the core of puppy runs in ram, and your settings, customizations, downloads and work will save to the stick automagically for you.

---

### Post by MrWES on 2009-05-21
> **fluxlizard said:**
> If you can boot from the usb stick, you should be able to do a puppy linux install to the stick and run from there. the core of puppy runs in ram, and your settings, customizations, downloads and work will save to the stick automagically for you.

If he as a floppy, he can use Puppy's 'Wakepup' to boot with and then put his pup_save file on the usb stick.

[http://www.puppylinux.com/flash-puppy.htm]("http://www.puppylinux.com/flash-puppy.htm")

Bill

---

### Post by winjeel on 2009-05-21
Thanks for the ideas. I'll check out Puppy Linux later. I've got many things to get to today.

---


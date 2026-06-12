---
title: "Installation Help Needed"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Cliffjam on 2011-05-29
Hello, I would appreciate it if someone could steer me in the right direction or tell me exactly which thread to post my question in.  

I will list all the details I can within this post so that I have it for all to reference (including myself).

I recently purchased a desktop system online without an OS with the intention of putting on either Ubuntu or Kubuntu. I've d-loaded and burned live cd's of 10.4 LTS and 11.04 for both and 9.10 in Kubuntu.  The winMD5Sum's all matched up fine. 

Whenever I try to install, the system locks up after I choose time zones(black screen, sometimes showing a locked-up mouse pointer) though once I managed to get to the User info screen.  If I try without installing, I seem to have intermittent luck.  It will sometimes run for awhile before lock up and sometimes lock up before completing the live, non-install, setup. 

Barebones with AMD CPU (Windows 7 ready)
  w/ Athlon II X3 435 (3 x 2.9GHz - 1.5MB Cache)
  Asus M4A78LT-M
  8GB DDR3-1333 PC3-10600 (2 x 4GB Dual Channel)
  500GB SATA2 - 3gb/sec 7200RPM (16MB Cache) Hard Drive

The Kubuntu 10.4 LTS Live-CD seems to get the farthest along before I run into trouble, but given a choice, I like the traditional Ubuntu more. I was trying both to see which OS would be more intuitive. 

My experience with Ubuntu is limited to version 8 and using live CD's on ancient systems.  I have very little knowledge and understanding of CLI and only once have copied something to do with sudo.

Thanks for reading.

---

### Post by verymadpip on 2011-05-29
If your MD5s are okay you may want to check the disc integrity.  There's an option in the list which has 'try blah' & 'install blah' & the like.

You could also try a USB install rather than CD.  I'd recommend Unetbootin for that.

Do keep us up to date with how things are going.

---

### Post by sanderj on 2011-05-29
@Cliffjam

So even running the live-CD leads to lock-ups? That's bad.

Things to do/check:
- can you successfully run the live-CD in another system? If so, can you create a live-USB-stick in that system, and try the live-USB-stick in your main system?
- can you run Test Memory from the live-CD to check that your memory is OK?

---

### Post by jerrrys on 2011-05-29
makes me wonder if your new cd is giving you grief.

---

### Post by gandaran on 2011-05-29
> **Cliffjam said:**
> Hello, I would appreciate it if someone could steer me in the right direction or tell me exactly which thread to post my question in.  

I will list all the details I can within this post so that I have it for all to reference (including myself).

I recently purchased a desktop system online without an OS with the intention of putting on either Ubuntu or Kubuntu. I've d-loaded and burned live cd's of 10.4 LTS and 11.04 for both and 9.10 in Kubuntu.  The winMD5Sum's all matched up fine. 

Whenever I try to install, the system locks up after I choose time zones(black screen, sometimes showing a locked-up mouse pointer) though once I managed to get to the User info screen.  If I try without installing, I seem to have intermittent luck.  It will sometimes run for awhile before lock up and sometimes lock up before completing the live, non-install, setup. 

Barebones with AMD CPU (Windows 7 ready)
  w/ Athlon II X3 435 (3 x 2.9GHz - 1.5MB Cache)
  Asus M4A78LT-M
  8GB DDR3-1333 PC3-10600 (2 x 4GB Dual Channel)
  500GB SATA2 - 3gb/sec 7200RPM (16MB Cache) Hard Drive

The Kubuntu 10.4 LTS Live-CD seems to get the farthest along before I run into trouble, but given a choice, I like the traditional Ubuntu more. I was trying both to see which OS would be more intuitive. 

My experience with Ubuntu is limited to version 8 and using live CD's on ancient systems.  I have very little knowledge and understanding of CLI and only once have copied something to do with sudo.

Thanks for reading.
you don't mention the video card, what brand and model of video chip? maybe the problem is due to the Linux drivers for the card.

---

### Post by Cliffjam on 2011-05-29
First of all, thank you for the replies.

The disks have been tested as Live CD's on several laptops and work perfectly. 

My video is only the onboard video, no additional graphics card has been installed.  The computer is intended for internet browsing and e-mail so I decided to start without any high end graphics system. Any video chip on this system would have been integral to my motherboard (or so I assume, and I DO get into the beginnings of the Live CD no problem before timeout).

I have attempted both the check memory and check hard disk features of the Live CD, both lock up after an undetermined time lapse.

My instincts lead me to wonder about video drivers, but I have no idea how to build a custom disk and I am hesitant to try.

As a third option, I have torrented a trial version of the dreaded Windows (Win7) as the motherboard states that it is Win7 ready.  If Win7 installs, then I will at least know that the hardware is fully functional (which I already suspect it is).

I have seen the Ubuntu disk fill my screen with lots of information once, and I saw "kernel panic" in there.  Bear with me, I don't know what that means, and it did NOT always appear.  Usually I just go black screen or locked screen.

---

### Post by jerrrys on 2011-05-29
has the option of the "alternate install cd" been mention?

---

### Post by Cliffjam on 2011-05-29
I have seen it on a download page, but I don't quite understand what is alternate about it, or which reasons I might want to try it.  What exactly is it for?

---

### Post by jerrrys on 2011-05-29
if this doesn't answer your questions let me know

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/GettingUbuntu#Download%20the%20Alternative%20Installation%20CD]("https://help.ubuntu.com/community/GettingUbuntu#Download%20the%20Alternative%20Installation%20CD")

this is dated, but gives you the idea

[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)

---

### Post by Cliffjam on 2011-05-29
I will be reading those links when I have a chance, but here's an update on my test of the Win7 trial disk.

It MOSTLY started installing when I got the blue screen of death. Upon my second attempt the time before it freaked out again was shorter....this is consistent with the way it was behaving whilst trying the Ubuntu installs.  I get less time between crashes the more I try to use it.

The second crash with the Win7 Blue screen of death gave me a message of "Page fault in non-paging area" along with the mess of numbers. I'm going to research this before I try to use an alternate Ubuntu install in case I have a hardware issue that I can take up with the company I just bought this from. This might take a few days. I'll keep everyone posted. Again, thanks for the comments.

---

### Post by 3rdalbum on 2011-05-29
These sorts of things are usually caused by bad RAM. Unfortunately it seems like there's a lot of bad RAM around; I've built five computers and found bad RAM in three of them.

---

### Post by jerrrys on 2011-05-29
should have a BIOS option to check ram.  it will take a long time

---

### Post by NormanFLinux on 2011-05-29
You can check up on what's happening by removing RAM modules and see if you still get lockups. If you don't, its probably bad RAM and should be replaced. If you do, the motherboard may be going bad or it could be a sign of a hard drive about to fail.

---

### Post by 4Orbs on 2011-05-29
Just some suggestions: First, go into the BIOS and disable the ASUS Express Gate feature. It can be re-enabled later. Second, check that the fans are all spinning, especially the cpu cooler. Third, double-check the sata connections and power connections to the hard drive and optical drive.

---

### Post by sanderj on 2011-05-30
> **4Orbs said:**
> Just some suggestions: First, go into the BIOS and disable the ASUS Express Gate feature. It can be re-enabled later. Second, check that the fans are all spinning, especially the cpu cooler. Third, double-check the sata connections and power connections to the hard drive and optical drive.

@ CPU cooler: good point! The system could lock up because of overheating.

An additional advice to the OP: reset the BIOS settings to default.

---

### Post by Cliffjam on 2011-06-01
I wanted to thank everyone for their comments to this thread. I contacted tech support from the vendor, and while they weren't much help at all, they wanted me to test the RAM chips.  I had 2 "4GB DDR3 1333 MHz 256x8 (PRT)"  RAM chips installed.  I took one out, taking me down to a 4GB ceiling and the system installed 11.04 perfectly! After I complete any updates, I'll add the other RAM chip back in to see what results I get.  

So 3rdalbum and NormanFLinux, thank you for seeing to the core of my issue, and thank you to jerrys for being so explanatory. I admit I've been a M$ user through necessity for years, but seeing the community for Ubuntu has made me want to try it for a long time.  This is the first computer I've gotten that didn't have Windows bundled, and in fact, the tech support guys weren't willing to trouble-shoot any OS that didn't have the "metallic silvery coating on an official Windows disk obtained through Microsoft."  Now, the ultimate test......sending this computer home to Mom.  :)

---


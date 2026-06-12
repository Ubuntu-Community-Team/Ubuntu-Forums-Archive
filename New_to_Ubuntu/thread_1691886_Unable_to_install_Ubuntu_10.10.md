---
title: "Unable to install Ubuntu 10.10"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Leinado on 2011-02-20
Hi folks I'm a new guy looking for some assistance on using Ubuntu for the fist time.

I used a flash drive (Kingston Traveller 2gb) to set up a boot USB Stick of Ubuntu 10.10.  I've tried multiple times (I even made a boot DVD of Ubuntu 10.10) but when I try to install it I get what looks like a message (black screen small white text):



(process:332): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)




Any ideas what's going on and what I can do about it?


Hardware:
CPU: AMD Phenom II X4 925 Deneb 2.8GHz Socket AM3 95W

RAM: Crucial Ballistix 2GB (2 x 1GB) 240-Pin DDR3 DDR3 (PC3 10600)
 
VIDEO: HIS H467QS1GH Radeon HD 4670 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP 

OPTICAL: Sony Optiarc CD/DVD Burner Black SATA Model AD-7260S-0B

POWER SUPPLY: CORSAIR Enthusiast Series CMPSU-650TX 650W ATX12V / EPS12V

HARD DRIVE: SAMSUNG Spinpoint F3 HD103SJ 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive 

MOBO: GIGABYTE GA-MA770T-UD3P AM3 AMD 770 ATX AMD

All parts are brand new and have never been in a past machine and I have no problem formatting the harddive if need be.

Thanks in advance for any help.



EDIT: Thanks for the tip on the Alternative Install info yeats.  I made a boot cd of it and have started running it. However after getting to the partition portion of the install and choosing "Guided - use entire disk" its been at 33% for at least the last 2 hours. Hopefully this is just because it's trying to format a 1TB drive.

---

### Post by yeats on 2011-02-20
If you're sure you want to install, try the alternate installer:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by Leinado on 2011-02-21
Thanks for the tip on the Alternative Install info yeats. I made a boot cd of it and have started running it. However after getting to the partition portion of the install and choosing "Guided - use entire disk" its been at 33% for at least the last 2 hours. Hopefully this is just because it's trying to format a 1TB drive.

I ended up restarting and ran a memory test.  Its been going for about 11hr. and there seem to be a lot of errors coming up.

---

### Post by Leinado on 2011-02-21
Just to give an update (and more possible info).

I ran the Alternative Installer in Expert Mode and when it gets to the "Loading Additional Components" portion it gets to 14% (text under the progress bar says, "Retrieving updates-modules-2.6.35-22-generic-di")

---

### Post by yeats on 2011-02-22
You can do Alt-F4 when the installer is running to see log messages (Alt-F1 to return to main screen).  What do the logs say when it's stalling out?

---

### Post by Leinado on 2011-02-23
This time it got to 21% ("Retrieving nic-pcmcia-modules-2.6.35-22-generic-di")

This is a screenshot of I got after hitting Alt+F4 to bring up that log.  (You can click on the thumbnail to get the full picture.)  Before the "[3936...." is a date and time stamp.  This section repeats itself every few minutes so I'm guessing its a part of the process that is failing and keeps retrying.

[[img]http://farm6.static.flickr.com/5056/5472162835_d09a513bc0_t.jpg[/img]](http://www.flickr.com/photos/33799370@N06/5472162835/)
[2011-02-23 20.25.00](http://www.flickr.com/photos/33799370@N06/5472162835/) by [Sanguine Dream](http://www.flickr.com/people/33799370@N06/), on Flickr

Thanks for your help.

---

### Post by yeats on 2011-02-24
> This time it got to 21% ("Retrieving nic-pcmcia-modules-2.6.35-22-generic-di")

I'll just ask... do you use a network card that you plug into the PCMCIA slots on your laptop?  If so, you might remove it for the install process, just to see if that makes a difference.  If not, you might consider trying to install in "expert mode", which should prompt you whether to load the PCMCIA modules (at which point you should answer "no").  Keep using Alt-F4 for troubleshooting.

> This is a screenshot of I got after hitting Alt+F4 to bring up that log. (You can click on the thumbnail to get the full picture.) Before the "[3936...." is a date and time stamp. This section repeats itself every few minutes so I'm guessing its a part of the process that is failing and keeps retrying.

Yes - this would probably point to a hardware problem.  Try disabling all peripheral devices (especially PC card ones) you might have hooked up and try again.

---

### Post by Leinado on 2011-03-03
Actually I'm working on a desktop not a laptop.  But in the end it was a hardware issue.

Originally my plan was to play around with Ubuntu for a few weeks then get a copy of Win 7.  Well this issue kinda forced me to get Win 7 ahead of schedule and low and behold it would not install either.  (Meaning that I couldn't install Ubuntu 10.10, 10.04, and Win 7.) Looked up the error I was getting and the general advice was pointing at RAM.  I randomly pulled out one of my RAM sticks and sure enough it booted normally and installed Win 7.  After the install I put the bad one back in and it gave the same error.

So in the end it was a RAM stick.  (Which is odd because it was passing memory tests. :confused:)  Thankfully I was using 2 1gb sticks so I still have 1gb stick to work with until I can get more (more than likely I'll replace that 1gb with at least 4gb of something else altogether, that's what I get for using RAM that came as part of a combo with my processor).

I have a second hard drive that I'm gonna attempt the Ubuntu install on (don't want Win and Ubuntu on the same drive) again.

Thanks for your help yeats!  You rock!:guitar:

---

### Post by mastablasta on 2011-03-03
or better yet replace both 1GB sticks and get 2 other sticks of same size, so you can have daster dual channel RAM.

---


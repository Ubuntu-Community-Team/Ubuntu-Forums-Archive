---
title: "Installation Problems - Samsung VM7000"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by jaconat on 2009-08-10
Hi all, very new to all this. I am currently a Windows user and getting cheesed of with performance etc, etc so looking to move all my machines to Linux by experimenting on my old laptop. Looked through the documentation as best I could but still having problems installing v9.04 on my old Samsung VM7000. 
 
The main options screen loads, I set country then try to install but it freezes with a black screen and flashing cursor in the top left corner. I left it sitting like this for a couple of hours just to check it wasn't really doing anything!
 
It has 256MB of memory and I ran the memory checker and everything passed OK.
 
Mucked about with a few of the BIOS settings (Installed OS=Other, Large Disk Access Mode=Other) but with the same result every time.
 
Any ideas as I am getting rather frustrated :(
 
Thanks

---

### Post by halitech on 2009-08-10
I'm not sure but from what I was able to find, it looks like the laptop has an old ATI Rage video card. Are you using the Desktop (Live CD) to try and install? If yes you may want to look at using the Alt install cd and possibly Xubuntu instead of Ubuntu as it has slightly lower requirements.

---

### Post by raymondh on 2009-08-10
Halitech has a point about trying the liveCD vis-a-vis the ATI rage card.

Also, at 256mb RAM less whatever the video card takes, it'll be quite a a tedious process to install and run a full-ubuntu desktop install.  This is the minimum requirements for [jaunty]("http://www.ubuntu.com/getubuntu/releasenotes/904").

My experience (lately) with Xubuntu has been not-so-impressive as compared to before.  For a Ubuntu flavor, I have started to use [crunchbang]("http://crunchbanglinux.org/").

Just my .02 cents.

---

### Post by jaconat on 2009-08-11
Thanks for the suggestions - tried xubuntu 9.04 desktop with the same results.
 
....so tried xubuntu 9.04 alt.  Started to install ok then locked up on setting up the partition.  I removed the partition using another app and the install progressed much further.  However it has now locked up installing the base system at 74% - storing language...
 
Any suggestions gratefully received.
 
Thanks

---

### Post by halitech on 2009-08-11
has it actually locked up or is it just taking a long time to get past that point? If I remember right setting up the language does take a abit on older systems.

If it is indeed failing, you could try crunchbang (never used it so can't comment on it) or install a minimum install of Debian with XFCE following the instructions here

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by jaconat on 2009-08-11
Thanks Halitech - you were correct.  It hadn't locked up just took a l-o-n-g time (~2 hours).  Now however it has frozen again on Configuring Language-pack-en-base.  It has been sitting there on 1% for the last 4 hours - I assume it has locked up now?
 
Really frustrated now as it is not the smooth start to starting with Linux as I had hoped.  What is the problem?  Is it that it is a really old laptop and really I just need to bin it and start with something newer?
 
Thanks

---

### Post by halitech on 2009-08-11
It's not that the system can't handle linux, I think its more the flavour of linux, or the install method should be re-evaluated.

Based on what I can find in the manual ( [http://www.samsungpc.com/products/vm7000/vm7000_manuals/vm7000_manuals.htm](http://www.samsungpc.com/products/vm7000/vm7000_manuals/vm7000_manuals.htm) ) this laptop was designed for Windows 98 but will support up to XP. 

Specs:
Display - 1024x768 32bit color
Video - 4meg ATI Rage XL w/ tv out
Ram 256meg PC100
Hard drive ?
CPU P3 700?

With those specs, its not going to be a powerhouse by any means but it can be made to work. I just did an install of Ubuntu 9.04 using the alt install cd on a celly 638 with 384meg of ram and a 60gig hard drive. Speed demon? not even close but usable.

boot to grub - 14 seconds
Boot to Login - 1min
Login to desktop - 40 seconds
total boot time - under 2 minutes.

Time to load firefox - 14 seconds
time to load Open Office - 24 seconds

So, while its not the quickest machine around, it does the job. I think the biggest problem is using the Live cd to try and load everything. I did an install of crunchbang and while it did load faster, its not as easy to configure and although I didn't time things, I don't think it booted much faster. I would almost suggest either letting it run over night (I don't think its locked up, just working hard on the section its on) and see what happens. If indeed it did lock up, grab a copy of the alt install cd and give that a go. The benefit of the alt cd is it doesn't load a desktop first, its more like an old style DOS installer but it does the job where the the Live cd will sometimes fail.

---

### Post by raymondh on 2009-08-11
'second the alternate install method.

As for crunchbang, my experience has been the opposite when I installed it on a P3 machine with 512mb .... as opposed to jaunty..... where I found the performance of crunch + openbox better than jaunty + gnome.  Nevertheless .... I agree, both machines are useable with either distro.

---


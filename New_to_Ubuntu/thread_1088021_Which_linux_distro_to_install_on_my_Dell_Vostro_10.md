---
title: "Which linux distro to install on my Dell Vostro 1000?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by cranky1984 on 2009-03-05
Hello everyone,

I am an absolute newbie to Linux and have Vista loaded on my Dell Vostro 1000 series laptop.
I wish to switch to Linux, however I have heard that there are compatibility issues with some of the linux distros. I would be obliged if anyone suggest me a free Linux distro which I can install and use without much pain?

My configuration is as under:-
AMD AthlonTM 64 X2 Dual-Core processor TK-57 (1.9GHz/256KB)
2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 Dimm
ATI Radeon®  Xpress 1150 256MB HyperMemory&#33922;  (integrated)
120GB 5400RPM  Hard Drive
8X DVD+/-RW with double-layer DVD+R write capability, Cyberlink Power DVD
Integrated Audio
Dell Wireless 1490 802.11a/g Wi-Fi Internal Card

---

### Post by kanikilu on 2009-03-05
Would it be too obvious to suggest Ubuntu? :P

Seriously though, try out a few distro's with Live CD's (which is most these days), and see which ones work the best "out of the box", and that's probably what I would go for to avoid a lot of work after installation to get everything working.

---

### Post by Flyingjester on 2009-03-05
i agree with kanikilu, try out the live cds, if everything runs run with them, go ahead and install. i would suggest ubuntu and fedora for first timers.

---

### Post by st33med on 2009-03-05
IMO, Ubuntu.  However, that Wireless card probably needs some work to get it up and running.  Any distro will have a problem with Dell Wifi cards. Needs NDISwrapper to use the driver.

It could also be a more compatible wireless card because Dell likes to mask the original manufactures.  Install Ubuntu and we can help with it.

---

### Post by cranky1984 on 2009-03-05
hehehe....
thanks for the reply...
i was just wondering if people have tried other flavors of linux and could suggest me on the same...I have never used Linux before...so thats the reason Im kinda apprehensive about jumping in. 
Live CDs sound good. err...sorry if im sounding stupid, but I just put the Live CDs in and check if everything is workin?? Is that what you meant? DOnt I have to install drivers and stuff like we do in Windows?

---

### Post by Flyingjester on 2009-03-05
no, drivers are contained in the kernel. the kernel is loaded into ram. and yes, if you pop a livecd in it should boot into it (might have to change bios settings though) like he said, wireless might be your biggest issue, and yes, for that you might have to install drivers. The only way to know with wireless would be to install it, then try and install the drivers for it. unless it works right away in the livecd.

---

### Post by kanikilu on 2009-03-05
> **cranky1984 said:**
> DOnt I have to install drivers and stuff like we do in Windows? Not always, but as st33med mentioned, the wireless NIC may take some work.

I eventually settled on Ubuntu, but the distro's I've tried are: Fedora, OpenSUSE, Mandriva and Sabayon, to name a few...

---

### Post by avtolle on 2009-03-05
While you may have to install a driver or two (especially with the wireless card and the graphics card), many drivers are incorporated within the kernel. As for me, apart from Ubuntu (from 5.10 through 8.10), I've tried LinuxMint (5 and 6; based upon Ubuntu),YellowDog Linux (for my ppc machines) and openSUSE 11.1. The "easiest" for new users of these is Linux Mint, given that it comes with codecs installed, and basically freezes the kernel to allow for graphics, etc. drivers to work once installed. OpenSUSE 11.1 is fairly user friendly, but I prefer Ubuntu and Mint. JMO.

EDIT: Mint also comes with Adobe Reader, Flash already installed, which has been a bit of a sticking point for some new users. Re: kernel freeze, when graphics drivers and wireless drivers are installed, depending upon the method of installation, kernel updates will result in the need to reinstall the same sometimes. 

As was said prior, obtain some Live CDs, (or DVDs) and give them a whirl to see how you like them.

---

### Post by cranky1984 on 2009-03-05
ok....i will try that ....should I backup my stuff or something for trying out the live cd or would everything be fine?

---

### Post by Flyingjester on 2009-03-05
everything is fine, livecds do not make any alterations to your computer :)

---

### Post by cranky1984 on 2009-03-05
cool...
thanks a ton for your help guys....ill try it out by tonight....
got to go give my mid terms now...:)

---

### Post by handydan918 on 2009-03-05
With that broadcom 43xx card?
[Mepis]("http://www.mepis.org/mirrors"), hands down. Has a GUI network assistant that will install the driver for you, no cli needed. Note that this will not work in Live cd mode. It must be done from an install to the hard drive.

---

### Post by kanikilu on 2009-03-05
The Live CD won't touch your hard drive (until you tell it to), but if you don't already have a current backup of important data, I'd say get on that ASAP before doing anything else.

---

### Post by st33med on 2009-03-05
> **Flyingjester said:**
> everything is fine, livecds do not make any alterations to your computer :)

Well, technically it creates a new partition and/or deletes whatever was on their. 

It could potentially screw something up (less than 1% of that happening), but, if you don't care for anything that is on Vista, you can install without backup.

That said, back ups are good if data on the HDD goes screwy. So, if you do this again, BACKUP BACKUP BACKUP!!.

---

### Post by cranky1984 on 2009-03-05
i tried going on the site ubuntu.com and it said download ubuntu 8.1. is that the same thing as live cd or is it different?

---

### Post by avtolle on 2009-03-05
The default download is the Desktop (Live) CD, so yes, that's it.

EDIT: Once you download the iso file, it will need to be burned to a CD as an image after checking its hash (md5sum) to be sure you have a good download. I always recommend burning at a slow speed (4x has worked for me), and then, when booting the CD, checking the integrity of the disk (an option at the opening menu) before proceeding. Good luck.

---

### Post by Ben Crisford on 2009-03-05
Erm, trying not to sound un-biased, this is the order to try them in:

[I]1)Ubuntu
2)Kubuntu
3)Xubuntu
4)Try Ubuntu again
5)Try Kubuntu again
6)Try Xubuntu again
7)Fedora
8)Other linux OS[/I]

You can get the live cds really easily ;).

---

### Post by kanikilu on 2009-03-05
Also, if you don't already have a way to burn an ISO image in Windows, I'd recommend InfraRecorder or ImgBurn.

---

### Post by CRIMPS on 2009-03-05
yeah, Infrarecorder worked well for me when I came from Windows and I wanted to find a free .iso burner.

Have fun!

---

### Post by raymondh on 2009-03-05
I got "my feet wet" with gOS 3.1 which I believe is hardy based. I did not have any trouble with wireless.

---

### Post by cranky1984 on 2009-03-05
cool...i jst burned by ubuntu DVD....
phew...im starting it up on ....
hope it works...
thanks a ton for ur help guys...
btw i used IMGBURN......

---

### Post by rafac24 on 2009-03-05
Yeah, the Ubuntu variations have been the OS's to consistently work well with most desktops and laptops right out of the box without any additional drivers. That's why it's gained so much popularity, I believe.

After your install, check out these site for some necessary/cool upgrades:
([http://tombuntu.com/index.php/2008/04/25/10-tips-for-after-you-install-or-upgrade-ubuntu/](http://tombuntu.com/index.php/2008/04/25/10-tips-for-after-you-install-or-upgrade-ubuntu/))
([http://maketecheasier.com/things-you-need-to-install-after-installing-ubuntu/2008/01/24](http://maketecheasier.com/things-you-need-to-install-after-installing-ubuntu/2008/01/24))

Those are just some suggestions. Don't take them all to heart. Have fun!

---

### Post by cranky1984 on 2009-03-06
hey folks..
im replying after logging in from my live cd...
damn this is sooo coool...
my lappy is fast and is wayyyyyyyyyyy coooler than the stupid vista....
bt my wireless card wasnt detected i guess...
i had to connect the ethernet cable for this....bt its awesome...damn....
im loving this....
i need to use Visual studio at work though..would I be able to do that from linux tooo?

---

### Post by cranky1984 on 2009-03-06
er...also....
im using pidgin as my instant messenger...Cant i use the webcam option on it?
a whole lotta questions i guess...bt this is coooool

---

### Post by trav1856 on 2009-03-17
> **st33med said:**
> IMO, Ubuntu.  However, that Wireless card probably needs some work to get it up and running.  Any distro will have a problem with Dell Wifi cards. Needs NDISwrapper to use the driver.

It could also be a more compatible wireless card because Dell likes to mask the original manufactures.  Install Ubuntu and we can help with it.

The wireless card works just fine, you have to install further drivers once you get Ubuntu running, it's the Samba stuff that's broken atm...I had it working (same laptop) for a few days, then an update made it barf.

---

### Post by cranky1984 on 2009-03-17
> **trav1856 said:**
> The wireless card works just fine, you have to install further drivers once you get Ubuntu running, it's the Samba stuff that's broken atm...I had it working (same laptop) for a few days, then an update made it barf.

hi there...well as you said the wifi card worked fine for me...i did have to install some drivers using the driver manager itself...
Im not sure whats samba and stuff...sounds greek and latin to me...lolol...
but the basic linux stuff is working for me and i havent been hapier..:)

---


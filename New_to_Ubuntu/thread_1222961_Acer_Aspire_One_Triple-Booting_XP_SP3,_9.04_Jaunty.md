---
title: "Acer Aspire One Triple-Booting XP SP3, 9.04 Jaunty, and Puppy Linux"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by LewRockwell on 2009-07-25
Acer Aspire One Triple-Booting XP SP3, 9.04 Jaunty, and Puppy Linux

this was my experience with an Acer Aspire One:

(note that I was responding to an Asus owner with Mint wireless issues - [http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious](http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious))


> **LewRockwell said:**
> I had an eerily similar experience with my Acer Aspire One AOA-150-1864 (seems many of the internals are the same as your Asus). Note usage of the Dell mini wlan 1390 card(Broadcom). I picked the netbook up used "on the cheap" and at first I thought I had been sold a piece of crap. It came with Windows XP Pro SP3 and the damn thing gave me fits connecting to my home wireless(Motorola Surfboard SB5101 Broadband Modem feeding a Linksys WRT54G). I must have messed around with that netbook for several hours resetting this and that and rebooting numerous times. Then I went into the router settings and started banging around there also. The one thing I did that might have cracked the nut was I switched from G-only to mixed(but after it started connecting I switched it back and it's still connected flawlessly).

After getting the wireless working and installing my favorite stuff on windoze(and using them to clean, spruce-up, and defrag windoze) I then set about partitioning the 120GB hard drive using a LiveCD of Puppy Linux(Gparted) via an internal cd-rom drive I had laying around and one of these gadgets which, I must say, no tech or hobbyist should be without([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)).

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

After the partitioning ritual(reducing the windoze partition in several smaller steps with the obligatory reboot into windoze between each reduction so checkdisk could do it's thing and so I could defrag with each reduction) I installed Puppy Linux and was pleased that it worked very well from the get-go(Puppy installation slipped the Grub bootloader in place also). Then it was off to the races to install Ubuntu 9.04 Jaunty Jackalope (full version) which also went without any problems at all. It took a minimal amount of time and fiddling to get it working with the wireless.

Of course there was the minor editing of the grub's menu.lst to get it looking "just right" and a couple of reboots into each system, but I must say that I am pleased with the performance and overall experience. I've also reserved five more partitions for future *nix distros as well.

One note with respect to the 8.9 inch display...it's small and it bothers my eyes more quickly than the bigger screens. I plugged it's VGA output into a nice 17 inch monitor I have on the tech bench and it looked great and was easy on my eyes.

I'd imagine using this little guy to drive a big monitor and, with a wireless keyboard and mouse assisting, it being a reasonably energy-efficient alternative to the regular desktop monsters consuming hundreds of watts unnecessarily.

.

of course, my regular LiveCD of full version Jaunty had been used successfully several times previously so I knew I had a good burn

Acer Aspire One, Dell mini wlan 1390, external CD/DVD drive, netbook, linux

Also, for reference when dealing with netbooks and compatability:
[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks](https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks)

Here are other good links:
[http://code-hacker.wetpaint.com/page/Install+Ubuntu+on+Acer+Aspire+One](http://code-hacker.wetpaint.com/page/Install+Ubuntu+on+Acer+Aspire+One)

[http://moblinzone.com/top_stories/494/34/37/Acer_Aspire_One_is_a_Netbook_to_Desire](http://moblinzone.com/top_stories/494/34/37/Acer_Aspire_One_is_a_Netbook_to_Desire)

[http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One](http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One)

.

---

### Post by LewRockwell on 2009-08-19
here's a screenshot of my partition editor showing my current seven operating systems:

XP
Ubuntu
Puppy Linux
Moblin Beta
EasyLFS
Mandriva
GoBoLinux

with one reserved partition and three separate swap partitions(just to be different)

actually the separate swap partitions were necessary for some experimentation and research

.

---

### Post by stratprof on 2009-08-30
It seems that "do-things-stepwise" (when partitioning) is a lesson others know well. I guess the only way to learn is to mess up and then repair everything.

The screen shot of your partition setup has, unfortunately, given me partition-envy. And your experience with Mint is awfully close to what I've been tinkering with doing.

My plan has been to use an old USB external hard drive, put the latest Mint on it, and boot my computer off this external disk. 

I was tinkering with creating multiple partitions on this external drive: system (ext3, about 12 gigs) plus a swap, and two separate partitions formatted as ntfs (to facilitate sharing documents and multimedia files with a Windows setup). 

Drawing upon my recent partition experience, it was my thinking that changing distros would  be no more complicated than deleting the Mint partition and replacing it with something else.

The idea of multiple distros co-existing on separate partitions on this drive is intriguing. I'd be grateful if you would comment upon my contemplated experiment and compare it to your setup. 

(On a related theme, my plan would not entail a GRUB startup screen as there'd be only one system on the disk. If I tried to emulate your setup, how would I create a GRUB menu to choose the system to startup?)

---

### Post by oboedad55 on 2009-08-30
> **LewRockwell said:**
> Acer Aspire One Triple-Booting XP SP3, 9.04 Jaunty, and Puppy Linux

this was my experience with an Acer Aspire One:

(note that I was responding to an Asus owner with Mint wireless issues - [http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious](http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious))




of course, my regular LiveCD of full version Jaunty had been used successfully several times previously so I knew I had a good burn

Acer Aspire One, Dell mini wlan 1390, external CD/DVD drive, netbook, linux

.

My drives look like this. Why do you have three swap partitions?

---

### Post by theozzlives on 2009-08-30
> **oboedad55 said:**
> My drives look like this. Why do you have three swap partitions?

No screenshot, but I agree only one swap is needed.

---

### Post by LewRockwell on 2009-08-31
> **oboedad55 said:**
> My drives look like this. Why do you have three swap partitions?

see original post

.

---

### Post by LewRockwell on 2009-08-31
> **theozzlives said:**
> No screenshot, but I agree only one swap is needed.

as per the original post, multiple swap partitions established for specific research, experimentation, and testing purposes...

.

---

### Post by LewRockwell on 2009-08-31
> **stratprof said:**
> It seems that "do-things-stepwise" (when partitioning) is a lesson others know well. I guess the only way to learn is to mess up and then repair everything.

The screen shot of your partition setup has, unfortunately, given me partition-envy. And your experience with Mint is awfully close to what I've been tinkering with doing.

My plan has been to use an old USB external hard drive, put the latest Mint on it, and boot my computer off this external disk. 

I was tinkering with creating multiple partitions on this external drive: system (ext3, about 12 gigs) plus a swap, and two separate partitions formatted as ntfs (to facilitate sharing documents and multimedia files with a Windows setup). 

Drawing upon my recent partition experience, it was my thinking that changing distros would  be no more complicated than deleting the Mint partition and replacing it with something else.

The idea of multiple distros co-existing on separate partitions on this drive is intriguing. I'd be grateful if you would comment upon my contemplated experiment and compare it to your setup. 

(On a related theme, my plan would not entail a GRUB startup screen as there'd be only one system on the disk. If I tried to emulate your setup, how would I create a GRUB menu to choose the system to startup?)

we see no problem with using an external hard drive for your testing and experimentation regarding various *nix distros

obviously this would work wonderfully well when the BIOS is set to boot first from USB, then from any optical drives present, and finally from your installed hard drive(this is what we do)

There really isn't any specific additional information that we can share with you here...that hasn't already been covered either in our original post or on some other forum/thread/posts...

The only caution we would specifically note would be to make sure that your grub is installed into the correct hard drive Master Boot Record

By default it will desire to install itself to the master/primary/internal hard drive(which would be incorrect in your case, as you desire to have all your additional *nix distros AND your grub bootloader on your external/secondary/slave hard drive)

Proper and thoughtful partitioning and efficient installation and administration of the grub bootloader are paramount to your overall success and sense of personal achievement...to that end, searching for grub and partitioning tutorials and information will supply the student with plenty of good materials of varying technical intensity

.

---

### Post by LewRockwell on 2009-09-11
> **LewRockwell said:**
> here's a screenshot of my partition editor showing my current seven operating systems:

XP
Ubuntu
Puppy Linux
Moblin Beta
EasyLFS
EasyPeasy
Mandriva
GoBoLinux

[S]with one reserved partition and[/S]

three separate swap partitions(just to be different)

actually the separate swap partitions were necessary for some experimentation and research

.

slipped EasyPeasy in there last night

EasyPeasy notes:

no way to keep grub from installing
(booted back into EasyPeasy LiveUSB and fixed the grubster...)

wireless doesn't work out of the box either
(too tired to fix for the time being...)

.

---

### Post by oboedad55 on 2009-09-11
> **LewRockwell said:**
> slipped EasyPeasy in there last night

EasyPeasy notes:

no way to keep grub from installing
(booted back into EasyPeasy LiveUSB and fixed the grubster...)

wireless doesn't work out of the box either
(too tired to fix for the time being...)

.

How does GoBoLinux work for you? I'm downloading a LiveCD as we speak. How does it handle the grub install? I don't want something overwriting what I normally use.

---

### Post by markbuntu on 2009-09-11
You should try kuki-linux. I have it on my AOA150 and everything works OOB. Very fast and lightweight and the 2.6.31 kernel so the intel graphics driver is finally working properly.

[http://www.kuki.me/](http://www.kuki.me/)

---

### Post by LewRockwell on 2009-09-21
slipped PCLinuxOS 2009.2 Gnome and Puppy Linux 4.3 onto the Toshiba yesterday and all went well so the Aspire will be put to the test soon!

re:

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.

---


---
title: "How to partition?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Phrea on 2009-08-18
Hello, 
Please forgive me my ignorance, this must have been asked a thousand times...

I'm completely new to [K]Ubuntu, and this will be a dedicated install, NO dualboot, I'm done with Windows on that box.

Here's the situation: I'm upgrading the hardware to a new mainboard [AM2+], an AMD 940 cpu and 4GB memory [and putting in an older Asus 3650 graphics card].
Along with this upgrade I will put in a 320GB HDD and a 1.5TB hdd, the 1.5TB disk will be a data disk, so we'll forget about that for now.
The problem is: How to format/partition the 320GB disk?

I've already chosen ext3 as the filesystem, and I know that my /home partition will be big [the rest of the hdd] [the way I want it, right?].

Please help me choose the sizes for the rest of the partitions [not scared of more than a few].

I'm thinking: / [root] 10GB, /etc 10Gb, /swap 8GB, and the rest for /home

I have a few questions: why does /etc need that much room [and what is it exactly?], and what is saved in that dir? and can I image my install once I think it workes for me?

Sorry for the long post and for repeated questions.

---

### Post by PunkLV on 2009-08-18
1) Are there any particular reasons why you need 8gb swap?
2) 10gb for / is more than enough, for desktops, at least
3) /etc stores configuration settings, mostly

---

### Post by Phrea on 2009-08-18
> **PunkLV said:**
> 1) Are there any particular reasons why you need 8gb swap?
2) 10gb for / is more than enough, for desktops, at least
3) /etc stores configuration settings, mostly

1: that's how I learned it, double the mem
2: ok
3: so how much room is needed for that partition? Or should I forget that partition in favour of another one?

---

### Post by PunkLV on 2009-08-18
With 4gbs of ram swap will be barely used.
I'd set 15Gbs for /, 1Gb for swap and the rest for the /home 
Currently, after a 3 months use, my /etc (Text files with config settings are being stored there) folder weights 13.1Mb and the whole / 4.9Gb.

---

### Post by impert on 2009-08-18
I doubt if you need any swap with 4Gb of RAM. The old rule of thumb (swap=2xram) was for much smaller RAM. I don't seen the point of having a separate partition for /etc, either. Using 10 G for / in Ubuntu with everything except /home should be fine, though since you've got lots of space you could go up a couple of Gb. Personally, I'd keep a bit of blank space, say 80 or 100G unformatted for the time being. You can always add it to your home part'n if you need to, or you could put another distro on it to compare, or to have a spare system for when you stuff up Ubuntu. Or you could use it for backups, though a different drive would be better for that. 
What's in /etc? Heaps of important stuff, you'd need a book to answer that. Have a poke around with file browser, to get the feel of it, and read the forums

---

### Post by bagle on 2009-08-18
realy i say 15 gb for the system files (/usr /ect ecsetra....) 1gb swap 4gb /root the rest should be /home.

yeah thats what i think sinse i usaly have a lot of programs installed. realy you could proably size system down to 12gb but breathing room is a good thing to have. 

yeah im a bit paranoyed. but this is what i recomend give or take a bit.:lolflag:

---

### Post by Arand on 2009-08-18
Always note, swap is necessary if you want to hibernate the computer, so in that case you'll have to set swap to at least 4GB. If you do not use hibernation, and know that you do not use any _extremely_ memory-hungry applications. You can probably do with less or no swap at all.

Currently I have 5GB used out of 14GB / [root], and I don't expect it to up much more.

/etc on a separate partition will proably be very much a waste, since it works completely fine just residing on the / [root] partition, also, as mentioned, it's only ever a handful of megs

---

### Post by LewRockwell on 2009-08-18
what we've learned over time is that it is a good idea to create a swap partition regardless of whether you THINK you are or aren't...going to use hibernate (always plan your partitioning based on the heaviest and largest usages and also utilizing all available functionality INCLUDING hibernation)

therefore, your swap partition should be 1X max ram

so if you currently have 2GB of ram but your system can support 4GB then your swap should be 4GB

1XMAXRAM

it should be noted that in legacy systems the older standard of 1.5 to 2.0 times installed ram should suffice

.

---

### Post by Bartender on 2009-08-18
It seems reasonable to leave yourself the option of hibernation, in which case you need to make swap a bit bigger than the physical RAM.  Not much, apparently - 4.2 GB or so?  With 320 GB at your disposal, and 1.5TB planned for storage, it's not like you've got to make any tough decisions here :)

I set aside 30GB for /.  Have installed a few dozen video editors, movie players, CD rippers, etc. and that folder just recently crept over 4GB.

Not a Linux geek, but I also don't see the need for an /etc folder.

---

### Post by c2006 on 2009-08-18
Something along the following lines would suffice:

/ - 15-20GB
swap - 4.2-5GB. 
/home Rest of disk.

I definitely agree with your idea of having the separate partition for /home, as it means you can clean install without having to lose your personal data (just don't overwrite /home). Although unlike Windows upgrades do tend to *just work*, it never hurts to be able to clean install without losing data, as it's invariably cleaner in the end.

The only other folder that might warrant a separate partition, really is /boot. You wouldn't even need 1GB of space for /boot.

---

### Post by zerhacke on 2009-08-18
With a 320 GB HDD there's no reason to chunk up the partitions for this and that.  If you make the 320 GB HDD all mounted to / with the ~4 GB set aside for swap you won't run out of problems.

Imagine in the future when you use all of the 10 GB for /etc (it's an example, folks, let's not get up in arms) and can't configure any more programs but you still have 250 GB free in /home.  If you mount the entire drive at / you will never sell yourself short either in /home or /foo or /bar.

---

### Post by Phrea on 2009-08-19
Wow, what great replies !
Thank you all so much.

I'm going with / [root/etc/usr, i.e. the complete install] 15 gig, /swap 5 gig [just in case, as mentionned] and the rest goes to /home.

Again, you guys are great. :)

---


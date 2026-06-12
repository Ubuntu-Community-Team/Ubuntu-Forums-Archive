---
title: "Cleaning, and  KleanSweep..?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-01-31
KleanSweep found over 50-megs of maybe "junk" only a third the way through the scan...  Most of it was in root...   I had uninstalled games before the KS scan... I don't play interactive cartoons since I quit repairing pinball-machines and video-games..  I've had enough interactive cartoons for ten life-times... The only bit of junk I have left from years of working with pinball machines and video games, is one old control panel for a Stargate, with all its controls, and lots of wires dangling from it... 

KleanSweep found a Lot of obsolete game-entries... Are they all OK to delete with KleanSweep?..

How do I know what not to delete?..

How do I get into root to delete the junk KleanSweep found?..

Why is "root" so controversial..?  Mention "root", and someone almost bites your face off...  It's part of the OS.. so why is it so "immoral & illegal" to talk about it..?  

What are the Best cleaners for Ubuntu?..

Why don't I see an Ubuntu "defrag"..?

What makes Ubuntu slow down..?  

What makes Ubuntu run faster..?

---

### Post by Kevbert on 2009-01-31
Best way to do a clean up is to use terminal with
```
sudo apt-get clean
sudo apt-get autoclean
```
Linux generally does not need a defrag - see [[COLOR="Red"]this[/COLOR]]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting").

---

### Post by DonaldJ on 2009-01-31
I pasted "sudo apt-get clean
sudo apt-get autoclean"...   OK now I gets it.. but it sure didn't remove as much as KS found..?


How can you look at the software-files of those newly installed packages..?

---

### Post by Kevbert on 2009-01-31
I'm not sure what you mean, but when you download a '.deb' package to be installed it is saved in /var/cache/apt/archives (i believe this can be removed as it just takes up hard disk space.
The other thing is that you may have a few backup files. In boot these are backups of kernels and can be removed as follows:
```
cd /boot
ls -l
rm *.bak
```
This will remove any backed-up (old) kernels, but not those shown in the grub boot menu.

---

### Post by DonaldJ on 2009-01-31
I finally got it.. I had missed one procedure...  Thanks!..


This Ubuntu sure cleans up fast, compared to Windows XP, which takes about a half-hour every couple days...

Is this just a command, or is it actually a software..?  I can't find it in the OS..?  Do you run this command in terminal for each cleanup?..

Does this cleanup ever take-out stuff it shouldn't..?   If it ever did take out good stuff, can it be restored..?

---

### Post by mister_pink on 2009-01-31
There's also sometimes some left over config files from when you remove things. Open up synaptic (System, Admin, Synaptic) and select the "Status" tab in the bottom left. Now on the left hand side select "Not Installed (residual config)". The programs that appear in the list on the right are ones which you have had installed but have left config files behind. If you don't want to keep these settings (ie you never plan to install them again) you can right click them and select "Mark for Complete removal". When you've done this to any you want to get rid of then click apply. 

Also, those clean up commands above shouldn't cause any issues. One gets rid of archived packages (which you can always download again in future) and the other removes programs which are no longer needed (because they were required by something else which you have since removed).

---

### Post by Kevbert on 2009-01-31
> **DonaldJ said:**
> I finally got it.. I had missed one procedure...  Thanks!..


This Ubuntu sure cleans up fast, compared to Windows XP, which takes about a half-hour every couple days...

Is this just a command, or is it actually a software..?  I can't find it in the OS..?  Do you run this command in terminal for each cleanup?..

Does this cleanup ever take-out stuff it shouldn't..?   If it ever did take out good stuff, can it be restored..?

These are just commands from the apt package.  You can run them whenever you want.  Another command is 
```
sudo apt-get autoremove
```
which will remove (software) packages which were automatically installed to make other software work (dependencies). When the software is removed, sometimes these packages are still installed and this command will remove the unused packages.  If you want to look at what these commands do you can enter the following in terminal
```
man apt-get
```
man = manual. To view each page in turn press the spacebar or to get back to the command prompt press q.
The clean-up should not remove anything that is required (good stuff). If it does then this is a bug.

---

### Post by DonaldJ on 2009-01-31
> **Kevbert said:**
> I'm not sure what you mean, but when you download a '.deb' package to be installed it is saved in /var/cache/apt/archives (i believe this can be removed as it just takes up hard disk space..



I  often like to take a looksee in what was in the OS that I'm deleting...
I always stripped Windows stuff down to its files and microns to see what in there..  sort of like an "autopsy"...   How do I get into those softwares to looksee what I'm killing..?

---

### Post by Kevbert on 2009-02-01
Same here. I good source of information is the Synaptic Package Manager as it shows what packages and some library files are for. If it's installed it will have a green box next to it and regardless of that will give a description of the file.
Another source of information is [[COLOR="Red"]Wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/"), but it can be edited by anyone, so it's always worth getting a second opinion.

---

### Post by DonaldJ on 2009-02-02
Reading about is good too, but I really just want to open it up, and see what's inside it...  

I wants to take one of the hd's with Ubuntu in it, and inspect every hidden thing in it..  just for personal curiosity, and because I've always enjoyed taking little thing apart, like when I was four, and got hold of my parent's alarm clock, with a screw driver and a needle-nose plier...  They found me sitting on the floor, surrounded with little clock thingies, little brass gears, springs, and screws, and such...  Well, I found-out what part was making that ticking-sound...

Are Ubuntu softwares locked from the user opening them up, like a kid with an alarm clock..?  I want to see those software's guts.. to see what makes them buzz and beep...  

I did this with PC's too...  I'd get towers from garage sales, and have a party in them...  A few really sent up a blast of smoke after all the crackles and pops stopped... One CPU even blew its plastic covering off, exposing its cct...  Last month I dropped a cheapy flash drive, and it died, so out I gets the needle-nose and the screw-driver to do an autopsy...  Not much in them...  I just waiting for one of my mp3's to croak...

How do you get to looksee in Ubuntu softwares..?  I gots my needle-nose and screw-driver primed and ready...

Once saw a rabbit hit by the car in front of me...  Managed to sedate it, and got into the crushed leg with tools and antibiotics, after reading what to do... I cleaned and cut, and cut and cleaned, and kept the little critter comfy and hydrated, and seriously drugged with marcaine, and I perfectly removed splintered bone, and platinum-wired loose-muscles and tendons to joints, and smoothed out, and inverted, the sharp ends, and potential abrasive points.. It never got any infection what so ever...  It purred when I caressed its back...  In six-weeks I had a healthy three legged bunny, who could still jump four-feet with one hind leg...  

I gots my needle-nose and screw-driver ready...  Who's next?..

At 15 I knew I could be the world's greatest brain-surgeon.. but school couldn't break my spirit, so the crazy nuns had the football coach lay a real nasty beating on me in the classroom, back when it was legal, intending for it to kick me out of school.. and it did... I snuck into universities, and studied there as a non-credit visitor...  Lab students took me under their wings, and some even gave me homework..  and a nuke fizzycist took me under his wing...  School and church destroyed my life, and my family...

---

### Post by DonaldJ on 2009-02-08
I think novices should refrain from using cleaners in Ubuntu till they know the OS enough to write commands...  Ubuntu is honest...  There isn't any of that nasty window's craziness in it...

---


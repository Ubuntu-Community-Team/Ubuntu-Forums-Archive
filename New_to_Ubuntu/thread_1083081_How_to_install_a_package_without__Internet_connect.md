---
title: "How to install a package without  Internet connection?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Rumtscho on 2009-02-28
For those who can't be bothered to read all, here is the actual question:

**How to install the package build-essential? I don't have Internet so I can't use synaptic, tried manual install and ran into apparent circular dependencies between packages.** 

Please explain it patiently, I had my first glimpse at a Linux six hours ago. 


--- the whole story ---


Last week I was turned down at a job interview because I have no experience at all with non-Microsoft software (I would have needed LAMP administration, Eclipse, LaTeX etc.) So I decided to gain some knowledge before the next interview (that's 10 days from now) :D 

I got a half-gutted old machine with a fried PSU and begged friends for upgrade leftovers till it was complete. (It's an Athlon 1800+ with 256 RAM, if that`s important). This morning, I downloaded the latest Ubuntu, got a recent edition of the Wiley Linux Bible, and set up the PC (Linux-only, single partition). Working with the book was pretty straightforward, it feels good to start chaining 3 commands on the terminal an hour after installation, even if they're the only 3 commands one knows :P But then I decided to do some real work (instead of coppying files by command line or changing Gnome desktop backgrounds). The first cool thing would have been to get an Internet connection working. 

The Ubuntu recognizes the ancient ethernet card all right, only I can't imagine laying 17 meters of CAT5 with two doors in the way, so I opted for wireless. Trouble is, my Ubuntu 8.10 doesn't even notice that there is a USB dongle attached (it was in the port during installation). 

My dongle's model is A/WLAN-N2, produced by a never-heard-of called either Aquipa or Pataco (the packaging suggests they're not quite sure themselves). The chipset is made by Ralink, but I can get no information about the actual chipset model, only a device ID (that's 148f:2770). I found a German wiki ([link]("http://wiki.ubuntuusers.de/WLAN/Ralink")) saying that I need a driver, and that there are native Linux drivers for Ralink chipsets. 

I guess that my chipset instrucions must be in the 28xx section, because they say that the drivers for the other Ralink chipsets are included in Ubuntu since version 7 something, and because the number 2770 appears in my device ID as well as in the name of the 2870 driver file on Ralink's homepage. 

I started as described in the wiki, by downloading the driver on my Windows machine, and proceeded by installing the packages linux-headers and build-essential. That's where I encountered trouble. I read that there are tools that can install the packages for me, but (!) they need a working Internet connection to do it - and I can't get one without those packages. So I decided to break the Catch 22 by downloading the packages on the Windows machine, then transfer them to the Linux PC via flash drive, and install them using whatever utility I find. It happened to be one called GDebi Package installer, and it started complaining right away: "Error: Dependency is not satisfiable: g++" and so on. So I downloaded the dependencies, and after a few round trips, the linux-headers package was installed. The other one caused trouble. The search for the package g++-4.3 led me not to one file, but to two different ones. The first is called g++_4.3_4.3.2-1ubuntu11_i386.deb, and it says it needs libstdc++6-4.3-dev before I can install it. The search for the libstdc yielded the file libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb. And I cannot install that one either, because it requires g++-4.3. So if I found the right files, there is a circular dependancy in those packages 	](*,) The second match for g++-4.3 was a file called g++-4.3_4.3.2-1ubuntu12_i386.deb, and that one needs a package called gcc-4.3-base. I got a file called gcc-4.3-base_4.3.2-1ubuntu11-i386.deb, but I cannot install it, as the installer insists that it is already installed and running. 

What am I to do now? Can you tell me how to install the build-essential package without using synaptic? Or should I try the non-native drivers with NdisWrapper - that's the second option mentioned in the page above but they say it causes stability problems. What is easier for a beginner, installing the Linux drivers or the Windows ones? If I go for NdisWrapper, do I need the build-essential package? Or is it just an easy thing and I only downloaded the wrong files? Or maybe I should try the generic Linux Wireless drivers, which are mentionted in another article of the wiki above (they seem to be targeted at multiple chipsets, but require the same packages as the Ralink ones).

---

### Post by The Cog on 2009-02-28
With the circular dependencies, you can overcome that by installing all of them at once. Collect all the .deb files into the same directory and then use > sudo dpkg -i *.deb
You have picked on about the hardest thing about Linux here. Ubuntu really does assume a working internet. It may be easier to cart the PC over to the nearest ethernet port until the installing is done. There is a difference between making some effort in order to learn and beating your head against a wall.

Actually, I use a pair of ethernet-over-the-mains adapters. I can't imagine doing without them now. But that's just a luxury, really.

If you run **sudo aptitude install build-essential** without Ethernet connected, it will fail of course, but may well tell you which packages it intends to try and download. Then you can just work through the list by hand.
EDIT: Actually, it may not even be able to give you a list of what it needs until it's been connected to the internet and scanned the repositories.

I've never tried ndis-wrapper so I can't say anything about that.

---

### Post by zvacet on 2009-02-28
**Sys>admin<software sources **and check box for add CD.Other way is to 
type in terminal

```
gksudo gedit /etc/apt/sources.list
```

and remove # sign from cd-rom line(it is on top of the file).Save file and close it.Put your Ubuntu disc in drive and go to the synaptic and install build-essential.Yes,you have that package on disc.

---

### Post by binbash on 2009-02-28
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by Rumtscho on 2009-02-28
Thank you all. Now I've got Internet and am writing this from my Ubuntu PC. 

I don't know if the Cog's solution with simultaneous install would have worked, but trying to install the package without a connection didn't get me a list of the needed files, only a network problem message. binbash's idea looked good, but the tool would have needed me to install certain python packages, which gets me back where I have started. So I just tried installing it from the CD like zvacet suggested, and it worked. Thank you!

---

### Post by The Cog on 2009-03-01
Good news. Thanks for the feedback.

Enjoy Linux.

---

### Post by elliotn on 2009-03-01
When it comes o keryx I ran into a huge problem when creating the project and plugin. Eg <project><plugin> terminal just errored thE<

---

### Post by EXCiD3 on 2009-03-02
> **elliotn said:**
> When it comes o keryx I ran into a huge problem when creating the project and plugin. Eg <project><plugin> terminal just errored thE<

What was the error with Keryx? Just copy and paste it here and I'll figure it out for you.

You made sure you used "python keryx.py --create <name> debian" correct? (replacing <name> with a project name of your choice)

---

### Post by Craftycorner on 2010-03-23
> **The Cog said:**
> With the circular dependencies, you can overcome that by installing all of them at once. Collect all the .deb files into the same directory and then use 
You have picked on about the hardest thing about Linux here. Ubuntu really does assume a working internet. It may be easier to cart the PC over to the nearest ethernet port until the installing is done. There is a difference between making some effort in order to learn and beating your head against a wall.

Actually, I use a pair of ethernet-over-the-mains adapters. I can't imagine doing without them now. But that's just a luxury, really.

If you run **sudo aptitude install build-essential** without Ethernet connected, it will fail of course, but may well tell you which packages it intends to try and download. Then you can just work through the list by hand.
EDIT: Actually, it may not even be able to give you a list of what it needs until it's been connected to the internet and scanned the repositories.

I've never tried ndis-wrapper so I can't say anything about that.

I too have one stand alone PC, with one USB drive.  Can this work carrying updates in my flash drive to my standalone?

---


---
title: "Installing tgz software"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Graemej on 2010-05-04
I would be grateful for information on the advisability and implications of installing non package software. I have used a package called gpsim which used to run on Ubuntu but now the GTKextra package which is a dependent of gpsim has been deprecated.

If I install this package manually would gpsim (which is a current package) find it ok?

If I do install a package manually are there going to be any problems down the line like being cleaned out by janitor or causing problems if it becomes a supported package etc. and of course problems of which I have no idea may be lurking

Thanks,
Graeme

---

### Post by cariboo on 2010-05-04
There is a version of gpsim in the repositories, it may be easier than installing from source.

---

### Post by Graemej on 2010-05-05
Thanks for your response. The version of gpsim in the repository will run at the command line but the GUI won't run due to GTK+extra (a dependency)  being deprecated. I need the GUI to run my LCD module amongst others. Hence my wondering if installing GTK+extra as a stand alone app would have any downstream problems.

---

### Post by misio.it on 2010-05-06
> **Graemej said:**
> 
If I install this package manually would gpsim (which is a current package) find it ok?


Short answer: [COLOR=Red]**No!**[/COLOR]

Long answer: Latest GPSim package, available on "universe", has been builded forcing the --disable-gui flag on configuration process. This produces a GPSim executable that will not use GTK+ at all.

Quick solution: You should download the GTKExtra 2.1.2 libs and configure, make and make install it, then download the latest GPSim and configure make and make install it too.

Nontrivial solution: I downloaded the Karmic GTKExtra and Lucid GPSim source packages (.dsc, diff.gz and .orig.tar.gz) from [http://packages.ubuntu.com](http://packages.ubuntu.com) and the GTKExtra 2.1.2 source (.tar.gz) from [http://gtkextra.sourceforge.net](http://gtkextra.sourceforge.net). Then, I followed the Packaging Guide recipes to update the Karmic GTKExtra package with the latest sources (2.1.2) and remove the --disable-gui flag from Lucid GPSim source package.
**[COLOR=Red]Rebuilding everithing I finally have a fully working GPSim with its GUI![/COLOR]**

Unluckily I'm not a "MOTU" so my packages are not reliable nor signed. Versions are not consistent and APT gets confused about them. I did everything in a virtual machine, just to try and will not install them package on my real linux-box so I will not publish them.

This just to say that have a full working GPSim with its GUI is possible and package maintainers should do what I did (better than me, of course) to provide us this useful software.

I hope that will happen soon...

---

### Post by Graemej on 2010-05-06
Hi Misio.it,
Thanks for your response. It was clear and put me in the picture. I am very new to Linux and although I have dabbled in past years I have only had it as my operating system for a couple of weeks so will take the easy option.

I can't understand why the GTK+extra was deprecated as it is live, currently being worked on and bug fixed so no patches are necessary any more and is at GTK+extra-2.1.2. It seems so strange that it would have been singled out like that, especially as it compromised gpsim another supported package. Gentoo did the same thing but I think realized it was a mistake and it is back as a package again. Fedora have the latest version and gpsim runs fine there but I want to stay with Ubuntu if possible. Like you I hope the maintainers put this right as I am much less capable than you.

Best wishes,
Graeme

---

### Post by petereiso on 2011-02-26
G'day 

I too tried to get the gpsim giu by compiling gtk+extra, but it depended on other things that I could not find via apt or even by google.

Fedora has it, debian 5 has it, debian 6 does not. Very frustrating.

Being a refugee from M$ windoze I ave been settling in to my new environment nicely over the past few years.  But to have to go on wild treasure hunts to make something that used to work operative is disappointing.  I look at a computer as a tool to, among other things, dabble in electronics, and not as the hobby itself.

*bitching finished*, and thanks to the maintainers for every thing else.

Can any-one say whether the maintainers are likely to re-enable the gui?

cheers 
pete

---


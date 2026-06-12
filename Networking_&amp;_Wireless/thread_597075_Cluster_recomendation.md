---
title: "Cluster recomendation?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by pcal on 2007-10-30
Hi Folks,

I am looking to build a cluster of linux machines as a hobby project to see if I can achieve it, and what it performs like if I can. Then, maybe, to find some practical use to put it to.

I have a 2nd hand 42 unit server rack that I got for the price of a couple of dozen beers, 32 brand new motherboards with 1Ghz processors that I bought from an auction for about the price of the cardboard box they were in, and a pallet load of power supplies. I can cobble together some framework within the rack to hold the motherboards, and clip in a switch to connect them all.

I have the hardware side of things sorted, and am trying to make a decision about what software to use. I've built up one machine and installed Feisty Fawn on it. Seems to run fairly well, and I would like some opinions about whether or not you think it would be a good candidate for the whole cluster.

I've not used Ubuntu before I must confess, and my Linux experience is only moderate - but this isn't a mission critical project and I have no deadlines. I've mostly used Xandros in the past, but with their going down the licensing path with Miro$oft I'm thinking it's time to try a new flavour!

Does Ubuntu support all the relevant technologies? - ie. tftp, pxe, mosix, etc.  And, has anyone here done anything similar in the past, and if so would you be willing to share some pearls of wisdom?


Best regards,

pcal

---

### Post by Capricori on 2007-11-15
Anybody got any ideas? I'd love to know too!

---

### Post by ajt on 2007-11-23
I've ported openMosix to Ubuntu: You can download my deb's of linux-2.4.26-om1 for Ubuntu 6.06.1 LTS from [http://bioinformatics.rri.sari.ac.uk/openmosix]("http://bioinformatics.rri.sari.ac.uk/openmosix"). Please note that you need to install modutils to boot this, or any other, linux-2.4 kernel.

We run openMosix under 'biobuntu', which is a version of [NEBC Bio-Linux4]("http://envgen.nox.ac.uk/biolinux.html") ported to Ubuntu 6.06.1 LTS for bioinformatics work developed as part of an EU funded research project: [http://nbx2.nugo.org]("http://nbx2.nugo.org").

---

### Post by Blutack on 2007-11-23
Beowulf :-)
[http://www.beowulf.org/](http://www.beowulf.org/)

---

### Post by motin on 2008-02-06
I can but tip you about a related thread: [http://ubuntuforums.org/showthread.php?p=4280066](http://ubuntuforums.org/showthread.php?p=4280066)

Cheers,

Fredrik

---


---
title: "Digital DJing software for Linux?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by loobyloo on 2009-03-05
Hi
I was watching a couple of DJs play a gig the other night using mp3s and CDs through Traktor. 
[http://www.download.com/Traktor-DJ-Studio/3000-2170_4-10187054.html](http://www.download.com/Traktor-DJ-Studio/3000-2170_4-10187054.html) 
It was very impressive to watch and hear.  Is there anything similar for Linux?  I've followed a couple of links and they suggest Final Scratch, but is there anything really comparable to Traktor?
Thanks

---

### Post by simtaalo on 2009-03-05
mixxx

---

### Post by loobyloo on 2009-03-05
Thanks!  I'll have a play around with it.

---

### Post by simtaalo on 2009-03-05
its worth going to their website to make sure you get the latest version, there's been alot of bug-fixes since the version in the repo's.

[http://www.mixxx.org/](http://www.mixxx.org/)

---

### Post by djsephiroth on 2009-03-05
> **loobyloo said:**
> Hi
I've followed a couple of links and they suggest Final Scratch, but is there anything really comparable to Traktor?

Yes: it's called [Serato Scratch Live]("http://www.scratchlive.net/"), and it's what the vast majority of DJs with digital libraries are using or moving toward right now; however, it's OSX/Win only. Mixxx looks interesting. I personally wouldn't use it, as I've already got SSL, but it'd be worth investigating so I can compare it to the other DVSes (digital vinyl solutions) out there. Another OSX/Win option in addition to Traktor Scratch and SSL is Torq (which is essentially a cheaper clone of Traktor, in all senses of the phrase). Not really mentioning these to promote them so much as to provide these products as points of reference (well, OK, I  do promote SSL, but hey). If you use Mixxx, let us know what it's like! I may play around with it myself when I've got same free time (got a wedding and a "rave" (the promoter's chosen term for the event, not mine) this weekend).

[EDIT] If you use Mixxx, you will want (read: all but need ) an ASIO sound card. It seems a lot like really old Traktor (not Traktor Scratch that uses control vinyl and CDs, the original Traktor DJ that uses keyboard shortcuts) in that it uses ASIO and/or multiple sound cards instead of specialized hardware to send one audio feed to the mains and another audio feed to the DJ's headphones. Looks like there's not a huge breadth of controllers for it, but they provide resources so you can code up your own solution.

---

### Post by stchman on 2009-03-05
> **simtaalo said:**
> its worth going to their website to make sure you get the latest version, there's been alot of bug-fixes since the version in the repo's.

[http://www.mixxx.org/](http://www.mixxx.org/)

They have an Ubuntu .deb, but it is only 32 bit.

---

### Post by simtaalo on 2009-03-05
> **stchman said:**
> They have an Ubuntu .deb, but it is only 32 bit.

yup i know, is slightly annoying for 64-bit users, but if ya use the build-dep command of apt-get building it from source shouldn't be hard.

or you could follow these instructions

[http://openmaniak.com/checkinstall.php](http://openmaniak.com/checkinstall.php)

---

### Post by Crafty Kisses on 2009-03-05
Mixxx is also in the repos.

---

### Post by simtaalo on 2009-03-05
> **Codename said:**
> Mixxx is also in the repos.

the version in the repo's is pretty old and there's been alot of big fixes in that time, as was stated above.

---

### Post by Crafty Kisses on 2009-03-05
Yeah there is a problem with that version, it crashes like every 5 seconds, it's weird. I'll just try compiling it from source.

---


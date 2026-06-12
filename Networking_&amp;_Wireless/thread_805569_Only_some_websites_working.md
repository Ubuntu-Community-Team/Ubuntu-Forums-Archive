---
title: "Only some websites working"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Happy Hippy on 2008-05-24
**Context**
I've not touched Linux in a couple of years (I think Dapper Drake was due out) but a friend asked me to install it on his Packard Bell Easynote (I can't see the model number anywhere). I've installed Heron and connected to the Internet via ethernet through my wifi router.

I'm currently using a Mac wirelessly through the same router.

**The Problem**
Trying to get the video drivers installed I added a couple of repositories and clicked reload - only a couple of files would download (Release.gpg files but not Translation-en_GB or Release).

Going online I noticed some sites would work (Google, BBC, Badongo) but not others (Rapidshare, Megaupload, speedtest.com among others). All of these sites run fine on my Mac and the speed test measured 2000/180 kbps (on the Mac). I can ping rapidshare at 36ms from the Easynote.

I'm running Safari on the ac and the default installation of Firefox on the Easynote.

Running lspci I see that the ethernet controller is an SiS 191 Gigabit Ethernet Adaptor and I am connected to a wired network according to the network icon in the status bar.

Any ideas, as I'm stumped...

TIA

---

### Post by Bubba64 on 2008-05-24
> **Happy Hippy said:**
> **Context**
I've not touched Linux in a couple of years (I think Dapper Drake was due out) but a friend asked me to install it on his Packard Bell Easynote (I can't see the model number anywhere). I've installed Heron and connected to the Internet via ethernet through my wifi router.

I'm currently using a Mac wirelessly through the same router.

**The Problem**
Trying to get the video drivers installed I added a couple of repositories and clicked reload - only a couple of files would download (Release.gpg files but not Translation-en_GB or Release).

Going online I noticed some sites would work (Google, BBC, Badongo) but not others (Rapidshare, Megaupload, speedtest.com among others). All of these sites run fine on my Mac and the speed test measured 2000/180 kbps (on the Mac). I can ping rapidshare at 36ms from the Easynote.

I'm running Safari on the ac and the default installation of Firefox on the Easynote.

Running lspci I see that the ethernet controller is an SiS 191 Gigabit Ethernet Adaptor and I am connected to a wired network according to the network icon in the status bar.

Any ideas, as I'm stumped...

TIA

Your probably missing the java script.

---

### Post by Happy Hippy on 2008-05-24
Hmmm, that wouldn't explain the lack of repository updates. Also, since posting i see that the Ubuntu website is not one of those willing to load. I really don't think it's a javascript issue (I don't get a blank page or empty plugin box, just a spinning (whatever the name of the spinny thing is - I'd call it a beachball in OSX)).

Another thought - there is no Mac control or encryption currently setup on the router so it can't be that (I disabled all security temporarily just in case).

---

### Post by Bubba64 on 2008-05-24
> **Happy Hippy said:**
> Hmmm, that wouldn't explain the lack of repository updates. Also, since posting i see that the Ubuntu website is not one of those willing to load. I really don't think it's a javascript issue (I don't get a blank page or empty plugin box, just a spinning (whatever the name of the spinny thing is - I'd call it a beachball in OSX)).

Another thought - there is no Mac control or encryption currently setup on the router so it can't be that (I disabled all security temporarily just in case).

Your probably right about the java but the download may be fixed in software sources with clicking download-other to look for fastest responding mirror, have you included medibuntu in the repositories as well.

---

### Post by Happy Hippy on 2008-05-24
Hmmm, on testing servers I get "No suitable download server was found. Please check your internet connection". I immediately googled a random word (blue), got a results page and the second link (wikipedia) is refusing to load (I didn't try the first one which looks like a music website - lots of flashy things there).

I didn't specifically include the medibuntu repository. I left the defaults and added the third party repositories initially.

Thanks so far

---


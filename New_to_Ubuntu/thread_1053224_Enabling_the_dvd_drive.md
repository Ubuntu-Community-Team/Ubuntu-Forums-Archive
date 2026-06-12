---
title: "Enabling the dvd drive"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by rosborne on 2009-01-28
My first post!
I've installed Ubuntu 8.04 successfully on a new Vostro (I partitioned the hard drive soit is 1/2 XP and 1/2 Ubuntu). BUT I can't get the dvd drive to work on Ubuntu - and it does work on XP. When i look at Places>Computer>CDR/DVD+R/W Drive and check Properties I learn that everything is "unknown"  - how do I make it known?
(BTW - the drive is a 16XDVD+/-RW Drive 8X DVD+/-RW with double layer DVD+/-R write capability.
Thanks in advance.
Robin

---

### Post by Arylon on 2009-01-28
My DVD is also listed as "unknown" in the properties dialog, but I've never had any problems using it. I think that the properties refers to the type of disc in the drive and not the drive itself, so if there is no disc inserted, than no type can be determined.

---

### Post by HotShotDJ on 2009-01-28
> **rosborne said:**
> My first post!
I've installed Ubuntu 8.04 successfully on a new Vostro (I partitioned the hard drive soit is 1/2 XP and 1/2 Ubuntu). BUT I can't get the dvd drive to work on Ubuntu - and it does work on XP. When i look at Places>Computer>CDR/DVD+R/W Drive and check Properties I learn that everything is "unknown"  - how do I make it known?
(BTW - the drive is a 16XDVD+/-RW Drive 8X DVD+/-RW with double layer DVD+/-R write capability.
Thanks in advance.
RobinWhat, specifically, have you tried to do without success.  As noted by Arylon, everything is "unknown" when there is no disc in the drive -- this is as it is supposed to be.

---

### Post by rosborne on 2009-01-28
Right you are - but the drive still does not work. 
How do I begin the detaective work?

---

### Post by HotShotDJ on 2009-01-28
> **rosborne said:**
> Right you are - but the drive still does not work. 
How do I begin the detaective work?By telling us what you are trying to do that is not working. :)

EDIT:  Ok.. actually, that response was a little bit snarky... what kind of disk have you inserted and exactly what task(s) are you attempting to perform (eg Video DVD, Music CD, reading a DATA dvd, burning a CD or DVD, etc.)

---

### Post by rosborne on 2009-01-28
In other words I placed a cd in the drive and the computer knows what it is - but there is no action (and I don't hear the spin of the disk in the drive).
Thanks

---

### Post by HotShotDJ on 2009-01-28
> **rosborne said:**
> In other words I placed a cd in the drive and the computer knows what it is - but there is no action (and I don't hear the spin of the disk in the drive).
ThanksSee my above edit (sorry about the originally terse reply -- long day -- just finished digging my car out of wet snow... ugh)

---

### Post by rosborne on 2009-01-28
A music cd is in the drive - Music Player reads the CD, lists the content but no sound (and like I said before no  sign that the drive is spinning the disk).
Hey I'm in NYC and know what you mean about the elements - no problem. Thanks again.

---

### Post by HotShotDJ on 2009-01-28
> **rosborne said:**
> A music cd is in the drive - Music Player reads the CD, lists the content but no sound (and like I said before no  sign that the drive is spinning the disk).
Hey I'm in NYC and know what you mean about the elements - no problem. Thanks again.Actually, this sounds like a SOUND issue.  If the CD were not spinning up, you wouldn't get the TOC listing.  If you haven't already done so, add the volume control to one of your panels (top or bottom, whatever suits you) by right-clicking on an empty space in the panel, click "Add to panel" and then select "volume control" and click the "Add" button.

Now, double-click on volume control and make sure that PCM is not muted in the volume sliders are up.  See if that helps.

---

### Post by rosborne on 2009-01-28
Nope - did what you wrote and no sound. And to add another wierdness - I had loaded Amarok and was playing the radio this morning. Good sound, etc. Now the damn progam will not even launch! No error message, nada.
Argh

---

### Post by HotShotDJ on 2009-01-28
> **rosborne said:**
> Nope - did what you wrote and no sound. And to add another wierdness - I had loaded Amarok and was playing the radio this morning. Good sound, etc. Now the damn progam will not even launch! No error message, nada.
ArghIn the past, I've had problems with CD drives that do not have the analog audio cable attached to the motherboard.  If you are using a desktop PC, it is possible that this is the problem (It might not be... it has been a long time since I've built desktop systems, and I used much older versions of Linux at the time).  On my current computer (a laptop), music CD's worked "out-of-the-box."

Also, you mentioned Amarok -- can I infer that you are using Kubuntu (the KDE version of Ubuntu)?  If so, I better stop trying to help you, because I have not used KDE for quite some time and I'm really unqualified on KDE systems.

---

### Post by rosborne on 2009-01-28
Actually I;m running Gnome 2.22.3. Amarok can be loaded. 
Since last we spoke I rebooted and Amarok is back on board. When I was closing it again I got a "cannot talk to klauncher" message which I fixed thanks to these fab forums. 

****

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---


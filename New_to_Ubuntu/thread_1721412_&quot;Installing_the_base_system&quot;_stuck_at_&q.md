---
title: "&quot;Installing the base system&quot; stuck at &quot;updating the list of available packages&quot;"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by Wobbley on 2011-04-04
I am having issues installing the newest version of Ubuntu Server Edition. I get to the part where it claims to be updating the list of available packages but from there it does not move on. 

I am a complete beginner when it comes to ubuntu besides trying it for a couple of hours when I first registered. Prior to installation I had Windows 7 installed and both my drives were NTFS.

_System Information_
Sapphire Radeon HD4870
Q6600
6GB RAM
150GB Raptor HD
320GB WD HD

Located in Norway
Norwegian keyboard
Behind a router.
Logitech G15 and G9 mouse plugged inn + screen.

_Things I have tried:_
Running the installation several times
Bit confused about the whole partition thing so I have tried several things there.
Pulled out the internet cable so no network connection was detected during installation.
Alt + Ctrl + F1 (Nothing Happens)
Did a disk check

It should not be the CD right? The whole "Updating" thing means it is retrieving data from the net? I am under the impression the system merely freezes at 73%. I was also really unsure what I was doing on the whole partition phase.

---

### Post by smurphy_it on 2011-04-04
If this is a "fresh install" (and not an upgrade) of Ubuntu server, you could try booting with some legacy boot options.  Such as noacpi and noapm, vga=791 is the other if I recall.

I'd also suggest, booting the computer again and when your machine boots up the cd of Ubuntu Server, run the "check CD for defects" option to ensure the media is good.

---

### Post by Wobbley on 2011-04-04
> **smurphy_it said:**
> If this is a "fresh install" (and not an upgrade) of Ubuntu server, you could try booting with some legacy boot options.  Such as noacpi and noapm, vga=791 is the other if I recall.

I'd also suggest, booting the computer again and when your machine boots up the cd of Ubuntu Server, run the "check CD for defects" option to ensure the media is good.

I have checked the disk for defects, burning another CD and going to try the USB approach

---

### Post by QLee on 2011-04-04
[QUOTE=Wobbley]...
I am a complete beginner when it comes to ubuntu besides trying it for a couple of hours when I first registered. Prior to installation I had Windows 7 installed and both my drives were NTFS.
...[/QUOTE]

Well, that information begs the question, why are you installing server edition? You are aware that it won't have X or GUI apps, eh?  Are you intending to use this system as a desktop system or a server system? 
__

---

### Post by Wobbley on 2011-04-04
> **QLee said:**
> Well, that information begs the question, why are you installing server edition? You are aware that it won't have X or GUI apps, eh?  Are you intending to use this system as a desktop system or a server system? 
__

*facepalms* Thanks for the heads up. I think the transition might be too harsh with no GUI at all. Desktop edition it is!


Well it seems like it was the disc after all. Works fine now. Suprised the disc check did not report any errors the first time around. So yeah....solved

---


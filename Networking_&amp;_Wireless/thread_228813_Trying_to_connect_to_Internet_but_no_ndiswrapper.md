---
title: "Trying to connect to Internet but no ndiswrapper?"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by TheIdiotThatIsMe on 2006-08-03
Howdy! I've just recently fresh installed Ubuntu Dapper Drake onto my desktop system with a Netgear 311v3 wireless card and no ethernet (or at least the onboard isn't supported, or something. Anyways, it isn't picked up by Ubuntu). 

Now, having had previous experience in setting up ndiswrapper with earlier Ubuntu versions, I went to go see if I could find and install ndiswrapper off a cd or to see if it was already installed, however, no luck. Well unfortunately, I cant connect to the internet with the computer so I cant go into the repositories and download the program. So I went to my stepdad's computer who I had loaded with Ubuntu Breezy Badger a while back (and who's I will NOT update due to the severe problems of my last update on my desktop that forced a clean reinstall). Anyways. I went onto synaptic and downloaded ndiswrapper-utils and ndiswrappergtk since by reading the description it said ndiswrapper was already built in and just needed something to configure it. So I download them through Synaptic and take it to my desktop; however they dont install due to conflicting versions (probably obviously because of the difference in OS Version).

Is there any way to get ndiswrapper working on my Ubuntu Dapper Drake? I have a useless system that is sitting there and it's really bugging me because it is my only system besides my laptop which needs Windows for college. Or is there any distro that comes with ndiswrapper built in and ready to configure?

---

### Post by az on 2006-08-03
There is a repo on the live cd that is apart from the live session.

While at your Dapper desktop, insert the live cd again and the package manager will start.  Install the proper version of ndiswrapper-utils from there,

Ad to upgrade Breezy, use the update-manager - it wil take care of the little niggles for you.  Click on the "install new version" tab.

---

### Post by TheIdiotThatIsMe on 2006-08-03
I had just tried that (it is the Dapper Drake live/install combo cd I used since it's Dapper Drake without internet) and it couldn't seem to find ndis-utils, although I will definately try again!

---

### Post by az on 2006-08-03
It's ndiswrapper-utils.  Don't boot from the cd.  Stick it in once you booted your installed ubuntu.

---

### Post by steveob on 2006-08-04
Try "sudo apt-get install ndisgtk".  Just worked for me and installed ndiswrapper-utils and all dependencies.  Good luck.

---


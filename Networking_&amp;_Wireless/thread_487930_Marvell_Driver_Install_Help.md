---
title: "Marvell Driver Install Help"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by mfm3 on 2007-06-29
OK, I have searched and searched. I give up on searching. Can someone please lend an ear.....
Situation:
I am at work. We have a proprietary software program for resurfacing polygon meshes. We run it on linux, naturally. The old version runs on debian. We are trying to build version 2. I chose Ubuntu, because I have had great experiences with it in the past. 
So we got this little box and got everything running just right, then realized we need the GPU of an nVidia GeForce 6xxx series or higher card to get the SDL to cooperate or something like that. (The guy who wrote the program failed to mention this when we were setting up the hardware). So we have to move to a full size case to fit the Video card. Problem is that we want to save the Ubuntu install that we already have. So we matched the hardware as best we could, got new stuff and a new case, and moved over the hard drive. Begin problem.

xorg.conf is setup for the integrated intel graphics. After a while I was able to get that taken care of. It uses the card, but I don't have the latest driver on there, which I would like to get. This will come later...

I cannot get the integrated NIC to work. Ubuntu sees it, (lspci, device manager), but won't use it. I need the driver. Found how to get and install the driver, only there's one problem:
I need the kernel-headers installed to install the Marvell driver. Without a connection to any repositories, how can I install the kernel headers? Live CD? Where?

Thanks to anyone who took the time to read this, and extra special thanks in advance if anyone can help me out.

---

### Post by mfm3 on 2007-07-12
Problem has been resolved, but just out of curiosity, did anyone even read this? If I need help from this forum and cannot find a relevant existing post after hours of searching, where or how should I go about posting my question in a way that someone will see it and try to help me? Thanks.

---

### Post by fredj on 2007-07-13
Yes someone did read this but only after you had already solved the problem. Unfortunately there are
many people posting here who need help so it takes some time to read them all.

---


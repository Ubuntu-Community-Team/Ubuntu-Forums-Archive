---
title: "Peer-to-Peer with multiple OS's .. how to?"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by tj.baker on 2008-01-14
Hello All,

After doing some reading, and a bit of searching for more readings, I am at a bit of a loss.

The Samba tutorial was fantastic, and I think I could follow it to get Samba running if indeed that is what I need to do - but the problem is, I'm not sure if that is the best solution for me or not.

Here's what I wish to accomplish and a bit about what I have hardware wise:

I have 3 different systems each with a different OS, and I'd like to set up a peer-to-peer between them all.  
The Edubuntu system I have is wired to my router, and the other two (laptops) access the internet wirelessly - with one having Windows XP and the other OS X.

The main thing I would like to be able to do is have our printer hooked up to the Edubuntu system and be accessible from the laptops - as well as have the external HD that's on the Edubuntu system be available to the laptops for storage purposes.

I had all of this going on another Windows system, but it decided to die on us -- and now I am at a loss.

Is Samba the way to go here?  Or is there another way to go about doing these things?

Thank you any and all who are willing to help out a complete noob - and I am sorry if I missed anything that might have already covered this (if so, may the mods have mercy and just combine my thread with said info....)

peace,

tj

---

### Post by sqrt2 on 2008-01-14
Well, Samba is the only thing that works with out-of-the-box with Windows. Although it can be a little tricky to get working, it also works well with Linux. I've had some problems with discovering computers on the network using OS X, but since you only have three boxes, that shouldn't be a problem here. (Command-K in Finder and connecting to "smb://<hostname>/" always worked.)

Samba should be pretty much what you want.

---

### Post by tj.baker on 2008-01-14
Fantastic!

Thanks so much for the fast reply.

I'll get on that tutorial and we'll see how it goes... :)

peace,

tj

---


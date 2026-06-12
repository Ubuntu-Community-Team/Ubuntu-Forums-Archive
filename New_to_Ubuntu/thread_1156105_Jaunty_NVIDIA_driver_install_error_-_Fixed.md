---
title: "Jaunty NVIDIA driver install error - Fixed?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by MaxVK on 2009-05-11
Hi there, I hope this helps someone else having problems installing the NVIDIA 180 drivers from the restricted drivers manager.

**The Problem**
I would click to activate the drivers in the restricted drivers manager.
A download percentage box would open.
Nothing on my router would flash to show that a connection was being tried, and the percentage would stay at 0% until an error shows up, explaining that Jockey has crashed.

**The Solution**
I was fiddling with my software and an installation asked for the Jaunty CD. I put the disk in the drive and everything went fine. I then tried the NVIDIA driver (again!) but this time it fired up the CD and installed the drivers!

My guess is that something in the restricted drivers manager is broken, and prevents it asking for the CD, so it just sits there until it times out or whatever. But if the disk is in the drive things just seem to work without a problem.

I have no idea if this is an actual workaround for the problem in general, but it worked for me - here's hoping it works for you if you have the same problem.

Regards

Max

---

### Post by Didius Falco on 2009-05-11
Hi Max,

Open **System/Administration/Software Sources** and see if the box for the Jaunty CD is checked at the bottom of the first tab. If it is, uncheck it - otherwise you'll face the same problem later.

I should have thought of that last night when I was typing that message to you...

Regards,

Didius

---

### Post by MaxVK on 2009-05-11
Hey Didius - Yes it was already checked (by default).

My point was that so far the driver installation has always failed, but this time, because the CD was actually in the drive, it worked straight away.

I'm thinking that the dialog that *should* open and ask you to insert the CD doesn't actually open, which leaves the installer high and dry until a timeout occurs. When the CD was already in the drive there was no pauses or hanging about and the drivers were installed successfully.

This post is just to let others know how I got it to work in case it helps them.

cheers

Max

---


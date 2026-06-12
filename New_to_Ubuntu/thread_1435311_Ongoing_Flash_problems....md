---
title: "Ongoing Flash problems..."
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Everynameistaken on 2010-03-21
I'm running 64-bit Ubuntu.  The other day, sound stopped working for Flash videos in Firefox.  

I tried restarting Firefox and the computer, but it didn't help.  I tried removing the version of Flash I had installed and reinstalling, but it didn't help.  I removed the alpha version of Flash I was using entirely and installed whatever version is in the Software Center, but it seems way more buggy.

So I'm stuck between using Flash with no audio and using Flash that doesn't play a lot of videos properly at this point.  Any help?

---

### Post by Everynameistaken on 2010-03-21
Apparently not.

---

### Post by sandyd on 2010-03-21
see link in sig.

---

### Post by Everynameistaken on 2010-03-21
Nah, still no sound.  I'd assume that installed the same 64-bit alpha I was using previously.

---

### Post by Everynameistaken on 2010-03-21
I've been playing around with JACK a lot lately.  I can't imagine why it would, but can that possibly affect the sound settings for particular programs?

It's stupid, but I'm scraping the bottom of the troubleshooting barrel.

---

### Post by Everynameistaken on 2010-03-22
Tried reinstalling Firefox too.  No dice.

---

### Post by teeliina on 2010-03-23
Hi! I recently wrestled a similar problem of not having any sound at all and flash not working after reinstalling karmic. I tested the changes/installations with youtube videos, and the adobe flash which youtube site link offers (in case you don't have flash at all) for ubuntu 9.04+ made the videos play, and installing of Pulseaudio and Gstreamer extras from software center brought my sounds back.

---

### Post by masux594 on 2010-03-23
Try this one.. I've had the same problem.. but this has solved it..

# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

Sysc, A

---


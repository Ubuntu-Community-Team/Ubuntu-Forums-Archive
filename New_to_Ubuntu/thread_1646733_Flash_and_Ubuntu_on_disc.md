---
title: "Flash and Ubuntu on disc"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by JoeBob9 on 2010-12-16
I am a new user of Ubuntu. My friend gave me a 10.04 boot disk and I think I like it. I have a problem when I use Ubuntu using only the CD. When I go to Youtube or other site that uses Flash videos, I just get a blank square where the video should be. Is there a way to use Flash on Ubuntu without installing it onto a hard drive? That is, I just want to use the boot CD.

---

### Post by seawolf167 on 2010-12-16
Flash is a proprietary format, you'll need to do the following to be able to play it

Open a terminal (Accessories -> Terminal), then type in the following:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by JoeBob9 on 2010-12-16
It did not work. Here is what I saw in terminal view after typing what you suggested:
 
Reading package list .... Done
Building dependency tree
Reading state information ... Done
E: Could not find package ubuntu-restricted-extras
 
Is there something I need to have available on USB stick, as I am only using the Ubuntu boot disk?

---

### Post by CharlesA on 2010-12-16
If you are booting off a livecd, you'd have to install flash and whatnot every time you boot off of it, since a livecd is run in memory, and nothing is saved to the disc.

---

### Post by JoeBob9 on 2010-12-16
How would I do that?  I guess I expected something similar.  Would it be possible to load the Flash from the liveCD or would I have to use a USB stick to load from?

---

### Post by JoeBob9 on 2010-12-16
I have done a little research and am ready to create my own LiveCD, but don't know which one to use.  If I can make one that has a browser (like firefox, or other), works with WiFi (my laptop works with this 10.04 version) and a way to view online Flash video.
 
I have narrowed it down to two that I have been able to find:
 
1) Ubuntu Linux (not sure if I can make a LiveCD that can view Flash video)
2) Linux Mint.  Seems to have Flash available when making the LiveCD
 
Any suggestions - or can I salvage this 10.04 version to use Flash?

---

### Post by uRock on 2010-12-16
I have the LiveCD image on a thumb drive that is able to store additions, such as the installed Flash from the adobe site.

LinuxMint's LiveDVD does have flash on it. Their LiveCD does not have flash.

---


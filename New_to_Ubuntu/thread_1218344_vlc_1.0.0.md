---
title: "vlc 1.0.0"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by DarinB on 2009-07-20
not sure how to upgrade my vlc to vlc 1.0.0 for jaunty???

---

### Post by VCoolio on 2009-07-20
you could add these repos:
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main

---

### Post by NightwishFan on 2009-07-20
In order to get 1.0, you should use use a version from PPA.

[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)


How to use a PPA:

[https://help.launchpad.net/Packaging/PPA#Installing%20software%20from%20a%20PPA](https://help.launchpad.net/Packaging/PPA#Installing%20software%20from%20a%20PPA)

---

### Post by eragon100 on 2009-07-20
You would get vlc 1.0 on your system if you followed those instructions, but I suggest you don't. Version 1.0 doesn't have many spectacular new features/improvements (not counting blu-ray support) and, for me at least, it has tons of problems which earlier versions didn't have. The most prominent among them is that it plays videos with a pretty bad lag, almost like a slide show. This makes videos a lot less fun to watch, and it happens with every video I try to play with it, not just the HD fullmetal alchemist episodes. VLC is the only player which has this problem on my pc :(

If I were you, I would keep using totem, because, at least in my experience, it is a lot more stable and faster than VLC :wink:

---

### Post by DarinB on 2009-07-20
ewww the last post does not sound good, problems i do not want. the only thing i do want is a way to keep the equalizer to stay put i do not have a save button it is situated behind the close button and no matter what my screen res is at or font sizes i can't see it. not sure if it is a bug or not. so i think i will leave well enough alone. better to have what i have than to break something. thanks all

---

### Post by NightwishFan on 2009-07-20
I cannot argue as I have never tried 1.0, though I doubt you would fight issues like that on a stable release.

The official (older not 1.0) release in jaunty is buggy. Example being that it does not follow the UI preferences I give it. It stubbornly keeps the video in a separate window. That is the biggest issue though.

---

### Post by SuperSonic4 on 2009-07-20
> **eragon100 said:**
> You would get vlc 1.0 on your system if you followed those instructions, but I suggest you don't. Version 1.0 doesn't have many spectacular new features/improvements (not counting blu-ray support) and, for me at least, it has tons of problems which earlier versions didn't have. The most prominent among them is that it plays videos with a pretty bad lag, almost like a slide show. This makes videos a lot less fun to watch, and it happens with every video I try to play with it, not just the HD fullmetal alchemist episodes. VLC is the only player which has this problem on my pc :(

If I were you, I would keep using totem, because, at least in my experience, it is a lot more stable and faster than VLC :wink:

Speak for yourself, VLC 1.0 is working perfectly on my arch system. Furthermore they finally merged them into one window again

---

### Post by eragon100 on 2009-07-20
> **SuperSonic4 said:**
> Speak for yourself, VLC 1.0 is working perfectly on my arch system. Furthermore they finally merged them into one window again

I had the same problem with the seperate windows, and it's indeed fixed, which is great. However, the video playback is very slow. I never said it was slow for everyone, I only said it is for me, which is true. For me, there is a very noticable difference between vlc with it's own internal codecs, and other video players, wether they use gstreamer or xine.

---

### Post by DarinB on 2009-07-21
i added the software sources but i don't see the vlc 1.0.0 in synaptic i added the key with the sudo key 
i added a screen shot of sources any ideas on what i am missing???? i do like the idea of getting rid or the all in one vlc!!!![ATTACH][ATTACH]121909[/ATTACH][/ATTACH]

---

### Post by SuperSonic4 on 2009-07-21
I don't see a problem? Have you ran ```
sudo apt-get update
``` before checking, especially if you added it via a terminal. You may also need to authorise it

---

### Post by PGScooter on 2009-07-21
vlc 1.0 is running pretty well for me. I've had a couple of small problems. When watching videos and skipping around in them (by dragging the tracker) it lags/freezes much more than .9. However, I am sticking with 1.0 because I want to help with development by reporting bugs. By the way, there are good vlc forums:

[http://forum.videolan.org](http://forum.videolan.org)

---

### Post by DarinB on 2009-07-22
huh it didn't take the first time but this time it did! thanks vlc  rocks, i am happy to have one screen haven't seen that for a few versions i had it on feisty with vlc, then it was taken out...... 
anyone that doesn't love vlc must have problems with their system and compatibility. 

**i do not have a save button on the graphic equalizer though i think it is behind the close button but i can't see it even if i reduce my font size and increase my screen res it still does not come up. has any one had this problem?????**

---

### Post by SuperSonic4 on 2009-07-22
> **DarinB said:**
> huh it didn't take the first time but this time it did! thanks vlc  rocks, i am happy to have one screen haven't seen that for a few versions i had it on feisty with vlc, then it was taken out...... 
anyone that doesn't love vlc must have problems with their system and compatibility. 

**i do not have a save button on the graphic equalizer though i think it is behind the close button but i can't see it even if i reduce my font size and increase my screen res it still does not come up. has any one had this problem?????**

Glad you like VLC but SMplayer is my preferred player for Quicktime files (although I'm thinking converting them to mp4 or something nicer)

---


---
title: "There is a problem with sound"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by nj96 on 2009-02-15
On ubuntu, whenever I boot up, there were always 3 things that had to do with ubuntu and one was windows. When I booted ubuntu up though, there seemed to be a problem and when i restarted it, more than 3 things came up that had to do with ubuntu! When I clicked on it, it worked. everything seemed to be working fine but when I booted her up, the sound wasn't working. I checked if it was muted or not. It was muted but when I made it normal and when I played a song, all I heard was crackling. Please help.:confused:

---

### Post by vwilsonuk on 2009-02-15
Have you checked the "PCM" slider isn't set to mute as well? (Right click volume, "Open volume control", see if there's PCM on the playback tab)

A recent update muted the PCM slider without user intervention, and there's an open bug that some soundcards produce crackling and no other sound when PCM is set to mute. 

Apparently it's been going on five months, and the PulseAudio team still release updates that mute your PCM slider without intervention. I spent several hours trying to debug my sound driver earlier in the week, only to discover this was the problem (hence the vitriol).

---

### Post by nj96 on 2009-02-15
thanks a million. I had alot of trouble and now it works fine.

---


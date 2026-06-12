---
title: "Sound stops working on 11.04... My fix"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by 4Orbs on 2011-05-01
This is what fixed my problem of disappearing audio in Unity and Xfce desktops.

Sound works fine at first. But when I logout and then login again the audio stops working. Rebooting makes the sound work again.

I've discovered the source of the problem (in my case, anyway). All my media files (mp3,avi,mp4,mkv) are stored on a different partition than the Ubuntu installation. After mounting that partition to play media, then logging out... the partition is still mounted upon logging back in, but is not accessible to the media player or user.

The Fix: Un-mount (eject) the media storage partition before logout.

---


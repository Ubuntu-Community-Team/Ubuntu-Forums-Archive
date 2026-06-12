---
title: "Creative Zen"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by coty26 on 2010-10-24
Hi, i just upgrade my ubuntu from 10.04 to 10.10 and now i can't use my creative zen. I've tried almost everything that i found in the forums, specially with banshee, but even when the computer recognized the device, when i try to open with banshee it crash and the zen too. I've had to reset it each time. I Also tryed with VLC, but is not way to export music. 
Then  ve' tried just dragged  from the music folder to zen, but even when its look like it worked, it doesn't. But when i look on the properties, the space is been used, but i can't see the music files. 

Thank you for the future help.

---

### Post by Dude-PWB- on 2010-10-24
My wife has a Zen. When I finally convinced her to get rid of windows altogether and go completely with Ubuntu, that was the first issue she came across.

She doesn't like command line at all, but once I installed mtp-tools and copied a few commands into a text file for her, it was a breeze. She even converts video files herself now with some commands I also added for her. She was never able to successfully do it with the windows program before, so she is even happier.

Most of the commands came from this site: [http://www.mossroot.com/worlds/2008/11/22/connecting-the-creative-zen-x-fi-to-linux/](http://www.mossroot.com/worlds/2008/11/22/connecting-the-creative-zen-x-fi-to-linux/)

Basically once you get mtp-tools installed and mtp-detect detects your zen you can transfer files to it by using:

```
mtp-connect --sendfile songname.mp3
```

And, it doesn't require you to specify the directory to put it in or anything, it automatically puts it in the proper directory.

Hope this helps.

---


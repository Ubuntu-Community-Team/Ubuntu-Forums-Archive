---
title: "Choppy video in Movie Player"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Edward in CT on 2010-08-18
When I try to play a MOV video in Movie player, it plays very choppy.  Audio is ok but video doesn't play well.  Can anyone help?  Thanks.

---

### Post by tufcamman on 2010-08-18
What are the specs of the computer you are using?

---

### Post by Edward in CT on 2010-08-19
Aspire one netbook intel atom processor
ubuntu 10.04 lucid lynx
gnome desktop
movie player came with it.

Any thing else?  Thanks

---

### Post by Oppermongo on 2010-08-19
Use VLC instead, works much better ;)

---

### Post by tufcamman on 2010-08-19
Ahh, your problem is probably that you computer simply doesn't have enough processing power to play back your video.  Fire up a terminal, run top (htop if you want to install it) and play back your video.  Most likely you will see your cpu spike up to 100 percent.  

I know that I had an atom based netbook and it was unable to playback anything above 480i.  (You can find out info on the video your playing with ffmpeg -i <video file> [You'll need to apt-get ffmpeg]).

Sorry I can't help you more, you can use ffmpeg to encode the video file to a smaller, easier to play format that you're netbook would handle.  Good luck.

---

### Post by no2498 on 2010-08-19
you may also try this

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope that helps

---

### Post by Thomas Garman on 2010-08-19
I watch movies, both ordinary DVDs and .avi files, on my ACER ASPIRE ONE D250 all of the time.  For DVDs I use an external USB DVD.  The Hyperthreading Intel Atom processor is perfectly fine.  If the video playback is choppy it must be your codecs... so...

---

### Post by Jazzy_Jeff on 2010-08-19
Install VLC, it is the best video player out there. If you are still having problems with this let us know.

---

### Post by jtarin on 2010-08-19
VLC vote.....most codecs you will need.

---

### Post by Edward in CT on 2010-08-20
VLC is the bomb!!!!!  My choppy days are over.  Thanks to everyone.  Once again, ya'll rock!!!

---


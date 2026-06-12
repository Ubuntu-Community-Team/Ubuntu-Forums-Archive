---
title: "PiTiVi Woes. Can't play back video in real time and can't save to H.264 or VP8"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by osc1882 on 2010-06-27
YO!
Maybe someone can help me out. Technical issues is killing my Vlogg. I just Re-stalled ubuntu hoping it would help with some of these problems... It fixed a few but others are still happening.

I just got a H.264 Pocket Camcorder and I have the newest Gstreamer including the ugly and bad ones and I used a guide to install H.264 and VP8. I'm recording 720p. 

One! 
If I right click on a clip and say play then it plays inside of the program no problem. BUT, if I try to play from the time line it plays the audio in real time but I only get a new frame or two every 2-5 secs. This does not work if I want to do even the most basic editing because I can't even watch the video let alone find the correct spot for cutting.

Two!
If I try to save to X.264 or VP8 and hit encode the encoding doesn't get anywhere. It starts on the first frame and stops, never moves a inch. I would really love to save to ether of these formats in order to not lose any video quality (what's the point of saving to 720 if it looks horrable after the encude) and I would love to save on file space. 

So any ideas on both of these? 

I problem I had before the reinstall of ubuntu is, if I encoded to Ogg Theora and played it back it looked great on my computer but after uploading it to youtube it came out as..... super warped video. As in didn't look anything like the original video. It was one of those... who knows what setting or update I did that messed that one up kind of things. I'm going to try to upload to youtube again here in a bit to see if the fresh install fixed that.

---

### Post by -humanaut- on 2010-06-27
Try downloading the h.264 codec from synaptic.

---

### Post by repunante on 2010-11-22
> **osc1882 said:**
> YO!
Maybe someone can help me out. Technical issues is killing my Vlogg. I just Re-stalled ubuntu hoping it would help with some of these problems... It fixed a few but others are still happening.

I just got a H.264 Pocket Camcorder and I have the newest Gstreamer including the ugly and bad ones and I used a guide to install H.264 and VP8. I'm recording 720p. 

One! 
If I right click on a clip and say play then it plays inside of the program no problem. BUT, if I try to play from the time line it plays the audio in real time but I only get a new frame or two every 2-5 secs. This does not work if I want to do even the most basic editing because I can't even watch the video let alone find the correct spot for cutting.

Two!
If I try to save to X.264 or VP8 and hit encode the encoding doesn't get anywhere. It starts on the first frame and stops, never moves a inch. I would really love to save to ether of these formats in order to not lose any video quality (what's the point of saving to 720 if it looks horrable after the encude) and I would love to save on file space. 

So any ideas on both of these? 

I problem I had before the reinstall of ubuntu is, if I encoded to Ogg Theora and played it back it looked great on my computer but after uploading it to youtube it came out as..... super warped video. As in didn't look anything like the original video. It was one of those... who knows what setting or update I did that messed that one up kind of things. I'm going to try to upload to youtube again here in a bit to see if the fresh install fixed that.


Any progress? I'm having the same playback problem (I don't know about the encoding, it is virtually impossible to edit anything) and it is driving me crazy.

---

### Post by no2498 on 2010-11-22
you can try this
and a restart of the computer is a must
it comes from the program cheese

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you

---

### Post by repunante on 2010-11-23
> **no2498 said:**
> you can try this
and a restart of the computer is a must
it comes from the program cheese

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you


Hi no2498,

Thanks for the help. I tried what you suggested in two computers I have:

1. Intel Atom 330@1.60 Hz; 2 GB Ram (Ubuntu 10.10, kernel 2.6.35-23)
2. Intel T1300@1,66Hz; 1 GB Ram (Ubuntu 10.04, kernel 2.6.32-25)

In the first computer it kind of worked, the playback didn't stop but in the transition from one video to another in a normal playback made the program collapse.
In the second computer it didn't make any noticeable difference.

In any case, the small improvement in the computer No 1 suggest that it is a problem with the power that the software requires from the CPU, isn't?

---

### Post by repunante on 2010-12-01
> **repunante said:**
> Hi no2498,

Thanks for the help. I tried what you suggested in two computers I have:

1. Intel Atom 330@1.60 Hz; 2 GB Ram (Ubuntu 10.10, kernel 2.6.35-23)
2. Intel T1300@1,66Hz; 1 GB Ram (Ubuntu 10.04, kernel 2.6.32-25)

In the first computer it kind of worked, the playback didn't stop but in the transition from one video to another in a normal playback made the program collapse.
In the second computer it didn't make any noticeable difference.

In any case, the small improvement in the computer No 1 suggest that it is a problem with the power that the software requires from the CPU, isn't?


No changes, PiTiVi is not working properly in those computers and neither OpenShot. It is curious how I could edit video in Windows using Vegas and so far it is not possible the same edition in Ubuntu on the same machines.
Fortunately I still have Kino, not that intuitive but perfectly stable.

---


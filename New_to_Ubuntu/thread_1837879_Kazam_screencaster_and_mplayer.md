---
title: "Kazam screencaster and mplayer"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by beew on 2011-09-02
Hi,

I was playing around with Kazam, I made a random recording of my desktop and saved the output. When I played the output file with mplayer it was all screwed up (tried both mplayer and mplayer2 and results were the same), VLC just crashed without even opening the .mkv file. However, playback in Totem and Banshee was perfect.

See the attached screenshots, left one is from mplayer, right one is from Totem.

Why is it that mplayer and VLC can't play the clip while Totem and Banshee can? 

Thanks

P.S. I am using Ubuntu10.10

---

### Post by beew on 2011-09-03
Ok, I figured it out. It turns out that playback is ok if I switch video output in mplayer from vdpau to xv, and disble GPU acceleration in VLC.  So it seems that the videos created by kzam for some reasons can be played with GPU acceleration.

I would like to learn why that is so. Thanks.

---

### Post by beew on 2011-09-03
Anyone?

---

### Post by beew on 2011-09-04
Bump!

---

### Post by beew on 2011-09-05
If I pass the .mkv file through handbrake (which results in a smaller .mkv file) then the playback is ok with vdpau enabled. I would like to know what is the mechanism involved.

---

### Post by beew on 2011-09-06
Hi, anyone???

---

### Post by beew on 2011-09-20
bump!

---

### Post by beew on 2011-09-23
Bump!

---

### Post by Denver Dave on 2011-09-23
You're a head of me,  in 11.04 how did you manage to get kazam installed?

Is there another screen recorder included with ubuntu that I'm missing?

---

### Post by beew on 2011-09-24
> **Denver Dave said:**
> You're a head of me,  in 11.04 how did you manage to get kazam installed?

Is there another screen recorder included with ubuntu that I'm missing?

To install kazam

[https://launchpad.net/~and471/+archive/kazam-daily-builds]("https://launchpad.net/%7Eand471/+archive/kazam-daily-builds")

Yes, there are other screen recorders like recordmydesktop, which is garbage as it cannot handle Compiz, there is xvidcap but audio doesn't work in Ubuntu, apparently it is disabled deliberately for some reasons. Kazam seems to be the best except for the problem I posted here.

---


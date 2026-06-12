---
title: "Video's freeze (Jaunty)"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-25
Having another problem with jaunty.

The video freezes whenever I play any video in full screen. This has happened with VLC and smplayer and with a variety of video and video formats.

This did not happen in intrepid. Any thoughts? Anything I should try or check?

---

### Post by abhiroopb on 2009-04-25
Update: This applies also even if the video is not in full screen. It just hangs at random points. The video freezes for a brief period (the audio continues fine) and then the video starts up again. This is highly irritating! Does not have anything to do with compiz, as if I disable compiz, it still freezes.

Again this happens in both Smplayer (here it freezes completely, and doesn't even restart) and in VLC (where it freezes and restarts).

I feel like tearing my hair out. Its almost completely impossible to watch videos now.

---

### Post by abhiroopb on 2009-04-26
Bump :)

---

### Post by dazzlingtanish on 2009-04-26
I have the same problem. Does anybody have a solution for this ?

---

### Post by abhiroopb on 2009-04-26
At least not going insane by myself!

---

### Post by karda on 2009-04-29
I have similar problem with my Toshiba Portege M200 laptop (Centrino 1.5Ghz, 1Gb RAM, NVidia GeForce Go5200 with 32Mb VRAM). I have recently upgraded to 9.04 from 8.10. Video playback in VLC, MPlayer and Totem (gstreamer based version) is sluggish. Sound is playing fine but the video loses synchronisation after a while. It slows down for couple of seconds and then speeds up to hyperspeed and slows down again. It looks as if there was something wrong with the decoding buffer handling, fe. it is filled in the beginning and the first buffer chunk is played fine (synchronised and with correct speed). What I think is happening is that during the playback of the first buffer chunk, the buffer is not filled with new data, so when the chunk ends then player tries to compensate by decoding on the fly which gives the sluggish performance. I'm not familiar with how video decoding is done in linux so I'm not sure if this is true. What I can say is that changing buffer size in mplayer and restarting it leads to different moments when video starts acting as said above. 
I've tried to install latest versions of ffmpeg, libavcodec, mplayer, smplayer and the result is the same. I've tried to install packages from ubuntu 8.10 but to no avail. Lastly I've tried to install the 169.xx NVidia driver but it seems that it doesn't want to compile against 2.6.28-11-generic kernel (official ubuntu jaunty kernel). I'm not sure if it is a problem with video drivers though. I've tried to run some 3D games (Aquanox, Ragnarok Online) and they seem to be working fine.
I've also tried changing video outputs in mplayer. I've tried xv, gl, gl2, x11, sdl...all with the same effect.
I've tried using the nv xorg video driver but video is just slow all the time.

I'm out of ideas... :(

---

### Post by rvm4000 on 2009-04-29
Did you try to change the audio output too?

---

### Post by karda on 2009-04-30
I've just tried to do that. Changing to oss or esd seems to solve the problem. Might it be a problem with pulse gnome integration? Alsa is also giving me slowdowns but I have my primary alsa device linked to pulse device:

my .asoundrc
```
pcm.!default pulse
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.bt820 { 
    type bluetooth
    device "00:07:A4:B6:09:6C"
    profile "auto"
}
```

---

### Post by Neville Grech on 2009-05-02
This is happening for me as well, usually the first few seconds are fine. Then video starts hanging... going fast ... hanging ... etc..

Maybe someone should file a ticket

---

### Post by benjamin222 on 2009-06-10
Same thing happening to me, video playback is horribly slow and choppy, and putting into full screen causes the system to crash.

Any way to fix without changing audio to OSS?

---


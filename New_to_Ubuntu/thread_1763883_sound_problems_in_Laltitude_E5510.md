---
title: "sound problems in Laltitude E5510"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by aam-aadmi on 2011-05-21
Hi,

I have just installed Ubuntu 10.04 on a Latitude E5510. I am having trouble with sound playback in firefox.

I followed [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

and did

```
gnome-volume-control
```

to check the volume controls; it looked okay. Then I did 

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

and I could hear the voice saying "Front", "Center".

But when I play a video from a website I hear no sound (though I can see the video).

Any advice?

Aam-aadmi

---

### Post by frogo on 2011-05-21
> **aam-aadmi said:**
> Hi,

I have just installed Ubuntu 10.04 on a Latitude E5510. I am having trouble with sound playback in firefox.

I followed [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and did

```
gnome-volume-control
```to check the volume controls; it looked okay. Then I did 

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```and I could hear the voice saying "Front", "Center".

But when I play a video from a website I hear no sound (though I can see the video).

Any advice?

Aam-aadmi


I was about to suggest installing gstreamer stuff from the restricted-extra package, because this is what enabled playing video (with sound) on my Dell Latitude e4310. But I see from another thread that you did that already...

---

### Post by aam-aadmi on 2011-05-21
Yes, I have already installed the "ubuntu-restricted-extra" packages. I can play music (from a CD, for instance) but when I stream video on the web using firefox, there is no sound. The video works just fine.

I have installed Real Player too, but that doesn't help either. Any further suggestions?

Aam-aadmi

---


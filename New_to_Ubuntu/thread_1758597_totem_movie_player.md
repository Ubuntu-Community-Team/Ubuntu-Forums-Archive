---
title: "totem movie player"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by redspotss on 2011-05-14
anyone know how to get the totem player to play my hd videos from my camcorder ? it tries to play them but it's real choppy , the videos are recorded in mov h264 codec res is 1280x720 30fps , any help would be great

---

### Post by wojox on 2011-05-14
Maybe more codecs. Copy and paste this in the terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install non-free-codecs
```

---

### Post by redspotss on 2011-05-14
tried no go still choppy .

---

### Post by no2498 on 2011-05-15
install smplayer just type it in a terminal it tells you how to install it
if still no joy try
in the terminal type gstreamer-properties click enter

click video

keep a note of what the/your plug-in is
change the plug-in to x window system no xv

hope that helps

---

### Post by kerry_s on 2011-05-15
try vlc, it can buffer to help sdcard slow speeds

---

### Post by no2498 on 2011-05-15
! kerry_s you know i have seen kids as young as 10 ask  questions  as young as 10 in these forums so why the wtf

---

### Post by kerry_s on 2011-05-15
> **no2498 said:**
> ! kerry_s you know i have seen kids as young as 10 ask  questions  as young as 10 in these forums so why the wtf

your talking about under my name?
if so, it's because it's something i commonly say or think. even a kid as young as 10 already knows what it means & most likely uses it chatting with other young'ins, so i don't really see the big deal.

i doubt you seen anyone, this is the net, you can say your how ever old you want to be, you can only guess how old someone is.

anyways, i'm not changing it, you can report me & if a mod asks me to change, only then will it be changed.

---


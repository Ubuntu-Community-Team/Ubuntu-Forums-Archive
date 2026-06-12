---
title: "Can't play MP3 files"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by retskrad on 2009-01-02
Why can't I play MP3 files?? I have downloaded this file:
[http://rapidshare.com/files/179088585/2Pac_-_06_-_Runnin___Dying_To_Live_.mp3.html](http://rapidshare.com/files/179088585/2Pac_-_06_-_Runnin___Dying_To_Live_.mp3.html)

I have tried to open it with VLC, ttoem, amorak, rythmbox, none works. I get no sound, the track doesnt even go.

Ina dditional, if it helps, I downloaded the restricted stuff..

Also, I have tried to play other mp3, I get no sounds or whatsoever..

---

### Post by Brafil on 2009-01-02
maybe you need the codecs: sudo apt-get install ubuntu-restricted-extras will do everzthing (But its kinda big)

---

### Post by retskrad on 2009-01-02
I already wrote it in my first post, that I've already done that.

---

### Post by abn91c on 2009-01-02
you need to install the mp3 addons file, its in the repositories. search for this in synaptic  [COLOR="Red"]li**[COLOR="Red"]bxine1-ffmpeg[/COLOR]**[/COLOR]

---

### Post by Law506 on 2009-01-02
is that .html still on the file extentsion?  could try removing that and see what happens.

so it just ends in .mp3

---

### Post by retskrad on 2009-01-02
No, its just rapidshare that oputs html. download it and it will become mp3.

---

### Post by retskrad on 2009-01-02
I already had libxine1-ffmpeg on my computer.

---

### Post by abn91c on 2009-01-02
I had that problem with amarok the other day when i updated to amarok 2.0, i ended up having to purge amarok from the system, reboot then install the default amarok then sudo apt-get amarok-kde4 to get it to play my Ipod video mp3's

---

### Post by retskrad on 2009-01-02
But why doesnt it play on vlc, rythmbox, totem, amorak.. I have the codec..

---

### Post by retskrad on 2009-01-02
Other stuff works like youtube, but nto mp3s..

---

### Post by stoogiebuncho on 2009-01-02
I've always used the GStreamer set of codecs for mp3 playback.  They are in the Add/Remove.

Have you been able to play MP3's on this computer in the past?

---

### Post by retskrad on 2009-01-02
On windows, but I havent in ubuntu. This is my first attempt of playing an MP3 on ubuntu.

---

### Post by retskrad on 2009-01-02
GStreamer, I have already installed eveything with name "GStreamer"

---

### Post by stoogiebuncho on 2009-01-02
Did you try the GStreamer package (or do you already have it installed)?

---

### Post by retskrad on 2009-01-02
Already installed.

---

### Post by stoogiebuncho on 2009-01-02
Unless I misunderstood, it sounds from your original post that the problem is not just with MP3 files - you aren't getting any sound at all from Ubuntu.  Is that correct?

For you to have all these packages installed and still not being able to play the MP3's suggests the problem might be with the sound card or your sound configuration.

Not to be insulting, but have you double-checked your volume settings?

When you try to play an MP3, does the program look like it's playing it but no sound comes out, or does it give you an error message?

Can you get any kind of sound out of any program?

---

### Post by retskrad on 2009-01-02
I already posted that when I play with vlc, the song keeps going and the time is going. But no sounds, I have triesd with serveral mp3. when I use amorak, rythmbox, the time isnt going and the I dont have no sound.

I get sound in general, like games and youtube.

---

### Post by stoogiebuncho on 2009-01-02
Have you tried abn91c's suggestion yet?

> I had that problem with amarok the other day when i updated to amarok 2.0, i ended up having to purge amarok from the system, reboot then install the default amarok then sudo apt-get amarok-kde4 to get it to play my Ipod video mp3's

The only other idea I would have was to install the Medibuntu stuff:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Particularly the w32codecs (or w64codecs, depending on your system)

---

### Post by retskrad on 2009-01-02
Thanks man, installed.

EDIT: Nah,s till it doesnt work to play mp3.

---

### Post by retskrad on 2009-01-02
restarted and it works. thanks.

---


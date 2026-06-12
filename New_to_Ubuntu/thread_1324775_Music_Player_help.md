---
title: "Music Player help"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by KermitDaFrog on 2009-11-12
Hey, im new so please try and make it as simple as possible...

when I connect my ipod, and run Rythmbox and attempt to play a mp3 i get a message that says "your gstreamer application is missing a plugin"

I have attempted to reinstall, the program and gstreamer plugins to no avail.  Thanks in advance

---

### Post by coldReactive on 2009-11-12
Did you follow this guide?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by KermitDaFrog on 2009-11-12
tried some of that stuff...when i run some of the commands i get an error saying doesnt exist like  Couldn't find package gstreamer0.10-pitfdll...

anyone? just trying to play some songs

---

### Post by coldReactive on 2009-11-12
> **KermitDaFrog said:**
> tried some of that stuff...when i run some of the commands i get an error saying doesnt exist like  Couldn't find package gstreamer0.10-pitfdll...

anyone? just trying to play some songs

mp3s are not normally supported in ubuntu (they never played by default in ubuntu, not until 7.04.)

---

### Post by KermitDaFrog on 2009-11-12
so do i have to convert them and if so how?
thanks for the help so far

---

### Post by coldReactive on 2009-11-12
> **KermitDaFrog said:**
> so do i have to convert them and if so how?
thanks for the help so far

You can use audacity to do that.

sudo apt-get install audacity

Open the MP3 files (Import) into audacity. Then export them into Vorbis (OGG) format.

Once you do this, you can't put them back onto your ipod, and macosx nor windows will be able to play them "by default."

So, basically, when you use linux, you either have to adapt it, or have to adapt your windows/mac oses.

---

### Post by KermitDaFrog on 2009-11-12
Alright thanks a ton man will look into it

---

### Post by sloggerkhan on 2009-11-12
did you try adding the medibuntu repos?

---

### Post by sandyd on 2009-11-12
install these packages (from synaptic)
libmp3lame0 
lame
gstreamer0.10-fluendo-mp3
gstreamer0.10-plugins-ugly

---


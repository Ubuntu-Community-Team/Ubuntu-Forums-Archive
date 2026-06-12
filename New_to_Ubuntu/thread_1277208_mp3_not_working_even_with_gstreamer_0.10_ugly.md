---
title: "mp3 not working even with gstreamer 0.10 ugly"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by praveenag91 on 2009-09-28
need help.
am a absolute beginner.

i followed steps in this forum and installed restricted extras to play mp3.
now gstreamer 0.10 ugly is installed but still mp3 does not play.


please help...

---

### Post by 3rdalbum on 2009-09-28
Is the gstreamer0.10-fluendo-mp3 package installed?

Do you get an error message when you try to play the MP3? If so, what is it? If not, are you sure your sound is working?

Are you sure it's definitely an MP3 and not a DRM-encrypted file from an online music store?

---

### Post by praveenag91 on 2009-09-28
my sound is working perfectly.
fluendo is not installed.
while playing mp3 with rythmbox music player it searches for mp3 plugin and doesnt find it.so an import error.
and the file is mp3.i was using it in windows.i did not buy it from online music store

please help.
i am trying this for more than a day now

---

### Post by nothingspecial on 2009-09-28
See [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by praveenag91 on 2009-09-28
and if i try to install vlc e synaptic i get the error as vlc nox cannot be installed and libtar cannot be installed.
please help

---

### Post by 3rdalbum on 2009-09-28
> **praveenag91 said:**
> my sound is working perfectly.
fluendo is not installed.

Sorry, I should have been more specific: Install the Fluendo MP3 codec. And while you're at it, hit the Reload button in Synaptic Package Manager to refresh your package list, and then Ubuntu should be able to find codecs and resolve the VLC dependencies.

---

### Post by t0p on 2009-09-28
You say you don't have  gstreamer0.10-fluendo-mp3 installed.  Neither do I, but I can play mp3s nevertheless.

I say try installing it anyway.

```
sudo apt-get install gstreamer0.10-fluendo-mp3
```

**EDIT:** I'm a bit confused.  You said you have ubuntu-restricted-extras, but your package manager says you can't install vlc-nox.  They are both from the same repository.  Exactly what error messages do you get when you run the command

```
sudo apt-get install vlc
```

---

### Post by halitech on 2009-09-28
did you install the ubuntu-restricted-extras package or just the gstreamer-ugly package? Do you have all the repos enabled?

---


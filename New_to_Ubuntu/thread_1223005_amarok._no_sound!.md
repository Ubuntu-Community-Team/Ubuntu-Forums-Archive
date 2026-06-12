---
title: "amarok. no sound?!"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by tyler.mcg on 2009-07-25
Ok so I got my mp3s on a data partition and Ive tried scanning them into amarok 2. Hit play. Nothing! Can't get the sound working

---

### Post by llamabr on 2009-07-25
I don't know what it means to "scan them into amarok" but I don't use amarok.

are you sure that sound is working for other applications?  can you play the mp3s with, say, mplayer or mpg123?

---

### Post by tyler.mcg on 2009-07-25
oh sorry I forgot to specify that sound works in other apps

---

### Post by swoody on 2009-07-25
tyler.mcg, have you installed the proper codecs to play .mp3's? Also, can you play them in other programs? Not just sound, but the actual mp3 files themselves. If not, try this great post on Multimedia:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Please let us know if that helps you out, or if you still encounter any issues :)

---

### Post by tyler.mcg on 2009-07-25
After I installed this OS I wanted to try out one of my favorite video sites. FF says I need to choose between 3 codecs so I choose the first one. the video website still didn't work it tried to work but froze on me and was very slow before I have to hard boot the computer, later I tried loading shockwave instead now the video player doesn't load a picture at all. It looks like its working but I wait and nothing happens the video will not play. In amarok, (heard was good) I tell it to scan my files to search for music so it does. I try to make a playlist and hit play and nothing happens. It looks as though the counter isn't even counting. But mp3s play in my other application

---

### Post by llamabr on 2009-07-25
try:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tyler.mcg on 2009-07-25
says ubuntu-restricted-extras is already the newest version.

---

### Post by llamabr on 2009-07-25
and do mp3's play otherwise?  try opening them with mplayer

---

### Post by tyler.mcg on 2009-07-25
mp3s work in rhythymbox, vlc mp, and totem in amarok I get a error:

amarok - the KDE Crash Handler

a fatal error has occured
the application amarok crashed and caused the signal 11 (SIGSEGV)

Please attach the following information to your bug report:
This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

---

### Post by CatKiller on 2009-07-25
You probably need to install the **phonon-backend-xine** package to have sound output with Amarok 2.

---

### Post by tyler.mcg on 2009-07-25
> **CatKiller said:**
> You probably need to install the **phonon-backend-xine** package to have sound output with Amarok 2.


Hi Catkiller!

I went into the terminal tried 

```
sudo apt-get install phonon-backend-xine
```and it comes back saying already installed newest version


anyone else?

---

### Post by CatKiller on 2009-07-25
> **tyler.mcg said:**
>  I went into the terminal tried 

```
sudo apt-get install phonon-backend-xine
```and it comes back saying already installed newest version

In that case you should be able to go to Settings &#8594; Configure Amarok... &#8594; Playback and select the backend and playback device of your choice. I'm using Amarok 2.1.1, so I can't remember exactly what the configuration options were called in Amarok 2.0.

---

### Post by tyler.mcg on 2009-07-25
i dont see any option to pick a device?

---

### Post by HungryOcopus on 2009-07-25
Hi, I had a similar problem in amarok. I installed a lot of codecs and still had no sound. In the end I found a solution online (after MUCH looking). I uninstalled then reinstalled amarok, then went into synaptic manager, marked phonon backend-xine for installation, and the phonon one above or below it (think it's phonon backend-gstreamer or something) for removal (I had to do them both at the same time for it to work, that's why I uninstalled and re installed). 
Anyway, if you haven't got it working yet, maybe try this, sorry for the vague description, I had the problem a while ago!

---


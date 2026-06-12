---
title: "No sound"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Wake Rider on 2008-12-14
Hello all, I'm having difficulty with Kubuntu 8.10. I have no sound for Youtube videos or any media file played in any media player e.g. VLC Kaffeine, Amorak etc. I can hear the KDE system sounds when my computer starts up or shuts down. How can I get my sound back?

---

### Post by gettinoriginal on 2008-12-14
I think you will fix this by installing pulse in synaptic  :p

But while you are in synaptic, make sure you have flash 10 installed.

---

### Post by Wake Rider on 2008-12-14
I have pulse installed but can't use it due to connection refused. I don't know how to give it sudo privileges and I still don't have sound on anything other than the system sounds.

---

### Post by Wake Rider on 2008-12-14
[http://ubuntuforums.org/showthread.php?t=996440](http://ubuntuforums.org/showthread.php?t=996440)

I tried this:

sudo apt-get install pulseaudio
pulseaudio -D 

and this is the output:
W: ltdl-bind-now.c: Failed to find original dlopen loader.

I keep searching because I really want sound and I see so many other posts with the same problem. Does anyone know how to fix this!!??

---

### Post by Wake Rider on 2008-12-14
bump

---

### Post by gettinoriginal on 2008-12-14
Places > home folder > Control H (shows hidden files) > .Pulse > properties > permissions

who is the owner ??  It should be you, not sudo.  Make sure the box at the bottom Allow executing file as program is ticked.

---

### Post by solwic on 2008-12-14
> **Wake Rider said:**
> [http://ubuntuforums.org/showthread.php?t=996440](http://ubuntuforums.org/showthread.php?t=996440)

I tried this:

sudo apt-get install pulseaudio
pulseaudio -D 

and this is the output:
W: ltdl-bind-now.c: Failed to find original dlopen loader.

I keep searching because I really want sound and I see so many other posts with the same problem. Does anyone know how to fix this!!??

Keep in mind that you usually can't get sound if both Firefox and VLC/Amarok/Whatever are running simultaneously.  Something broken in Pulse, as I understand it.

---


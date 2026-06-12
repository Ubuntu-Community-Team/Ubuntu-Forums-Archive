---
title: "VLC/TOTEM Choppy playback on DVD"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by deviator on 2010-02-12
after trying to get a dvd i borrowed from the local shop to play i ran into a problem of having the playback all choppy.

libdvdcss2 installed

among other things i'm sure i didn't need (W32 codec)

here is what it looks likes, both on totem and vlc.
[IMG]http://img14.imageshack.us/img14/8964/screenshotcbm.png[/IMG]

---

### Post by deviator on 2010-02-12
anybody?

---

### Post by deviator on 2010-02-13
bump really need help for this, i stress it's a dvd problem and has no effect on xvid or avi's. seems to only happen with some dvd's.

i have restricted extras installed along with libdvdcss2 and libdvdread4

---

### Post by 3rdalbum on 2010-02-13
That looks like the classic "DVD is faulty" symptom. If you look at the 'dmesg' command, does it give you read error messages?

---

### Post by deviator on 2010-02-13
it seems the problem was that i installed libdvdcss2 using apt-get and not the synaptic package manager. after i reinstalled it via synaptic everything is fine. go figure.

---

### Post by Chris Edgell on 2010-02-13
How did that go?  Did you go into the terminal and uninstall, then install through synaptic?

---


---
title: "Can't get laptop's internal mic to work..."
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-12-09
I'm using an acer aspire netbook, the built in camera works fine but the mic doesn't at all.  I've looked around a bit and can't seem to find anything that helps.  The Linux Mint forum guys were pretty useless too, can anyone here help me out?

---

### Post by Zimrie on 2009-12-09
is input in sound preferences enough enlarged?

---

### Post by Space-Wolf on 2009-12-09
This is my input setting at the moment: [http://img31.imageshack.us/img31/5899/screenshotdk.png](http://img31.imageshack.us/img31/5899/screenshotdk.png)

---

### Post by Zimrie on 2009-12-09
maximize it (input)

---

### Post by Locke_99GS on 2009-12-09
Open *alsamixer* from a terminal, un-mute it [M}, and turn it up.

---

### Post by Space-Wolf on 2009-12-09
Hmm, I tried both suggestions and all that sound recorder records is quiet static.

---

### Post by Locke_99GS on 2009-12-10
Use *pavucontrol* to make sure the correct input is being used.

---

### Post by ricardo.gloe on 2009-12-10
I have the same issue on my netbook aspire one. The built-in mic, when I max the volume inputs, plays only static on playback. At least an external mic, when connected, seems to work by changing to mic 2 connector in the volume control settings.


I've installed the lastest alsa drives, as per instructions on the netbook ubuntu installation wiki, then maxed volume with gnome-alsa mixer, I've checked with pavucontrol. None of these things work.

If anybody's found a solution or has a suggestion, I'd also appreciate it.

---

### Post by Space-Wolf on 2009-12-10
Hmm, I guess nothing yet.  People on other forums have been having the same problems too.

---


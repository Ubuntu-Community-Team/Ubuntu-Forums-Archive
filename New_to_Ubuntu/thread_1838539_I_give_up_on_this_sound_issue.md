---
title: "I give up on this sound issue"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Zanderist on 2011-09-03
ever since I started using tuxguitar and timidity to hear it, my sound has been screwed up. As in totally muted....I'm at a loss as to why sound is such a complex subject on ubuntu.

---

### Post by jfed on 2011-09-03
Sound and Linux have always been enemies since the beginning of time.

---

### Post by JD8182 on 2011-09-03
Just a Suggestion, open a terminal and type alsamixer and make sure the volumes are all up. Also click F6 while in alsamixer and change your device, then make sure the sound is correct for your devices as well..Good luck.

---

### Post by Zanderist on 2011-09-03
I've done that, and yes it was turned all the way down. So I turned it up and heard sound again, then the sound stopped opened up the terminal only to find that somehow it was turned down again.

---

### Post by charly17201 on 2011-12-19
I just recently found TuxGuitar and had the same issues many others have had - no sound. I found one piece that did fix the no sound issue. Go to the Package Manager, search on TuxGuitar and install any package not installed already.

Then once you've downloaded and installed it all, in TuxGuitar, go to Tools, Settings then sound and select Real Time Sequencer and Gervil Midi Port. That got my sound working.

The other issue, was that it didn't "Stick" when I restarted the program the next time. What I ended up doing was making all the settings again and saving the default 'tuxguitar.tg' file that opens on startup. Now sound is still there each time I restart the program.

New problem, when I'm working with multiple windows on the desktop (11.10 Ubuntu Studio) I often loose TuxGuitar even though I have it pinned to the sidebar (I hate the Unity GUI). I have to reduce or close any other windows (FireFox and Thunderbird, etc) in order to find TuxGuitar.

---

### Post by TBABill on 2011-12-19
If it'll save you any efficiency on the desktop, Alt+Tab between open apps in unity may help keep from having to minimize the others to find the one you want.

---


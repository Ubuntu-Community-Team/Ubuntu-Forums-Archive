---
title: "Musically suddenly doesnt play"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Zopiac on 2009-09-06
Since about 20 minutes ago my music won't play, and gives me the following error in Totem and Rhythmbox:

Could not get/set settings from/on resource

However, when I hover my mouse over the file in Nautilus, it's preview function plays it fine.

What is the problem???

---

### Post by Zopiac on 2009-09-06
Bump :/

---

### Post by pi.boy.travis on 2009-09-06
Is the file on your hard disk, or on some remote server?  Sometimes I get this problem if I try to play music right from my FTP server when it is busy.

---

### Post by spikoley on 2009-09-06
I am not great with sound issues, but your issue sounds similar to the sound issue I had.  This is what fixed it.

```
sudo apt-get install padevchooser
```

1. Open Totem or which ever program with the sound issue
2. Alt + F2 and enter padevchooser to open PulseAudio Device Chooser utility
3. Left click on the system tray icon
4. Volume Control
5. Playback tab
6. Click the down arrow for Totem
7. Move Stream
8. Select USB Audio and it worked!

---

### Post by Zopiac on 2009-09-06
> **spikoley said:**
> I am not great with sound issues, but your issue sounds similar to the sound issue I had.  This is what fixed it.

```
sudo apt-get install padevchooser
```

1. Open Totem or which ever program with the sound issue
2. Alt + F2 and enter padevchooser to open PulseAudio Device Chooser utility
3. Left click on the system tray icon
4. Volume Control
5. Playback tab
6. Click the down arrow for Totem
7. Move Stream
8. Select USB Audio and it worked!

I get this error after about 10 seconds using the programme: Connection failed: Connection terminated

Also, the files are on my HDD.

---

### Post by Zopiac on 2009-09-07
Bump

Just realised that the thread is called "Musically..." lol whoops

---


---
title: "Flash without Sound"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Living2007 on 2009-10-21
Running 8.04 here, i managed to get FF 3.5.3 and download the latest Flash from the adobe website because YouTube needs the plug-in. The adobe flash must have updated through the ubuntu update manager, and now i can't here the sound from YouTube vids, I can get it to work though, but that involves disabling and re-enabling the plug-in to get it to work.

How an i to fix this?

---

### Post by spikoley on 2009-10-21
This worked for me. 


```
sudo apt-get install padevchooser
```

1.  Open Totem
2.  Alt + F2 and enter padevchooser to open PulseAudio Device Chooser utility
3.  Left click on the system tray icon
4.  Volume Control
5.  Playback tab
6.  Click the down arrow for Flash
7.  Move Stream
8.  Select USB Audio and it worked!

---


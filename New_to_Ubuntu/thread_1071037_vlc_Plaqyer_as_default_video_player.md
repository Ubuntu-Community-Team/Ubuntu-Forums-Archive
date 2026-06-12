---
title: "vlc Plaqyer as default video player"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Patricrawley on 2009-02-15
How do I get vlc to be my default video player and banshee to be the default music player?

---

### Post by ibuclaw on 2009-02-15
The easiest way I know is just to right-click the audio/video file, then select "**Properties**".
Then in the **Open With** tab, select the application so that the bullet box is checked next to the application you want to associate the file with.

Regards
Iain

---

### Post by spcwingo on 2009-02-15
One way to do that would be to open Nautilus, then open edit>preferences>media, and choose your preferences from there.  Alternately you could go to system>preferences>preferred applications>multimedia and choose your preference.

---

### Post by u-slayer on 2009-10-28
Here's the quick way to set VLC as the default for ALL media files:

```
cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
```

---


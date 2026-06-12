---
title: "Mic Is Working, Then Cuts Off"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by hockeygoalie5 on 2011-02-12
Sorry there's a second thread of this that's empty, don't know what happened there!

Hello, this is my first post on the forum and hopefully it goes well.

I'm using an HP Pavilion with a built-in microphone. The microphone  worked on first install but stopped. I looked up the problem and edited  gstreamer-properties, after a restart this worked. However, after some  time the microphone had stopped working. It was not detecting any sound,  as if it isn't there at all. Editing gstreamer and putting it back to  what I had then restarting fixes this issue. I've looked everywhere for a  solution and never found one. This problem extends from Mangler, to  Skype, to the sound properties panel so I'm sure it has nothing to do  with the program. I don't know what you would need to help debug the  issue, so post back if you want more information.

Thanks in advance,
hockeygoalie5

---

### Post by cariboo on 2011-02-12
Check alsamixer to make sure the mic volume is turned up. Open an Applications->Accessories->Terminal and type:

```
alsamixer
```

use the arrow keys to navigate and turn the volume up and down. Once you have the settings to your liking, press esc to exit, then type:

```
sudo alsactl store
```

to save the settings.

---


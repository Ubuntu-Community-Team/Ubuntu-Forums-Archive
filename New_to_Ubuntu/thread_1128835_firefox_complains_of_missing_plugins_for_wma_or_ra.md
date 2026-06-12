---
title: "firefox complains of missing plugins for wma or ram"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by nhasian on 2009-04-18
In ubuntu 8.10 or 9.04, I am unable to play:

[http://audio.islamweb.net/audio/listenbox.php?audioid=10951&type=wma](http://audio.islamweb.net/audio/listenbox.php?audioid=10951&type=wma)

or

[http://audio.islamweb.net/audio/listenbox.php?audioid=10951&type=ram](http://audio.islamweb.net/audio/listenbox.php?audioid=10951&type=ram)

firefox says "additional plugins required" and has a button for install plugins which does nothing.

how can i make these files play in firefox?  Please note i have mplayer, and vlc installed both of which play wma or ram files if they are saved to my desktop, but i can not play them in firefox.

please advise,

thanks in advance!

---

### Post by markofealing on 2009-04-18
Same here on Ubuntu 8.10!

---

### Post by nhasian on 2009-04-18
i havent figured it out for wma yet, but i got it working for ram.  in a terminal type:

```
sudo apt-get remove totem-mozilla && sudo apt-get install mozilla-mplayer
```

---

### Post by Paqman on 2009-04-18
You could also try the [Firefox VLC plugin]("apt:mozilla-plugin-vlc") (click to install).

---

### Post by nhasian on 2009-04-18
i have the vlc plugin installed but its still doesnt work.  are we missing a step?  like telling firefox to use the vlc plugin for certain filetypes?

> **Paqman said:**
> You could also try the [Firefox VLC plugin]("apt:mozilla-plugin-vlc") (click to install).

---

### Post by Paqman on 2009-04-19
I don't really know much about trying to play wma files, as I never really need to, but you might want to try connecting to the [Medibuntu repository]("http://www.medibuntu.org/"), run an update and download the package w32codecs.

---


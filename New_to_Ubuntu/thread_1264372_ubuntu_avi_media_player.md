---
title: "ubuntu avi media player"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Johnecash on 2009-09-12
hi guys

does anyone know of a media player that will play avi files inside ubuntu? and how to install ? thanks

---

### Post by talsemgeest on 2009-09-12
> **Johnecash said:**
> hi guys

does anyone know of a media player that will play avi files inside ubuntu? and how to install ? thanks
Go to the terminal and run ```
sudo apt-get install ubuntu-restricted-extras
``` which will install all the codecs you need. Now you will be able to play AVI files in the default media player.

---

### Post by t0p on 2009-09-12
As talsemgeest said above, if you install ubuntu-restricted-extras you can use any media player to play .avi files... and just about any other media file format.

I prefer **vlc** to totem (the default "movie player").  Install by typing into a terminal:

```
sudo apt-get install vlc
```

---

### Post by irate.turtle on 2009-09-12
You can install mplayer

```
sudo apt-get install mplayer
```




> **Johnecash said:**
> hi guys

does anyone know of a media player that will play avi files inside ubuntu? and how to install ? thanks

---

### Post by talsemgeest on 2009-09-12
> **irate.turtle said:**
> You can install mplayer

```
sudo apt-get install mplayer
```
I think totem or VLC are considerably easier to use for an absolute-beginner than mplayer.

---

### Post by hockeytux on 2009-09-12
Xine or VLC will both work fine. :popcorn:

---

### Post by andrew.46 on 2009-09-12
Hi Johnecash,

> **Johnecash said:**
> does anyone know of a media player that will play avi files inside ubuntu? and how to install ? thanks

As many have suggested vlc is an excellent piece of software that is not only kind to new users but will challenge older hands with its vast array of options. But if you ever want to try something a little different further down the track I would suggest you could try a *modern* version of MPlayer allied with SMPlayer + a codec pack. This can take a little more tweaking to setup and run than vlc but IMHO MPlayer richly repays the investment of time an effort in mastering it. I attach a screenshot of MPlayer + SMPlayer in action to whet your appetite a little :).

Andrew

---


---
title: "Gstreamer missing plugin"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Swatfoot on 2009-03-20
I'm trying to watch a dvd but I get a error using movie player that says gstreamer missing plugin
I think it might need a codex or some thing any help is much appreciated.

---

### Post by Temposs on 2009-03-20
Open a terminal by Applications->Accessories->Terminal, and type:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by dafty-w on 2010-04-26
I'm facing this issues too.

Thank you for a solution, Temposs.

---

### Post by jeffrey2009 on 2010-10-19
I tried to install this plugins using the command listed but I still get the error message when playing the following link in radio tray

[http://82.135.234.195/pukas.wax](http://82.135.234.195/pukas.wax)

also tried 

mms://82.135.234.195/pukas.wax


"Your GStreamer installation is missing a plugin"

---

### Post by jeffrey2009 on 2010-10-19
Actually got it working now, needed to restart radio tray.

---

### Post by tbdfm01 on 2010-12-22
> **jeffrey2009 said:**
> I tried to install this plugins using 

"Your GStreamer installation is missing a plugin"


I had to install the alsa plugin for gstreamer to get it working.  I had removed pulseaudio because it sucks.

(aptitude install gstreamer0.10-alsa)

---

### Post by cannibal_aj on 2012-01-22
```
apt-get install gstreamer0.10-alsa

```
and it works :guitar:

But guys, it will be great if this package was in radiotray dependencies. Not everyone use Ubuntu.

---

### Post by oldos2er on 2012-01-22
Closed, necromancy.

---


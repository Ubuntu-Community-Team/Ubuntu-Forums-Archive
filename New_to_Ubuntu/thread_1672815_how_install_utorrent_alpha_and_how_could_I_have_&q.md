---
title: "how install utorrent alpha and how could I have &quot;full screen&quot;?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by magodiafano on 2011-01-21
Hi, I am a n00b and I have two simple questions:
the first is relative to utorrent alpha... I don't know how install it:

I downloaded a .gz file and I have extracted it. When I try to click on utserver (there is a padlock up the icon) a file setting.dat is created and nothing happens.
What I have to do?

The second question is relative to the maximisation of the windows (like firefox): when I do the maximization two bars remain (the upper one with application, places.. etc etc) and the lower one (similar to windows).
is there a way to have only one bar like in windows? I would like only the lower one.

Thank you

---

### Post by cariboo on 2011-01-21
uttorent for linux, is a server only, just open a terminal and navigate to the directory where the extracted files are and type:

```
sudo ./utserver
```

you should then be able to access it from your web browser at [http://localhost:10000](http://localhost:10000), although it doesn't work for me.

I'd suggest giving qbittorrent a try, as it's quite similar to utorrent.

---

### Post by gordintoronto on 2011-01-21
Do you really want to run a server, or just do bittorrent downloads? Transmission is included with Ubuntu.

The easiest way to only have one panel, at the bottom, is to install Linux Mint...

---

### Post by jrz on 2011-02-21
> **magodiafano said:**
> Hi, I am a n00b and I have two simple questions:
the first is relative to utorrent alpha... I don't know how install it:

I downloaded a .gz file and I have extracted it. When I try to click on utserver (there is a padlock up the icon) a file setting.dat is created and nothing happens.
What I have to do?

The second question is relative to the maximisation of the windows (like firefox): when I do the maximization two bars remain (the upper one with application, places.. etc etc) and the lower one (similar to windows).
is there a way to have only one bar like in windows? I would like only the lower one.

Thank you

I extracted the files to a folder on my Desktop named UTServer, and just open a terminal screen, navigate to the directory containing the executable, 
cd Desktop/UTserver/utorrent-server-v3_0 and type ./utserver as shown below.

joe@compaq:~/Desktop/UTserver/utorrent-server-v3_0$ ./utserver

server started - using locale en_US.utf8
IPv6 is installed

Utorrent is then running and to view it I open Firefox and enter [http://localhost:8080/gui](http://localhost:8080/gui) which allows me to view and use utorrent.

It works very well, and appears to connect to seeds and peers much more quickly than running the Win version under wine, the CPU usage is much less, and torrents appear to complete much more quickly.

---

### Post by marcusaur on 2011-02-21
on yer bars at both sides are two small arrows click anyone and it hides yer bar

---

### Post by jrz on 2011-02-21
> **marcusaur said:**
> on yer bars at both sides are two small arrows click anyone and it hides yer bar

I'm not quite sure what you mean without seeing a screen dump.

My display was not correct initially, but fixed by holding the control key and clicking the + key several times corrected it.

---

### Post by marcusaur on 2011-02-21
how to get bars away  [http://lookpic.com/c1/i2/1459/kIaKnRcu.png](http://lookpic.com/c1/i2/1459/kIaKnRcu.png) look for curser above the firefox logo

---

### Post by marcusaur on 2011-02-21
as for torrent client i find the preloaded transmission works very well never tried to download utorrent  no need

---

### Post by jrz on 2011-02-21
> **marcusaur said:**
> how to get bars away  [http://lookpic.com/c1/i2/1459/kIaKnRcu.png](http://lookpic.com/c1/i2/1459/kIaKnRcu.png) look for curser above the firefox logo

You can right click on the bar and under properties uncheck "Show hide buttons" to remove the arrows, and you can check "Autohide" to hide the bar like in Windows.

---

### Post by jrz on 2011-02-21
> **marcusaur said:**
> as for torrent client i find the preloaded transmission works very well never tried to download utorrent  no need

It's a matter of personal choice, I've tried various apps, including transmission and though they all worked satisfactorily, I ended up preferring utorrent under wine, but now find the utorrent alpha without need of wine to be much more efficient.

---


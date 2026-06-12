---
title: "No volume control GS Streamer plugins and/devices found"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Struggling1 on 2009-02-01
I switched on my laptop this morning only to find there is no sound, and there is a little red X over the sound icon.
When I click on it, it says "No volume control GS Streamer plugins and/devices found."

(1) Does this mean that my sound card died overnight?
(2) Is it merely not being recognised for some strange reason?
(3) How can I make it work?
(4) I think I use Ubuntu 8.4
(5) Laptop is an Acer Aspire 3680
(6) I do not know anything about computers and need the advice to be as simple as possible.
(7) Thanks in anticipation; I am distraught :(

---

### Post by gettinoriginal on 2009-02-01
Can you please run in terminal:
```
lspci
```
and post results here?

---

### Post by Struggling1 on 2009-02-02
Thanks for getting back to me.  I spent all night online and eventually found the plugins at
[http://gstreamer.freedesktop.org/download/](http://gstreamer.freedesktop.org/download/)

That restored the sound :D

Still, I hope this isn't some crazy website - since then I've found I can't delete stuff from my trash!!!  Wonder if the two events are related...?

---

### Post by gettinoriginal on 2009-02-02
Try this for emptying your trash:
```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by Struggling1 on 2009-02-04
Thanks!  That worked!  You're a star :KS

---


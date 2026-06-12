---
title: "Argh! Where's my sound gone?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Alexpants on 2008-12-23
I'm currently running Ubuntu 8.10, been on it for about a month and aside from a whole barrage of gaming issues I've had I actually really like it. 
Here's the problem though, I just booted up, went to put some music on and I have no sound! 
I've got no idea what's causing it, or how it happened, does anyone have any ideas on how to fix this? Sorry it's a bit vague but I really have no idea why this has happened.

---

### Post by jaxadam on 2008-12-23
I'm not going to be of much help, because I'm new to this, too.  I haven't had any sound at all, and someone sent me this link to read through.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by nerdking on 2008-12-23
have you checked your volume control?

---

### Post by Alexpants on 2008-12-23
Yes.

---

### Post by halitech on 2008-12-23
open a terminal and post the output of
```
aplay -l
```

---

### Post by linux_tech on 2008-12-23
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type


```
gnome-alsamixer

```
check all settings, make sure nothing is muted


If you havn't already installed these under Intrepid, installing these will probably improve your sound


```

sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```


To open volume control type:
```
gnome-volume-control

```

---

### Post by linux_tech on 2008-12-23
You can also try restarting alsa
```

sudo /etc/init.d/alsa-utils stop

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start

```

---


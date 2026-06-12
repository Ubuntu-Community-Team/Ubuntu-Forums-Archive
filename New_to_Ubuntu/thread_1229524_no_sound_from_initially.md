---
title: "no sound from initially"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by r.v.the.evil on 2009-08-02
hello friends
aplay gives
 aplay -l
aplay: device_list:217: no soundcards found...

and
lspci gives
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
    Subsystem: ATI Technologies Inc RS780 Azalia controller
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at 92410000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel




how can i get sound

---

### Post by gorgon on 2009-08-02
let me google that for you! :)

[http://ubuntuforums.org/showthread.php?t=1124049](http://ubuntuforums.org/showthread.php?t=1124049)

does that help?

---

### Post by r.v.the.evil on 2009-08-02
> **gorgon said:**
> let me google that for you! :)

[http://ubuntuforums.org/showthread.php?t=1124049](http://ubuntuforums.org/showthread.php?t=1124049)

does that help?


in this thread it is shown to select alsa mixer which i dont have
and no alsa devices are shown
i read a thread and uninstall alsa-base
it might be the problem

---

### Post by r.v.the.evil on 2009-08-02
any new thread which can help

---

### Post by gorgon on 2009-08-02
hm. did you follow the 3rd post in the link as well? on editing the file /etc/modprobe.d/sound ?

ALSA should be installed by default.. try running 'alsamixer' in a terminal and tell what happens.

---

### Post by gorgon on 2009-08-02
ah, sorry, i missed your last posts.

hm. according to alsa-project.org support for your soundcard was added in version 1.0.14. current stable version is 1.0.20 .

Is there a reason that you uninstalled alsa? I would reinstall it and follow the instructions in the post i mentioned above.

---

### Post by r.v.the.evil on 2009-08-02
> **gorgon said:**
> hm. did you follow the 3rd post in the link as well? on editing the file /etc/modprobe.d/sound ?

ALSA should be installed by default.. try running 'alsamixer' in a terminal and tell what happens.


i read a thread in which it was writen to uninstall alasa mixer
and uninstall new mixer 
unfortunately alsa was uninstalled and neww mixer was not installed
so i lost thaat

---

### Post by r.v.the.evil on 2009-08-02
is any one there to help

---

### Post by r.v.the.evil on 2009-08-02
how can i run alsa mixer in terminal

---

### Post by gorgon on 2009-08-02
have you tried this?
[http://kubuntuforums.net/forums/index.php?topic=3103453.0](http://kubuntuforums.net/forums/index.php?topic=3103453.0)

(it also requires you to reinstall alsa..)

---

### Post by r.v.the.evil on 2009-08-02
How can i reinstall alsa 1.20
and my aplay -l gives no sound card found

---

### Post by gorgon on 2009-08-02
ok.

if you remember what packages you removed you should be able to install them again with 'apt-get install'. to be sure, let's do this in a terminal:

```
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils libasound2
```

---


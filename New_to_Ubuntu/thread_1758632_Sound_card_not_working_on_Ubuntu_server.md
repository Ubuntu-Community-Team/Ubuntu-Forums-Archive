---
title: "Sound card not working on Ubuntu server"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by longreacher on 2011-05-14
I've heard good things about these forums, and I'm hoping someone can send me in the right direction.  I'm trying to use a microphone with my headless server but I'm not picking up any audio.  The server doesn't seem to be seeing the sound card.  

A little background, I'm running 10.10 server

```
aplay -l
```
gives me

```
aplay: device_list:235: no soundcards found...
```


```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Gives me output [_**here**_]("http://www.alsa-project.org/db/?f=6713ddfee489908857f67ad56d00b1e4a9603eab")

I've tried following other people's problems in the forums, but at some point, their problems and mine diverge.  Can anyone steer me in the right direction?

---


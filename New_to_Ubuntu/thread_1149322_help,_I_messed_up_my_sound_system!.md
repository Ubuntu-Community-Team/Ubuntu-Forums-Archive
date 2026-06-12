---
title: "help, I messed up my sound system!"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by gandaran on 2009-05-05
I installed this alsa-driver-linuxant package then removed it now I don't have any sound, on sound volume control I only have the master volume option all other options have simply disappeared, I reinstalled all pulseaudio and alsa plus libasound packages but still no sound, how can I fix this?

---

### Post by jobbesat on 2009-05-05
Try [this]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")

---

### Post by Insanity01 on 2009-05-05
Install ALSA, it should work ^^

---

### Post by neu2buntu on 2009-05-05
try this code.... copy and paste into terminal

```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```

---

### Post by gandaran on 2009-05-05
many thanks to all
I fixed it installing module-assistant then choose to build alsa-source 
it's not what I wanted but well sound is working.

---

### Post by stakh on 2009-05-05
> **neu2buntu said:**
> try this code.... copy and paste into terminal

```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```

Can you please explain these commands?

upon doing sudo alsa force-reload, the system asks scary questions like "do you want kde to forget about your devices?"

---

### Post by stakh on 2009-05-05
also, when I do $pulseaudio -D, I get:
> 
$ pulseaudio -D
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: main.c: daemon initialization failed.



---


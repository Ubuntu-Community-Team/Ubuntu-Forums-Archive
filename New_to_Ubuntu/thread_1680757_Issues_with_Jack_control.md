---
title: "Issues with Jack control"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by Musicjunkie4537 on 2011-02-03
Hey.  I have an M-Audio Audiophile 2496 sound card that i'm trying to use Jack with OSS. and i'm having the hardest time with it.

Here's what I get when I try to start the jack controller.

I alrealy changed the code to set the memlock to  2225052, but I don't think its recognizing it in the code.  So i'm a bit stuck

```
 jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2225052
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
OSS: failed to enable full duplex for /dev/dsp: oss_driver.c@565, errno=95
oss_driver: /dev/dsp : 0x10/2/48000 (128)
oss_driver: indevbuf 4096 B, outdevbuf 4096 B
oss_driver: using barrier mode, (dual thread)
OSS: read() failed: oss_driver.c@968, count=-1/4096, errno=13
jackd watchdog: timeout - killing jackd
```

---


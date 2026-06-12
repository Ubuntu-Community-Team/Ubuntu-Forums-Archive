---
title: "IDJC installed and connected BUT"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by trucker33377 on 2009-01-10
ive got this hooked up to icecast and it plays. But the tracks speeds up and slow down, also theres alot of crackling on the files. The mic seems to work better it is an ogg file still not real clear but better then mp3. output is 128bits. I'm lost and so close too. files play fine on totem player this is just on the DJ player, even if its not streaming out too

---

### Post by StephenF on 2009-01-11
My first thought is that resampling is eating up too many CPU cycles. In IDJC preferences try selecting player resample quality "Fast" and also in the Server window do the same.

Another thing you should do is create a config file for jack-audio-connection-kit.

In a terminal:
$ echo "/usr/bin/jackd -d alsa -r 44100 -p 2048" > ~/.jackdrc

This will reduce the chance of buffer x-runs and it also sets the jack sample rate to 44100Hz which is the same as CD audio so that most of your music playback will not need any resampling.

---


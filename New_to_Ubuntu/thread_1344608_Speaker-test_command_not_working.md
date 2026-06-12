---
title: "Speaker-test command not working"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-12-03
I have set-up my 2.1 system with amplifier and I wanted to ensure my left speaker and right speaker were correctly placed.

So, I tried this command:
```

speaker-test -Dplug:surround40 -c4 -l1 -twav

```

In the past I used to get a voice saying "left speaker" and "right speaker". Now I get the following error:

```

Playback device is plug:surround40
Stream parameters are 48000Hz, S16_LE, 4 channels
WAV file(s)
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy

``` (continues until I exit the console)

I found the command on the forums a while back but now it does not work.

I had a look at the man page for "speaker-test" and I tried the following command:

```

speaker-test -Dplug:front -c2

```

I got the same output.

I searched through the forums and found a variation:
```

speaker-test -c2 -|1 -twav
1: command not found

```

This made a loud hiss on my right speaker and then my left speaker.

Any thoughts? 

Thanks!

---


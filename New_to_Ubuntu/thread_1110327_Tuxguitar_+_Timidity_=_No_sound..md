---
title: "Tuxguitar + Timidity = No sound."
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Luciano90 on 2009-03-29
Hi there. Well I've been fighting with ALSA, OSS and the X-Fi for a couple of days.

I've finally recompiled the kernel and got the X-Fi drivers working. Also I've got OSS too (which I've installed before the drivers). 

Now I have a problem:
```
luciano-deb:/home/luciano# timidity -iA -Os
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')
```

I can't start timidity that way, but:
```
luciano-deb:/home/luciano# timidity -iA -Od
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3
Playing time: ~4 seconds
Notes cut: 0
Notes lost totally: 0
Playing time: ~15 seconds
Notes cut: 0
Notes lost totally: 0

```

In fact, works.

But I can hear no sound at all. Except, if while playing, I change the Timidity Port at TuxGuitar, that way SOMETIMES, I hear 1 note, and the no more sound. Kinda wierd. Anyway, at TuxGuitar propierties I Have:
-TuxGuitar Sequencer.
And in port:
```
Midi Through Port-0 [14:0]
TiMidity Port 0 [128:0]
TiMidity Port 1 [128:1]
TiMidity Port 2 [128:2]
TiMidity Port 3 [128:3]
Midi Through Port-0 #0
TiMidity Port 0 #0
TiMidity Port 1 #1
TiMidity Port 2 #2
TiMidity Port 3 #3
```

None of the 10 Port's work. When I chose the ones [128:X], sometimes it happens what I've stated up. I read that the ones with [128:X] are ALSA, and the others OSS. I have all instaled through repositories, incluiding -alsa, -jsa, -oss.

Any ideas?

---

### Post by Luciano90 on 2009-03-29
bump           ?

---

### Post by llamabr on 2009-03-29
Hi.  I'm afraid that you're no longer an absolute beginner.

Try taking this question to the appropriate forum for sound cards or periferals, and an expert will help you.

Good luck.

---


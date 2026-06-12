---
title: "[SOLVED] tuxguitar"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Arthur Millar on 2008-12-04
do i need to have MIDI to use tux guitar 
i have installed it and it seems to work fine i just have no sound
what am i missing?

---

### Post by bryncoles on 2008-12-04
i had this problem with the new tuxguitar too! i swear, every upgrade, the only thing that ever needs fixing is tux guitar. 

anyway, i fixed the problem by installing 'timidity' - you can find it in synaptic. its a midi emulator. 

then run this command in a terminal to start timidity running:

```
timidity -iA -Os
```

then boot tuxguitar and work through the menus - tools -> settings -> sounds. select a timidity port - you might have to try several before you find one that works though. i have to use timidity port 0[129:0]. 

you will have to put that command in a termina each time you want to run tuxguitar, unless you add timidity to your start-up sessions. 

just click system->preferences->sessions->add session and put that command in there. 

hope that fixes it for ya!

---

### Post by Arthur Millar on 2008-12-04
YES YES YES YES YES
Thank you  
Thank you
Thank you

timidity port 0[128:0].

---

### Post by bryncoles on 2008-12-04
no problem - im happy to help!

dont forget to mark the thread as 'solved' in the thread tools and happy rockin'! ;)

---

### Post by Her Ghost on 2008-12-04
legend!

---

### Post by Catdaddy on 2008-12-17
Awesome I've been dealing with this problem forever!! thank you so much now I can listen to music and keep Tux Guitar open as well. Thanks!

---

### Post by Jota37 on 2009-01-13
Hi,

Nice to see it worked to some. When I tried that, it didn't for me. But something else got sound to work in Tuxguitar for me.

This worked in both Ubuntu and Kubuntu, which I have in different computers. Both are 8.10, by the way. And Tuxguitar 1.0 didn't have sound in either computer, until today -- after quite some reading of several forums.

What solved it for me was installing package **tuxguitar-jsa** (available through Synaptic).

Then: 
1. open Tuxguitar and go to Tools -> Plugins
2. disable "ALSA output plugin" and "OSS output plugin" (if you have them)
3. enable (if it isn't yet) "Java Sound Api plugin"
4. restart Tuxguitar

That did it for me, I hope this helps someone else out there.

---

### Post by cygnus8595 on 2009-01-22
Both fixes worked for me, but the jsa fix is much more elegant. Thank you so much!

---

### Post by balsamo on 2009-02-02
> **Jota37 said:**
> Hi,

Nice to see it worked to some. When I tried that, it didn't for me. But something else got sound to work in Tuxguitar for me.

This worked in both Ubuntu and Kubuntu, which I have in different computers. Both are 8.10, by the way. And Tuxguitar 1.0 didn't have sound in either computer, until today -- after quite some reading of several forums.

What solved it for me was installing package **tuxguitar-jsa** (available through Synaptic).

Then: 
1. open Tuxguitar and go to Tools -> Plugins
2. disable "ALSA output plugin" and "OSS output plugin" (if you have them)
3. enable (if it isn't yet) "Java Sound Api plugin"
4. restart Tuxguitar

That did it for me, I hope this helps someone else out there.

Hi, I've done this and tuxguitar says : MIDI System is unvailable when I click on "play" ...

Any idea ?
I much prefer this solution than the timidity one ...

---

### Post by Jota37 on 2009-02-02
> **balsamo said:**
> Hi, I've done this and tuxguitar says : MIDI System is unvailable when I click on "play" ...

Any idea ?
I much prefer this solution than the timidity one ...

Hi,

I haven't seen this error, so I am just guessing wildly here...

Do you still have timidity running when you get that error? I don't know if my hunch makes sense, but it might be that both TuxGuitar and timidity are competing over some resource -- as it happens with audio, for example: when TuxGuitar is running, Amarok can't access the audio in my Kubuntu 8.10 machine.

If you do not have timidity running, then I don't know what could be causing this (I'm assuming that your MIDI was working with timidity, and therefore MIDI is OK in you machine).

---

### Post by balsamo on 2009-02-02
Well actually timidity was not working when i got this error.
When I start timidity by hand and choose the correct settings in tuxguitar, it works great.

---

### Post by Luciano90 on 2009-03-29
Sorry for the bump, but here is my problem:
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
luciano-deb:/home/luciano# 
```

Any ideas?. I had X-Fi + OSS. Now I've recompiled the kernel, and have Alsa + X-Fi drivers (dunno if some apps are still using OSS, flash now works for example, and I've used dpkg-reconfigure linux-sound-base).

I removed and installed tuxguitar, also tuxguitar-alsa & tuxguitar-oss where installed in the apt-get install tuxguitar.

---

### Post by sagelanoj on 2010-04-18
> **balsamo said:**
> Hi, I've done this and tuxguitar says : MIDI System is unvailable when I click on "play" ...

Any idea ?
I much prefer this solution than the timidity one ...

I just re-strated Ubuntu and it was solved. Hope it will for you too.

---

### Post by Lanix90 on 2010-10-12
Hey guys :)

I had the same problem with my 1.2v Tuxguitar, running on Ubuntu 10.10... Software displayed as if it was playing, but no sound was coming out of my speakers.
I used your advices here and I thank you for all your posts, they were absolutely helpful!
Both of these ways of fixing got my TG to play sound, BUT!
 -The first way, the 'midity' way caused a strange delay that is not remotely synchronized (between channels) yet always the same kind of delay - makes it sound like bagpipes-****. Seemed like my computer is having a hard time performing, but my CPU was working at about 7-14% the whole time.
 -Then I tried the 2nd way, the 'tuxguitar-jsa' way. This got my sound playing on time, but it sounds extremely awful. Not only when I play multiple channels simultaneously, but when I play only one channel alone.
Does anyone have a clue what the problem might be?

Thanks a lot. :) :guitar:

---

### Post by mark2741 on 2011-01-07
Thanks. This worked for me - 10.10 64-bit, latest version of tuxguitar in the repos. Unfortunately the tabs don't sound as good as how they do when played on the tuxguitar website preview, but that's definitely a midi issue. When the same file is played on the website it has a more 'guitarish' sound to it (like an acoustic guitar, at least the two jazz files I've tried so far). But in tuxguitar on my computer they sound like just plain midi tones.

---

### Post by BlackDeathzGuitarist on 2011-09-10
Thanks a lot! The 'timidity' solution worked great!

---


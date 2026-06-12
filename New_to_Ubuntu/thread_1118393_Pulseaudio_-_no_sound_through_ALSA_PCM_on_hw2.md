---
title: "Pulseaudio - no sound through ALSA PCM on hw:2"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-06
all i want to do is make pandora work and be able to hear audio in youtube

to do this, i have to use pulseaudio

i have been configuring pulseaudio for the past 2 hours with no luck. 
i followed this guide here [http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)
and added my sound card at the end of the config file. no luck.
all i get is silence

is there some way to get my addon sound card working through pulseaudio without taking a sledgehammer to the onboard sound card???
](*,)

---

### Post by asuastrophysics on 2009-04-06
here is the output of pulseaudio in terminal:

[HTML]girdy@girdy-desktop:~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.Bt87x.pcm.front.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM front:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.Bt87x.pcm.surround40.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround40:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.Bt87x.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround41:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.Bt87x.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround50:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.Bt87x.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround51:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.Bt87x.pcm.surround71.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround71:1
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 32000 Hz.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:2
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.Audigy.pcm.surround71.0:CARD=2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround71:2[/HTML]

---

### Post by asuastrophysics on 2009-04-06
ok i found out what was wrong. 
this took 3 hours to uncover:

in /etc/modprobe.d/alsa-base, the last line i added was 
optiosn emu10k1 index=2

***i spelled options wrong. that is what caused this chaos.

i really wish someone could write a simple GUI for adding a sound card to pulseaudio....
after all, this is "linux for human beings" ;)

---

### Post by kostkon on 2009-04-06
> **asuastrophysics said:**
> ok i found out what was wrong. 
this took 3 hours to uncover:

in /etc/modprobe.d/alsa-base, the last line i added was 
optiosn emu10k1 index=2

***i spelled options wrong. that is what caused this chaos.

i really wish someone could write a simple GUI for adding a sound card to pulseaudio....
after all, this is "linux for human beings" ;)
But there is...

You made the whole situation extremely complex without a reason. You only had to install the *PulseAudio Device Chooser* using Synaptic, then open the PulseAudio Volume Control and set in there your Audigy to be the default card.

I believe because you thought it is difficult you made it to be difficult...

---

### Post by asuastrophysics on 2009-04-07
> **kostkon said:**
> But there is...

You made the whole situation extremely complex without a reason. You only had to install the *PulseAudio Device Chooser* using Synaptic, then open the PulseAudio Volume Control and set in there your Audigy to be the default card.

I believe because you thought it is difficult you made it to be difficult...

My device was never listed under the Pulseaudio Volume Control. It listed my USB bluetooth device and the onboard sound card. 
It had no listing anywhere for my Creative SB Audigy card. 
This is why I had to spend so much time putting it there. Why wasn't it there? God knows...

---

### Post by asuastrophysics on 2009-04-07
above post: sorry i just thought it might be worth pointing out. 

I abandoned pulseaudio for ALSA, which I really like using.
 
I was only trying to switch to Pulse because web sites like Pandora and Youtube had no sound. See below why:

NOTE: You do not have to be currently using the pulseaudio sound server for flash websites work. **However, pulseaudio still must be running in the System-Monitor**. If you do not want to use pulseaudio, do not kill the process like I did :roll:
That is the research I gathered from over 4 hours of tinkering with it. It's good to know how it works tho.

BTW, just thought I'd say that ubuntu runs absolutely flawless on my Acer Laptop. Never once had a problem. I only run into problems with this desktop tower that I built. (ATI Graphics card + Creative Labs' terrible proprietary drivers for linux)
When it runs on the right hardware, it's a d*** good OS. :popcorn:

(My two cents)

---


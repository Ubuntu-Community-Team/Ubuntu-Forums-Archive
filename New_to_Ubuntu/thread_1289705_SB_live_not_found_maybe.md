---
title: "SB live not found maybe???"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by uv101 on 2009-10-12
Hi, I'm having some issues with my SB live. 
 
I've run "sudo aptitude install linux-restricted-modules-`uname -r` linux-generic"
 
"aplay -l" reports no soundcard.
XBMC application reports no sound card
 
Alsamixer shows the card and with the digital out enabled, my processors locks onto a silent PCM audio stream.
 
"lspci -v | less" gives me
 
04:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
Subsystem: Creative Labs Device 8061
Flags: bus master, medium devsel, latency 64, IRQ 16
I/O ports at cce0 [size=32]
Capabilities: <access denied>
Kernel driver in use: EMU10K1_Audigy
Kernel modules: snd-emu10k1
 
wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
 
the output of this file is here
 
[http://www.alsa-project.org/db/?f=572809c12298b9381258969607eed20468e59bef](http://www.alsa-project.org/db/?f=572809c12298b9381258969607eed20468e59bef)
 
I'm pretty new to this and this has definately got me stumped
 
Would appreaciate any help, Thanks Ian

---

### Post by OffAxis on 2009-10-12
what does 

```
asoundconf list
```

give you?

Sometimes the soundcard gets switched from the SBLive to the onboard if you have them both enabled in BIOS.

you should be able to set your default one with

```
asoundconf set-default-card <name from list command above>
```
(you may need to run that with a sudo in front)

```
sudo asoundconf set-default-card <name from list command above>
```

---

### Post by uv101 on 2009-10-13
Hi,
 
```
asoundconf list
```
 
*Live*
 
 
Sometimes the soundcard gets switched from the SBLive to the onboard if you have them both enabled in BIOS.
 
*MB soundcard disabled in BIOS*
 
you should be able to set your default one with
 
```
sudo asoundconf set-default-card* Live*>
```
 
Now alsamixer can't see the card at all. 
 
Is there a way to completely uninstall the soundcard driver lib and start again?
 
This build was done as a base build, but i'm tempted to start again with the full installation. The soundcard definately worked ok with the full installation!
 
Ian

---

### Post by OffAxis on 2009-10-13
> Now alsamixer can't see the card at all. 
can't see the card how?

Is sound muted or is it failing with the message
```
alsamixer: function snd_ctl_open failed for default: No such device

```

If alsamixer starts then 'm' mutes and unmutes a function. (Within alsamixer you can press 'h' to bring up the help menu, 'Enter' to close it).

If alsamixer is failing to open then you had a typo when you set the default sound card. (If asoundconf list still brings up 'Live' then the card / driver are probably being seen properly, it's just a matter of configuration.)

Is ***Live*** showing in the upper left corner of alsamixer?
You can specify which card to mix by specifying a numerical value with the -c flag.
```
alsmixer -c 1
```

---

### Post by uv101 on 2009-10-13
alsamixer would not start as no device present!
 
```
lspci -v | less
```
showed the card on the bus as previous
 
```
 asoundconf list
```
no longer shows any cards, was prev showing "Live"
 
To be honest, I gave up and reinstalled full 9.04 from disk and its all good now!
 
I'd still be interested it what else I could have checked. 15yrs in IT and 2 weeks in Linux so I'm soaking up info like a sponge! :)
 
Thanks, Ian

---

### Post by OffAxis on 2009-10-13
pulseaudio entered the fray in 8.04 (installed by default). That would be an excellent thing to explore since it's now in most major distributions.
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---


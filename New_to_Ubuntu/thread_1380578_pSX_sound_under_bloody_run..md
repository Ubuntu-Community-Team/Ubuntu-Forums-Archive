---
title: "pSX sound under bloody run."
date: 2010-01-13
forum: New to Ubuntu
---

### Post by danwosere2007 on 2010-01-13
Yo. Used pSX emulator with windows, no probs with sound/general performance at all. (ascertained that the bios, disc images and general spec of computer (Samsung N130) is suitable for running pSX.). 
  When running pSX on ubuntu 9.10NBR the general sound is o.k (sound effects e.t.c) but the XA sound is super sketchy for some reason. I have done the whole disable autospawn in pulse folder, install recommended alsa packages, pulseaudio -k thing but sadly to no avail. I have also tried commenting the last 2 lines of .modprobe alsaconf file, no joy there either. Still same skippy sound. 
    The onboard sound device appears to be realtek acl something or other preceeded by hda intel. (i.e it would appear to be an integrated onboard chip). I've heard some bad things about these, but am certain that if it can run under windows no problemo, then its probably but a wee bit of code away from running on ubuntu 9.10NBR. Im sure this is a pretty mainstream problem (lots of people seem to be mentioning the sound underrun thing), and thus wondered if anyone was "on the case" so to speak, or if any solutions have been found to the problem. When i run pSX as root i get something to do with breadcrumbs as an error line if that helps at all =P, and generally as aforementioned buffer or sound underrun appears quite frequently too.
  Any suggestions are more than welcome =) 
Cheers - Eiji Takanaka (7G operator)

P.s the whole kill pulseaudio thing does work to solve zsnes emulator sound problems though!

---

### Post by warfacegod on 2010-01-13
Instead of Realtek something or other try using: 

```
sudo lshw
``` 

and posting this portion of the results:

>        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:c0000c00-c0000dff memory:c0000800-c00008ff


To copy and paste in Terminal use Shift+Ctrl+c or v

---

### Post by warfacegod on 2010-01-13
This might be useful as well:

```
amixer get Master
```

Example:

> Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [on]
  Front Right: Playback 63 [100%] [0.00dB] [on]


You said you did "the whole kill pulseaudio thing"... so I'm not sure if this one will work for you or not. See what happens.

---

### Post by danwosere2007 on 2010-01-14
Yo. I did the whole lshw (List hardware? at a guess;) thing this is the result for the sound card ;)

*-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0440000-f0443fff

As i said it shows up as Realtek ACL 9somthing something in alsa when pulseaudio has been temporarily disposed of. Any suggestions/help appreciated! :) (cheers war by the way thats a useful little command to see what hardware is on the system ;)

---

### Post by warfacegod on 2010-01-14
Glad you like the code. I don't have any real advice for you concerning your pSX sound issue. I just thought posting the output of those codes might be applicable to your issue. Another useful code is:

```
uname
```

Type man uname for a list of different options for it.

---


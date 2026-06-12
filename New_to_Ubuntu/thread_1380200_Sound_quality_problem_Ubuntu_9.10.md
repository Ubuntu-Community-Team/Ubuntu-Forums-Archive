---
title: "Sound quality problem Ubuntu 9.10"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Tlah on 2010-01-13
I'm new in Ubuntu NR, I had Fedora before but I couldn't solve this same problem.
The audio quality is really low in comparative with Windows.
I was wondering if there is a way to have the same audio quality I had before switching to Ubuntu, by now thats the only problem I have.

Info:

```

card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 52400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```I've been reading, and I figured out that ALSA doesn't support ICH8 Family, but the pages I read from were old.

PS: I'm using Spotify (Wine) and with the "esound package" it works 100% good, nice audio quality; so I believe its not a hardware problem.

---

### Post by Forbees on 2010-01-13
i would expect the sound problem to follow you into wine as well considering wine runs through ubuntu . . 

what netbook are you running? it could be a known probelm with just your netbook

i run an asus eeePC 1000ha, in 9.10;

back in 9.04 there were known problems with wifi and fixes for it, but with 9.10 thats no longer a problem

sorry i can't be of any REAL help, but worst comes to worst it might be fixed in the next distro

---

### Post by lavinog on 2010-01-13
can you describe the audio quality issues you are having?
Is the volume too low, or is there distortion or poping noises?

---

### Post by Tlah on 2010-01-13
I run a Compaq Presario C727US with Ubuntu Netbook Remix.
Actually I had problems with the Wifi too, but I managed to solve it.

---

### Post by Forbees on 2010-01-13
what kind of sound problems are you having? as lavnog asked?

pops? distortion? static? 

in 9.04 whenever i muted the sound it just turned to pure static, but now in 9.10 mute works fine

---

### Post by Tlah on 2010-01-13
Poor quality sound.
Like the audio files are in a very low bitrate.

---

### Post by Forbees on 2010-01-13
hmmm you have the "restricted extras" installed i'm assuming . . 

have you tried a different media player?

---

### Post by Tlah on 2010-01-13
Thanks, all my audio files work better in Banshee, but I'm still having the same problem with audio in Firefox

---

### Post by Tlah on 2010-01-13
Just if it helps someone, I solved the audio problem in Firefox installing VLC Media Player with the plugin for Mozilla

```
 apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc 
```

---

### Post by Forbees on 2010-01-13
my next sugestion would have been try lowering the audio levels in ```
alsamixer
```

by lowering most the levels in the green mode i've solved my music "server" from distorting 

this issue was found today and fixing it reminded me of you lol

---


---
title: "No sound from speakers with Realtek ALC3223 on 14.04 LTS"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by francescopontillo on 2015-03-20
My Dell 7537 can't seem to output audio through its speakers, headphones work great. Both work under Windows.
Here's my audio card configuration:

```
fra@fra-pc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC3223 Analog [ALC3223 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
fra@fra-pc:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xe3614000 irq 64
 1 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xe3610000 irq 63

```

```
fra@fra-pc:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

```

Anyone knows what might be the issue?
Kernel version is 3.16.0-31-generic.

---


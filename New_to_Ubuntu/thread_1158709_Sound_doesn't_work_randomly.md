---
title: "Sound doesn't work randomly"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by l-x-l on 2009-05-13
I've done a decent amount of research on this before I decided to post for help. I have a Dell E1705 laptop with a fresh install of Jaunty. I believe my soundcard is a SigmaTel STAC9200 (that's what I see in Gnome ALSA mixer). When the login screen first comes up I always hear the drums. So no problem there. But after entering my proper password, I don't always hear the login sound. Sometimes I do & sometimes I don't. This occurs even after a reboot (sometimes I hear it & sometimes I don't). That's usually my first sign of whether sound works or not. Then I try to play a CD or watch something on Youtube to confirm if sound works. And it if I didn't hear the login sound, then all other sound usually doesn't work.

What's weird is that on the occasions where I boot-up into Ubuntu & the sound works, if I was to log-off for whatever reason & log back in, sometimes the sound would be gone.

All the levels on Volume control are up. Nothing is muted. When I click on Preferences, everything is checked off (Master, PCM, LFE, Capture, Mux, IEC958, IEC958 Default PCM, Input Source). I've installed Gnome ALSA mixer. No help. I've installed aumix & made sure the levels were all the way to the right. Nothing. 

I've read about adding to the last line of /etc/modprobe.d/alsa-base.conf "options snd_hda_intel xxx...=xxxx...." but I have no idea of how to find the xxx info needed. Any help on this problem would be much appreciated. Below is some info that may help.


cat /proc/asound/modules
```
0 snd_hda_intel
```

cat /dev/sndstat
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)Kernel: Linux Bakery-PC 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Config options: 0
```

lspci -v
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 01)
        Subsystem: Dell Device 01cd
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```


aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L:
```
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
```

---

### Post by l-x-l on 2009-05-13
Quick update:

When I do the following sound returns.

```
killall pulseaudio

sudo alsa force-reload
```

Still I don't think I should have to do this each time I boot-up or login for the sound to work. Any help would be appreciated.

---

### Post by l-x-l on 2009-05-14
Ok... I toyed around some more with this problem. My sound was working fine so I decided to logout & quickly log back in to test if the sound would work. Sure enough after I logged back in it no longer worked. I then went to System Log viewer to see if I could find what's happening. Under user.log I saw this 

```
May 14 05:25:46 My-PC bonobo-activation-server (lxl-16770): could not associate with desktop session: Failed to connect to socket /tmp/dbus-vMGgPxCG5l: Connection refused
May 14 05:25:56 My-PC pulseaudio[16862]: pid.c: Stale PID file, overwriting.
May 14 05:25:58 My-PC pulseaudio[16862]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
May 14 05:25:58 My-PC pulseaudio[16862]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
May 14 05:25:58 My-PC pulseaudio[16862]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
```

---


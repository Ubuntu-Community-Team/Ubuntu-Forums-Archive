---
title: "audio doesnt work"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Drenriza on 2009-11-24
i have upgraded to the new ubuntu version 9.10, and now my audio controller doesn't work.

Audio hardware information.
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

hope some1 can help me.
Thanks on advance:KS

---

### Post by Orian90 on 2009-11-24
Did check your whether your sound was muted or not? Mine was muted the first time I started, and I had been searching for an hour before I found out it was :rolleyes:

If it isn't I don't know what it could be, maybe someone with more experience does ;)

---

### Post by Julita on 2009-11-24
Comprehensive Sound Problem Solutions Guide might help you: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Drenriza on 2009-11-25
unfurtiantly my sound arnt muted  :(

And that is 1 long-axx guide :)

---

### Post by VertexPusher on 2009-11-25
Run speaker-test and check its output for error messages.

---

### Post by Drenriza on 2009-11-25
speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11,354161
 0 - Front Left
Time per period = 11,359570
 0 - Front Left
Time per period = 11,359837
 0 - Front Left
^C

---

### Post by VertexPusher on 2009-11-25
> **Drenriza said:**
>  0 - Front Left
Time per period = 11,354161
 0 - Front Left
Time per period = 11,359570
 0 - Front Left
Time per period = 11,359837
 0 - Front Left
^C
ALSA is working fine. If the device is not muted, there must be a routing problem in PulseAudio.

---

### Post by Drenriza on 2009-11-26
How can i fix that?

---

### Post by Drenriza on 2009-11-30
$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


what does that mean?

---

### Post by Julita on 2009-12-02
Removing pulseaudio entirely can solve the problem. At least, I don't have strange sound issue any longer (Well, I have, but not because of the software ;))

---

### Post by llamabr on 2009-12-02
> **Julita said:**
> Removing pulseaudio entirely can solve the problem. At least, I don't have strange sound issue any longer (Well, I have, but not because of the software ;))

Yes, I solved a similar problem with:

```
sudo apt-get remove pulseaudio
```

---

### Post by Drenriza on 2009-12-03
how can i remove it entirely from the pc.

---

### Post by Julita on 2009-12-03
You need to open the terminal and type the command there: 

```
sudo apt-get --purge remove pulsaudio
```

---

### Post by Drenriza on 2009-12-04
i have now tryed to use the command remove and purge pulseaudio.
but i still have 0 sound. what can i then do?

---

### Post by Julita on 2009-12-04
Type from terminal

```
alsamixer
``` you will see the table where you are able to configure your sound input/output. Where you see gray box with 00, it means that something is muted. To unmute it, use keyboard button "m." Pay attention to Master, Master M, PCM, CD, PC Speak. Unmuting them can help. Use "up" arrow of your keyboard to increase the volume.

---

### Post by Drenriza on 2009-12-08
Nothing is muted, in alsamixer.

When i start my computer i also get sound for about 1sec. The sound that comes where you can enter username and password to enter the pc.

But after i have logged on, the sound disapears 100% again.

---

### Post by Julita on 2009-12-08
I have found this [help.ubuntu.com/community/HdaIntelSoundHowto](help.ubuntu.com/community/HdaIntelSoundHowto) it seems that there are issues with your card with ubuntu. In this theme [http://ubuntuforums.org/showthread.php?t=1335644](http://ubuntuforums.org/showthread.php?t=1335644) the OP has the same problem. Try looking at the first link. It should be useful.

---

### Post by Drenriza on 2010-01-04
Solved. Removed audiopulse and installed alsamixer

---


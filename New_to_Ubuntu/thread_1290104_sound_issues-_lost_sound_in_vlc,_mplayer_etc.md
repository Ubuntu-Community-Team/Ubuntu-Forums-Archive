---
title: "sound issues- lost sound in vlc, mplayer etc"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by M0GEJ on 2009-10-13
Last night the sound on my laptop decided to stop working on vlc but is fine on flash.  I had this problem a while back when I upgraded to Jaunty but managed to get it sorted eventually.  I am not sure what I did to get it fixed then: any ideas?

---

### Post by Oak37 on 2009-10-13
I'm not at my computer now but can you choose which sound device to use within VLC's settings?

---

### Post by M0GEJ on 2009-10-13
I can go into tools --> preferences --> audio, and change the output type.  I have tried a few of these but have not had any luck so far...

---

### Post by bruno9779 on 2009-10-13
Have you tried the classic?:

close affected program

alt+F2

```
killall pulseaudio
pulseaudio
```

restart the program

---

### Post by M0GEJ on 2009-10-13
I just tried that and get the following message when I enter in pulseaudio:

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
W: module-rtp-send.c: Failed to push chunk into memblockq.
W: module-rtp-send.c: Failed to push chunk into memblockq.
W: module-rtp-send.c: Failed to push chunk into memblockq.

I have been to user settings --> manage groups, and am listed as being in the "pulse-rt" group.

---

### Post by bruno9779 on 2009-10-13
have you been messing with chmod and chown?
seems like some ownership is out of place

---

### Post by M0GEJ on 2009-10-13
Interesting: the one output type I hadn't tried (ESounD audio output) seems to solve the problem in vlc:)

I am not sure what went wrong there yesterday as I was watching a dvd, left the room to go and get something to eat and lost sound when I tried to play another episode....

---


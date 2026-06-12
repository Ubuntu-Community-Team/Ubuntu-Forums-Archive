---
title: "Sound detection problems"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by dan1973 on 2009-05-05
Good morning,

Have just installed jaunty Xubuntu on an IBM thinkpad A21e (old)

Am having trouble with the sound. Worked fine for about 1 minute, then produces a 'screechy' kind of old school dial-up modem noise and has subsequently stopped working.

Could somebody give me some ideas as to where to start troubleshooting this.

Have another similar machine which i am installing Xubuntu on to find out if it's just the onboard speakers which have fried.

Many thanks,

---

### Post by dan1973 on 2009-05-05
Have more info to add. Output of aplay -l is as follows:

```
ubuntu@ubuntu-laptop:~$ aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: I440MX [Intel 440MX], laite 0: Intel ICH [Intel 440MX]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
ubuntu@ubuntu-laptop:~$ 
```

output of aplay -L as follows:

```
ubuntu@ubuntu-laptop:~$ aplay -L
front:CARD=I440MX,DEV=0
    Intel 440MX, Intel 440MX
    Front speakers
surround40:CARD=I440MX,DEV=0
    Intel 440MX, Intel 440MX
    4.0 Surround output to Front and Rear speakers
surround41:CARD=I440MX,DEV=0
    Intel 440MX, Intel 440MX
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I440MX,DEV=0
    Intel 440MX, Intel 440MX
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I440MX,DEV=0
    Intel 440MX, Intel 440MX
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=I440MX,DEV=0
    Intel 440MX, Intel 440MX
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

Hope this helps,

---


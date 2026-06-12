---
title: "Master Sound is controlling NOTHING"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by ima5k on 2010-05-25
The Master sound, although master, is not controlling anything.
As a result, when i change the sound from my keyboard nothing happens.
How can i fix this, namely, when i change the master sound output then the whole system sound change?

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Ubuntu 10.04

Thanks in advance

---

### Post by -humanaut- on 2010-05-25
Click the sound icon go to Sound Preferences --> Hardware and make sure your hardware is detected and set correctly.

---

### Post by ima5k on 2010-05-25
I think it is. The profile i use is Analog Stereo Duplex, but even if i choose any working setting the result is the same. Master channel still make no use.
Any other suggestion?

---

### Post by -humanaut- on 2010-05-25
hmm... That's strange You do have sound right? Also check the output section of Sound preferences.

---

### Post by ima5k on 2010-05-26
Yes, there is sound but changing Master makes no difference (although when i change PCM or Front i have proper increment/decrement of the output volume).
I tried every possible working setting from SoundPreferences but failed to make it work.

---

### Post by ima5k on 2010-05-27
Any other suggestions to this?

---

### Post by lidex on 2010-05-27
So basically you need the volume control/keys to control PCM. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by ima5k on 2010-05-28
I have set my volume keys to control PCM, this is my solution so far,but i want the Master Sound to work. So:

uname -a
```
Linux #### 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```* I use the Analog device

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```head -n 1 /proc/asound/card*/codec#*
```
Codec: VIA VT1708S
```This is a custom PC, i set up on my own but, might, the mainboard model will help.
It is a ASRock A780GXH/128M

**and thanks for your reply

---

### Post by Je Et on 2010-07-23
Sorry to jump in here, but what do you do if you get this:

[B]shango@shango-desktop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory[/B]

---

### Post by lidex on 2010-07-23
> **Je Et said:**
> Sorry to jump in here, but what do you do if you get this:

[B]shango@shango-desktop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory[/B]

Either alsa is borked or your codec is AC97 or another type not falling under that driver or hda-intel.
For AC97:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```

---

### Post by lidex on 2010-07-24
*ima5k*
have a look here:
[http://ubuntuforums.org/showpost.php?p=9377246&postcount=33](http://ubuntuforums.org/showpost.php?p=9377246&postcount=33)

---

### Post by ima5k on 2010-07-24
Thnx, but still can't get MASTER sound to work

---


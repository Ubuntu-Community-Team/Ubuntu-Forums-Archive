---
title: "installing snd-es1938 help"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by raddad on 2009-03-20
Alright. So we gave up on the creative labs card (unsupported). We went out and purchased the ESS 1938 4-channel PCI Sound Card. :|

We did add snd-es1938 to the /etc/modules and then reboot. In System>Pref>Sound, ESS Solo-1 shows up and for Default Mixer Tracks, we have
ESS ES1938 (Solo-1) (ALSA mixer) selected. 

Still, no sound.

I did check alsamixer to see if anything was muted and everything showed up fine.

Still no sound.

Any ideas?

Edit: running ubuntu 8.04 Hardy Heron. just for reference.

---

### Post by markbuntu on 2009-03-20
Your best bet would be to remove alsa and reinstall it and reboot. It should find the card and load the driver automagically.


(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

This will get rid of all those pesky settings from before and give you a clean slate to totally mess up all by yourself. Just kidding. If you need more help go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by raddad on 2009-03-20
Ok. I thought It gave me an error. I reopened terminal and it worked on reinstall stage. I'm gonna keep going with thte rest of the process.

---

### Post by raddad on 2009-03-20
Ok. Finished the process and rebooted. No sound still. I also checked alsamixer once more just in case.

---

### Post by markbuntu on 2009-03-20
What does aplay-l tell you?

---

### Post by raddad on 2009-03-20
> **markbuntu said:**
> What does aplay-l tell you?

Here is the result
```

raddad@Lenny:~$ aplay-l
bash: aplay-l: command not found

```

:confused:

---

### Post by markbuntu on 2009-03-20
did you put a space between aplay and -l?

---

### Post by raddad on 2009-03-20
> **markbuntu said:**
> did you put a space between aplay and -l?

nope. ahhhh.  no I didn't. when I first saw the error, I copied it from your previous post just in case. :D

Here is the new outcome, after adding the space.

```

**** List of PLAYBACK Hardware Devices ****
card 0: Solo1 [ESS ES1938 (Solo-1)], device 0: es-1938-1946 [ESS Solo-1]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

---

### Post by markbuntu on 2009-03-22
Well that means that the system sees your sound card and has the driver loaded so more basic troubleshooting is in order.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---


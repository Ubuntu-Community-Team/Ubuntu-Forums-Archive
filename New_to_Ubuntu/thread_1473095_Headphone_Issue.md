---
title: "Headphone Issue"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by gameyharp on 2010-05-04
First time linux user here was referred to these forums by a kind soul on reddit :D. The issue I'm having is that I can't get my media player (rhythmbox) to play my music through my headphones. When I login I get the login tone through my headset and when I get messages via pidgin I get them through my headset as well. I do have my system>pref set to headset and I actually disabled my laptop speakers sound so I don't even see it in the list anymore. Any suggetsions? (running on an asus n90sv)

EDIT: To clarify since I didn't really state it the sound comes out of my laptop speakers instead via headset :*(.

---

### Post by Cowboybebop79 on 2010-05-05
What type of earphones/headset are you using bluetooth or ordinary plugin?

---

### Post by lidex on 2010-05-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by gameyharp on 2010-05-05
I'm using just a normal logitech usb headset. Not sure what you mean by posting in code tags but here is what I got:

Linux gameyharp-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux (uname -a)

**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
aplay -l


Advanced Linux Sound Architecture Driver Version 1.0.20. (
cat /proc/asound/version


Codec: Realtek ALC663
head -n 1 /proc/asound/card*/codec#*

---

### Post by _0R10N on 2010-05-05
> **gameyharp said:**
> I'm using just a normal logitech usb headset. Not sure what you mean by posting in code tags but here is what I got:

Linux gameyharp-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux (uname -a)

**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
aplay -l


Advanced Linux Sound Architecture Driver Version 1.0.20. (
cat /proc/asound/version


Codec: Realtek ALC663
head -n 1 /proc/asound/card*/codec#*


I'm assuming that you have a fresh install. So, I recommend you to before doing anything, update your whole system by running:
```

sudo aptitude update
sudo aptitude upgrade

```
If the problem persists, then check your sound preferences. Under the System->Preferences->Sound, check you have these values set in the corresponding tabs.

---

### Post by gameyharp on 2010-05-05
I've updated/upgraded + dist-upgrade. I've been in sound prefrences the last couple days trying to resolve this. Any other suggestions?

---

### Post by lidex on 2010-05-05
Go to this page and work through it:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") Make sure to install the alsa-backports. After a reboot go into 'System>Preferences>Sound' and make sure your settings are correct.

---


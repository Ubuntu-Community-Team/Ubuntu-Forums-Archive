---
title: "Login Screen has sound, the OS itself doesn't"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by abben on 2008-12-19
Hey all. I am fairly used to having to manually install my sound blaster 16 drivers after any fresh ubuntu install, but its particularly troublesome this time around.

Here is what I know:

- I get the login noise (working sound) at startup
- I don't get working sound once I am at the desktop
- typing aplay -l in the terminal shows:
```
**** List of PLAYBACK Hardware Devices ****
card 0: S16 [Sound Blaster 16], device 0: SB16 DSP [DSP v4.13]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
- I've looked at alsamixer, I don't think I have it muted
- The driver I'm using, sb16, has worked on this computer in the past.

Any thoughts?

---

### Post by abben on 2008-12-19
shameless  bump

---

### Post by starcannon on 2008-12-19
All I can think of is fiddling around in the sound gui:
System>Preferences>Sound
Change things to Alsa to start with, liberally use the "Test" button, continue your customising until you get Test to work on all the options listed(you'll have to do other testing for the mic/mic input)

Also worth mentioning is that I have found that on some hardware I have had to choose the specific sound chipset from the dropdown menu in the sound gui as well; the one labled:
[B]Default Mixer Tracks:
[/B]Device: [some device listed here]

GL wish I had more to offer you.

---

### Post by linux_tech on 2008-12-19
Try installing gnome-alsamixer if you have not yet installed it. Run it and adjusting settings
In terminal (Applications>Accessories>Terminal) type:

```
sudo apt-get install gnome-alsamixer
```

Make sure nothing is muted and try unchecking the option for Audigy Analog/ digital output jack.

If still nothing try this next
```

sudo /etc/init.d/alsa-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start

```

---

### Post by abben on 2008-12-19
First, thanks for your time & advice. I just kind of figured it out, as in. I'm not getting access to the sound card unless I do sudo first. 

if I run:

```
gnome-alsamixer
```

I get nothing. If I run:

```
sudo gnome-alsamixer
```
it shows me my dials

similarly, if I do
```
totem 01\ Don\'t\ Touch\ Dead\ Animals.mp3
```
Totem runs, I even get a nice vizualization, but no sound.

If I do
```
sudo totem 01\ Don\'t\ Touch\ Dead\ Animals.mp3
```

I have my sound. Any way I can make this run without root access? Thanks again for the advice.

---

### Post by linux_tech on 2008-12-19
> **abben said:**
> 

I have my sound. Any way I can make this run without root access? Thanks again for the advice.

This explains sudo usage quite well-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by markbuntu on 2008-12-19
If you get the login sound that means your sound card is basically working and you just need some help with setting it up

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by shecky on 2008-12-19
Add yourself to the audio group. If you're using pulseaudio, add yourself to the pulse groups as well.
```
sudo usermod -G `groups|sed 's/ /,/g'|sed 's/$/,audio,pulse,pulse-rt,pulseaudio/'` YOURUSERNAME
```

Log out, then back in. Should fix it right up.

---

### Post by annda on 2008-12-19
UPDATE: TOO LATE


check if you are allowed to use audio as a user, this is actually a standard setup, but who knows - are you a member of the 'audio' group?

```
groups
```

---

### Post by abben on 2008-12-19
> **shecky said:**
> Add yourself to the audio group. If you're using pulseaudio, add yourself to the pulse groups as well.
```
sudo usermod -G `groups|sed 's/ /,/g'|sed 's/$/,audio,pulse,pulse-rt,pulseaudio/'` YOURUSERNAME
```

Log out, then back in. Should fix it right up.

Thanks shecky. I don't use pulseaudio, (nor am I clear on its purpose). But I have added myself to the "audio" group, and I can listen to audio without sticking a sudo on the front.

Now, my latest joy is a total lockup 5-10 seconds into that audio. I'll let you all know if I figure anything out. Thanks for the help.

Edit: Ok. I had toyed around with pulse-audio stuff before uninstalling it. I think the problem was using "pulseaudio" as a default sound card instead of good ol sb16. I changed it back, and (on top of everything I've done since starting this thread), things seem to be working fine now. Thanks again for the help.

---


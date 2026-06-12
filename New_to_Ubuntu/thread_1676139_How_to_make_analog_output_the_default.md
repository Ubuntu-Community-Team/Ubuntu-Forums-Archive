---
title: "How to make analog output the default"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Keith Myers on 2011-01-26
:(Ever since I made a new computer with onboard audio the default output device always becomes the High Definition Audio output device.  I get no sound until I go into the audio preferences and select the analog audio output device.  I have disabled the HD audio output device but every time I boot the system, it always defaults back to HD audio.  How do I get the system to ignore the HD audio and make the analog output device the default?

Keith

---

### Post by gordintoronto on 2011-01-26
Do you use Preferences/Sound, and the hardware tab, to make the change? What devices show up there?

What version of Ubuntu?

An HDAudio device normally produces analog output, so your post is a little confusing.

---

### Post by Keith Myers on 2011-01-27
> **gordintoronto said:**
> Do you use Preferences/Sound, and the hardware tab, to make the change? What devices show up there?

What version of Ubuntu?

An HDAudio device normally produces analog output, so your post is a little confusing.

Yes I do use the Preferences/Sound tool to change the output device so I can hear sound out of my powered analog speakers.  The devices that show up in the Sound Preferences/Hardware tab are:

GF104 High Definition Audio Controller
1 Output
Digital Stereo (HDMI) Output

Internal Audio
1 Output/1 Input
Analog Stereo Duplex

The Sound Preferences/Output tab shows:

<bullet> Internal Audio Analog Stereo
             Stereo

<no bullet> GF104 High Definition Audio Controller Digital Stereo (HDMI)
                   Stereo

I am not connected to any digital audio devices.  I just use the powered speakers on the desktop.

I am running Ubuntu 10.10 64bit.  The problem is that every time I boot, the sound output gets set to the GF104 device and I have no sound. As soon as I open Sound Preferences and change the output device back to Analog Stereo Output, then I get my sounds back.  I have been reading about audio in the forums for days now and have not come across my problem.  All the problems I have seen documented are about the opposite issue of not having digital audio working.  I may or may not have that problem, I haven't tested the system with digital audio.  I will cross that bridge when I get to it.  For now, I just want sound out of my analog speakers as default when the system boots and initializes. I am connected to the Line Out connector at the backside of the motherboard.

Any ideas where I go to change the default behaviour of the system to use analog audio output?

Cheers,  Keith

---

### Post by gordintoronto on 2011-01-27
Sorry, I would expect that when I choose a sound device, it stays selected even if I reboot.

---

### Post by Keith Myers on 2011-01-28
The problem is not show-stopping, just annoying.  I just have to change the output device every time I boot into Ubuntu.  I also liked the greeting sound of the system booting as I can start the computer and walk out of the room and know that the system booted correctly when I hear the system initialization sound.

Keith

---

### Post by cariboo on 2011-01-28
You can use alsamixer to set your default audio device, once you have alasmixer running, press F6 to select the your sound device, once you are done, press esc to exit, then in the same terminal, type:

```
sudo alsactl store
```

to save your settings.

---


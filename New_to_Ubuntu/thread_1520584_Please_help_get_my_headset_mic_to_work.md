---
title: "Please help get my headset mic to work"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2010-06-29
I can't record anything with the microphone on my headset. I opened up alsamixer, but there are so many settings and I don't know what I'm doing.

My headset: [http://www.plantronics.com/north_america/en_US/products/computer/gaming-headsets/gamecom-367](http://www.plantronics.com/north_america/en_US/products/computer/gaming-headsets/gamecom-367)

I have two audio devices, I believe. One is built in to the motherboard (not the one I want to use), and the other is (I believe) an Audigy 2 ZS or something like that. I'm afraid I don't know for sure!

If there's some kind of information you need, please let me know how I can find it. Thanks.

---

### Post by tbohaning on 2010-06-29
Try starting pavucontrol. It gives you full control of all of the devices when they are in use. I had a similar issue with Skype and this tool allowed me to enable the mic and head set when I needed it.

---

### Post by Cleveland Rock on 2010-06-29
The problem is, I don't know how to get it to detect anything.

---

### Post by Jakiejake on 2010-06-29
> **Cleveland Rock said:**
> I can't record anything with the microphone on my headset. I opened up alsamixer, but there are so many settings and I don't know what I'm doing.

My headset: [http://www.plantronics.com/north_america/en_US/products/computer/gaming-headsets/gamecom-367](http://www.plantronics.com/north_america/en_US/products/computer/gaming-headsets/gamecom-367)

I have two audio devices, I believe. One is built in to the motherboard (not the one I want to use), and the other is (I believe) an Audigy 2 ZS or something like that. I'm afraid I don't know for sure!

If there's some kind of information you need, please let me know how I can find it. Thanks.

System -> Preferences -> Sound
Does It show up in there?

---

### Post by Cleveland Rock on 2010-06-29
> **Jakiejake said:**
> System -> Preferences -> Sound
Does It show up in there?
By "it", I assume you mean my sound card. It says "CA0106 Soundblaster", which is apparently Creative Labs Audigy LS. Good to know. The other is just called "Internal Audio".

---

### Post by lidex on 2010-06-29
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by Cleveland Rock on 2010-06-30
I don't know what I'm doing here, but I unmuted everything in gnome-alsamixer and dragged all the sliders to the top, then tried every setting on the "input devices" tab of pavucontrol, and none of them seem to be picking up any sound.

---

### Post by lidex on 2010-06-30
In pavucontrol, on 'Input Devices' tab for mic press middle icon to unlock channels then move one of the sliders all the way down and set the other at 100%.

---

### Post by Cleveland Rock on 2010-07-01
I'm afraid that did nothing, lidex.

---

### Post by Cleveland Rock on 2010-07-01
Crap! I apparently did *something* in the mixer, because now none of my games have sound! I have sound for everything else, though…

Edit: Whoops. Sorry for the double post.

---

### Post by Cleveland Rock on 2010-07-03
Sorry for the TRIPLE post, but I really want to get my sound output working in games. The microphone is a lower priority now&#8230;

---

### Post by lidex on 2010-07-04
Try re-installing your sdl lib:
```
sudo apt-get install --reinstall libsdl1.2debian-pulseaudio
```

---

### Post by Cleveland Rock on 2010-07-04
Nope, that wasn't it.

I still think it was something I did in gnome-alsamixer that caused the problem, so maybe you could look at my mixer and see if there are any problems.

[http://img64.imageshack.us/img64/6407/screenshotgnomealsamixe.png](http://img64.imageshack.us/img64/6407/screenshotgnomealsamixe.png)

---

### Post by Cleveland Rock on 2010-07-04
I fixed my output problem. I went into the Sound Preferences and changed my hardware profile, then changed it back. For whatever reason, this fixed it.

However, there is still the issue of getting my microphone to work…

---

### Post by lidex on 2010-07-05
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Cleveland Rock on 2010-07-05
> **lidex said:**
> Provide a link for the output
Here you go:
[http://www.alsa-project.org/db/?f=f5fb9ab768c028f6299e06745edab7875be3982b](http://www.alsa-project.org/db/?f=f5fb9ab768c028f6299e06745edab7875be3982b)

---

### Post by lidex on 2010-07-05
You say you want to use the audigy, correct? Your install sees the other sound card as default. Try disabling onboard audio in the bios first.

---

### Post by Cleveland Rock on 2010-07-05
I'm afraid you'd have to tell me how to do that, or else I'd *really* mess things up.

---

### Post by lidex on 2010-07-05
Reboot and you'll see a screen with some text that should tell you how to enter bios setup. Usually you just press a key - mine is <delete>, yours may vary. You'll need to be quick about it though. If you miss it just start over. Once in the bios setup maneuver through the options using arrow keys until you find something similar to 'onboard devices'. Hit enter to edit. Select onboard audio and disable. Save to bios (probably <F10>)and exit.

---

### Post by Cleveland Rock on 2010-07-07
Okay, here's my new output:
[http://www.alsa-project.org/db/?f=f1886f1bec0dcf7ccef01efc131f6dff479943ca](http://www.alsa-project.org/db/?f=f1886f1bec0dcf7ccef01efc131f6dff479943ca)

---

### Post by lidex on 2010-07-07
Have a look here:
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9350880&postcount=16]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9350880&postcount=16")

---

### Post by Cleveland Rock on 2010-07-07
Nope. No luck. Although, I did notice something.

No matter what I choose for "port", this is what it looks like when I'm tapping my microphone trying to get it to pick up sound:
[http://img268.imageshack.us/img268/5206/screenshotvolumecontrolv.png](http://img268.imageshack.us/img268/5206/screenshotvolumecontrolv.png)

And here's what it looks like when I'm listening to Devo:
[http://img812.imageshack.us/img812/2024/screenshotvolumecontrol.png](http://img812.imageshack.us/img812/2024/screenshotvolumecontrol.png)

---

### Post by wonderingwhy on 2010-07-08
I have this exact same issue with the mic, and I've just upgraded to 10.04.  When doing a test call through skype I was watching the Pauvcontrol and skype was taking it's input from the internal audio analogue stereo instead of the webcam.  Maybe this is Cleveland Rock's same issue.  

I'm new at this too and don't know how to fix it.  Any direction would be great.

---

### Post by lidex on 2010-07-08
Try paprefs. You'll need that and padevchooser. If not installed:
```
sudo apt-get install paprefs padevchooser
```

Open 'Pulseaudio Device Chooser' from 'Sound & Video' menu. An icon will appear in notification area. Click that icon and choose 'Configure Local Sound Server'. On the 'Simultaneous Output' tab check/select the option there 'Add vitual output...'

BTW, you have in first screenie soundblaster set as fallback, try disabling that option.

---

### Post by Cleveland Rock on 2010-07-08
No luck! Argh!

---

### Post by wonderingwhy on 2010-07-08
Thanks lidex, it worked a treat, you rock :guitar:

---


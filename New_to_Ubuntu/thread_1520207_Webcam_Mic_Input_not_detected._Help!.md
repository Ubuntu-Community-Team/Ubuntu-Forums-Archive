---
title: "Webcam Mic Input not detected. Help!"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by christafo on 2010-06-29
Very new to ubuntu.

My problem is as follows.

Neither skype or ubuntu will recognise the inbuilt mic on my Lifecam VX 5000 as an input option. It recognises it as hardware, but there is no dropdown option in the input tab of the audio settings panel.

The weird thing is, before i moved my computer and had to unplug everything, it worked fine. Im confused as to why it no longer works, despite the only thing that's changed being the usb slot im now using, and the geographical location. Naturally the latter is a moot factor, but does the fact im using a different uSB slot have anything to do with it?

Help!

Thanks in advance x

---

### Post by zkriesse on 2010-06-30
Ok, I can tell you right now that while Skype may look like it's not taking your mic I'm pretty sure it is in fact working just fine. Don't panic, it's going to ok! Go to [COLOR="Blue"]System -> Preferences -> Sound -> Input Tab[/COLOR] In the input tab click the radio button for your mic, and you should be ok. If that doesn't work let me know and we'll think of something else ok?

---

### Post by flakzeus on 2010-07-06
I'm actually having the same issue. On the input tab, I've got three options. 
1) Microphone 1
2) Microphone 2
3) Line-In

None of these seem to work with my VX-5000. The video works with Skype however. 

Any ideas?

---

### Post by lidex on 2010-07-07
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


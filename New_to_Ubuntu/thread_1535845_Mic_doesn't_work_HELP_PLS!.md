---
title: "Mic doesn't work HELP PLS!"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by The Real Pelana on 2010-07-21
Hello Im a happy Ubuntu user since sunday morning. I downloaded skype and realized the microphone doesnt work. Thus I opened up the voice recording included with 10.4 LTS and I couldnt record a single word.
Can anyone guide through the steps to get my mic back to work?

Thank you!

---

### Post by Joe of loath on 2010-07-21
It would really help if we knew what sound card you had ;)

---

### Post by The Real Pelana on 2010-07-21
> **Joe of loath said:**
> It would really help if we knew what sound card you had ;)


All info i can get is that it is a realtek sound card... does that helps?

---

### Post by Chris1274 on 2010-07-21
Try this:

Go to Applications > Sound & Video > Sound Recorder

Under File, click on Open Volume Control

Click on the Input tab and uncheck "Mute"

Hopefully that will get your mic working.

---

### Post by The Real Pelana on 2010-07-21
> **Chris1274 said:**
> Try this:

Go to Applications > Sound & Video > Sound Recorder

Under File, click on Open Volume Control

Click on the Input tab and uncheck "Mute"

Hopefully that will get your mic working.




Nope it seems that unmuting is not the problem either...

---

### Post by Chris1274 on 2010-07-21
Do you have the appropriate driver installed?

---

### Post by The Real Pelana on 2010-07-21
I can hear very well. My volume control even works with Fn+Up or down keys.
Its just that last night I tried to use Skype and realized that my mic wasnt working.

How, from where and which driver do I need please?

---

### Post by Chris1274 on 2010-07-21
Open the Sound Preferences as before, only this time open the Hardware tab and see if your device is configured.

---

### Post by The Real Pelana on 2010-07-21
> **Chris1274 said:**
> Open the Sound Preferences as before, only this time open the Hardware tab and see if your device is configured.




Its all blank. There are no options at all and no list of drivers either...

---

### Post by Chris1274 on 2010-07-21
Try ```
sudo apt-get update
sudo apt-get dist-upgrade
``` then restart your computer and look under System > Administration > Hardware Drivers. Hopefully the driver you need will be there for you to install. If not, someone else more knowledgeable than I will have to help you out. I'm still an ubuntu novice myself.

---

### Post by The Real Pelana on 2010-07-21
> **Chris1274 said:**
> Try ```
sudo apt-get update
sudo apt-get dist-upgrade
``` then restart your computer and look under System > Administration > Hardware Drivers. Hopefully the driver you need will be there for you to install. If not, someone else more knowledgeable than I will have to help you out. I'm still an ubuntu novice myself.



Thank you Chris Imna check it out.

---

### Post by The Real Pelana on 2010-07-21
Nope didnt work :-(

---

### Post by Legendary_Bibo on 2010-07-21
> **Chris1274 said:**
> Try this:

Go to Applications > Sound & Video > Sound Recorder

Under File, click on Open Volume Control

Click on the Input tab and uncheck "Mute"

Hopefully that will get your mic working.

Oddly enough my mic hasn't been working but when I went into those options and changed the slider bar from unamplified to 100%. It even gave me my voice recording for video recording in Cheese. :confused:

Welp, whatever works.

---

### Post by The Real Pelana on 2010-07-21
I have tried but nope, nada yet...

---

### Post by lidex on 2010-07-21
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

Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

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

Skype:
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

---

### Post by The Real Pelana on 2010-07-22
Thank you lidex. after installing alsa mixer at least i have some light noise but no voice at all.
do i have to change any command line? alsa mixer also recognizes my realtek sound card...

---

### Post by lidex on 2010-07-22
> **The Real Pelana said:**
> Thank you lidex. after installing alsa mixer at least i have some light noise but no voice at all.
do i have to change any command line? alsa mixer also recognizes my realtek sound card...
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
arecord -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by The Real Pelana on 2010-07-22
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
arecord -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)



```
Linux Marco-netbook 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

**** PLAYBACK List hardware devices****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevice: 1/1
  Subdevice #0: subdevice #0

**** CAPTURE List hardware devices****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevice: 1/1
  Subdevice #0: subdevice #0

ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                        0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                   1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 

Codec: Realtek ALC272 

Acer Aspire One D250-1151 
```

Thank you for your support Lidex!!!

---

### Post by lidex on 2010-07-22
Reference here:
[http://www.linlap.com/wiki/acer+aspire+one+d250](http://www.linlap.com/wiki/acer+aspire+one+d250)
In essence, use pulseaudio volume control. On the 'Input Devices' tab select your mic, unlock the channels and move right slider down to zero. Adjust the left for comfortable level.

---

### Post by The Real Pelana on 2010-07-22
Ok lidex, ill check it out. Thanks a lot!

Ps. I like better the Help command in Ubuntu rather than the "help" useless questionaire of xp

---


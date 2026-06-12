---
title: "USB Sound Card Problems"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by noorez on 2009-03-07
Hey, I have some questions about setting up my USB Sound Card. Here are the solutions that I've already tried that are posted on other threads on this site:

1) Set Default Sound Card to PulseAudio
2) Under Sound Prefrences set everything to PulseAudio
3) Under Multimedia Systems Selector set the Plugin to PulseAudio.

This did not work at all. I only ever got sound from the built in sound card on my laptop and sometimes it didn't work at all!

So I then tried this:

1) Set default sound card to Audio (the usb sound card)
2) Under Sound Prefrences set everything to ALSA
3) Under Multimedia Systems Selector set the Plugin to ALSA

This caused somewhat random behaviour. The totem player used the usb sound card, firefox (youtube) used the built in sound card....

Anyone else have an idea on what to do?

---

### Post by kostkon on 2009-03-07
You need to revert everything you have done back to their defaults (most importantly you need to set your sound playbacks in *System &#8594; Preferences &#8594; Sound* to *Autodetect*. Also, you can set, if you want, your sound inputs to *PulseAudio* and set an input device using the utility below.)

Then, the thing you need to do is to install the *PulseAudio Device Chooser* utility (using *Synaptic*. It will create a menu entry in *Applications &#8594; Sound & Video*). Run it, left-click on its icon in your system tray and select *Volume Control*.

In the *Input Devices* and *Output Devices* tabs you can set the default input and output device to be used by your applications. Right-click on the device you want and enable the *Default* option. Thus, I assume you'll want to set here your USB sound card as the default output device (and input if you want). Afterwards, all your applications will send their audio to your sound card by default.

Also, from there, if you want, you will be able to send the audio stream of one application from one device to another in real time (for example from your USB to your onboard card. Also, maybe in some rare cases, you will need to manually send the sound of some apps to your USB sound card). In the *Playback* tab you should see the audio streams of your running applications (the ones that produce audio only, of course). Right-click on one and select *Move Stream...* to move its audio to the device you want.

You can set *PulseAudio Device Chooser* to start every time you login from its preferences.

If you have 8.10 you are OK, you only need to do the above. If you have 8.04, then you may need to follow [this guide]("http://ubuntuforums.org/showthread.php?t=789578") to better setup your *PulseAudio*.

Hope that helps...

---

### Post by noorez on 2009-03-08
Sweet!! That did help. Using the move stream, I was able to move sound from my built in speakers to the usb ones while using flash 10 in firefox. However, I couldn't configure it so that the sound always starts from the usb speakers by default. (Even though I've set the USB speakers as default in the Output tab). Under asoundconf-gtk, what should I put the setting to:
PulseAudio, Intel (built in) or Audio (USB). I guessing its not going to be Intel!!

---

### Post by noorez on 2009-07-07
Ok...I'm having a problem again....after upgrading to 9.04 I am no longer getting any sound through the USB sound card.....even after I try to move the stream over....

any ideas..? did any settings get reset or changed upon upgrading to 9.04?

---


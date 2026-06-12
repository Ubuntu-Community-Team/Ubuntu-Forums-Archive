---
title: "Sound issues with USB speakers and gnash/flash"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Xstang55 on 2009-01-10
Hello,


1st post here! So far, love Ubuntu 8.10. 32bit

However, I've been having an issue with sound using my usb speakers while watching flash/youtube videos.That is, im not getting any.

I've been getting sound through rhythmbox and the gstreamer addons, which only confuses me more.

Here's the setup: Its a homebulit PC with a asus p5k pro motherboard (p35 chipset) and a e8400wolfdale and 8800gt. The sound is though a usb external DAC (listed as a Burr-Brown Japan PCM 2702 in the volume settings), which I have running to a '60's era Heathkit amp and phase-tech speakers.

Anyone know what to do?

Thanks.

---

### Post by kostkon on 2009-01-10
Since that in 8.10 the audio is controlled by *PulseAudio* then you could set the sound playbacks in your sound preferences (*Syste &#8594; Preferences &#8594; Sound*) to *Autodetect* and then install the *PulseAudio Device Chooser*.

Run it (it's menu entry will be in *Applications &#8594; Sound & Video*) and it will put its icon in your system tray. Left-click on its icon and select *Volume Control*.

Load a Flash video in your browser and then in the *Playback* tab in *Volume Control* you should see its audio stream (it should say something like *Firefox ALSA*). Right-click on it and select *Move Stream...* and in the list that will appear select your USB device (it you should appear there). *PulseAudio* will remember your choice the next time.

Also make sure that your set your device as the default PulseAudio output device in the *Output Devices* tab. Just right-click on entry for your USB device and enable the *Default* option.

---

### Post by Xstang55 on 2009-01-10
huge thanx for the prompt reply! appreciated!

---


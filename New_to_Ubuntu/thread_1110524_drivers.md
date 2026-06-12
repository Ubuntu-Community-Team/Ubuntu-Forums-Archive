---
title: "drivers"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Heath94 on 2009-03-29
i have ubuntu running and i have no sound and i can't turn on the diplay animations

---

### Post by llamabr on 2009-03-29
It's unlikely that this is a drivers issue.

run alsamixer, or double click on the volume icon on the task bar, and try editing the preferences, and moving the sliders.

Are they grey'd out?

Also, what system are you running?

---

### Post by cwsnyder on 2009-03-29
Display animations require a driver capable of 3D graphics acceleration for your graphics card (ie. Intel, ATI, or nVidia graphics driver installed).  It also requires a compositing manager installed, such as Compiz.  Finally, you can turn on the display animations at that point.

---

### Post by sailthesea on 2009-03-29
Your sound problem may be lack of supporting codecs for Flash and Audio I've found this works well for a startup install

Open a Terminal and put these in:

1 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
2 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
3 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

This will find the drivers and install them and should also stop any clashes You can do this same thing in Synaptic and Add /Remove but this is simpler
Good luck!
sailthesea is online now Report Post   	Edit/Delete Message

---

### Post by Hospadar on 2009-03-29
You might try checking System->Administration->Hardware Drivers

This has some third-party (non-free-as-in-speech) drivers for video cards, some wireless cards and a couple other odd items.  this might help you activate at least your 3d.

As for your sound, to best get helped and help yourself, you'll need to know what kind of sound card you have.  In a terminal (Applications->Accesories->Terminal) type in "lspci" and post the output here.  You might also be able to tell by looking at the output, common sound cards are made by sigmatel, Intel (look for HDA mixer or something like that), creative, and some others.

---


---
title: "Sound problem in 10.04"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by ravi_buz on 2010-09-06
I installed OSS following the instructions given in this link [http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html). but the installation dint go good and now i am unable to listen to any sound. Please help me to remove this and get back the old pulse.

---

### Post by dream_coder on 2010-09-06
there are instructions on that page for undoing the changes

In a terminal, run sudo dpkg-reconfigure linux-sound-base
Choose ALSA. Reboot.
Remove the libasound configuration file: rm ~/.asoundrc
Reinstall Pulseaudio and associated packages: sudo apt-get install pulseaudio indicator-sound libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 ubuntu-desktop ppa-purge
Restore the original Pulse-based Gnome volume manager: sudo ppa-purge ppa:dtl131/ppa
Configure Gstreamer for Puseaudio output by running gstreamer-properties and setting input and output to PulseAudio.
If you manually configured applications (e.g. Audacious, Audacity, Kdenlive, SMPlayer, VLC, Wine, etc.) to use OSS4, switch them back to Pulseaudio or ALSA-output.
Start gconf-editor. Open system/gstreamer/0.10/audio/default. Check if any keys (e.g. musicaudiosink and chataudiosink) are set to &#8220;osssink&#8221;. If so, change them to &#8220;pulsesink&#8221;.
Remove the OSS4 package using Synaptic or with sudo apt-get remove oss-linux. Optionally you can also remove gstreamer0.10-plugins-bad and ppa-purge now.

---

### Post by ravi_buz on 2010-09-07
well thanks, but i thried and that dint work.
and i solved it by simply selecting complete removal option of OSS in synaptic and now it works good.

---


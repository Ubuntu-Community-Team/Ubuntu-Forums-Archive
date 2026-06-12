---
title: "Setting output destination for Bluetooth headphones"
date: 2016-10-14
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2016-10-14
I'm running Kubuntu 14.04 and I have a pair of Bluetooth headphones.  I've succeeded in pairing the phones to the computer --both the phones and System Settings confirm that.  How do I actually switch my sound output from the computer speakers to the headphones?

---

### Post by jeremy31 on 2016-10-15
Go into Sound Settings to change the output device to headphones

---

### Post by pwabrahams on 2016-10-15
I can't find anything with the literal name "Sound Settings" within System Settings".  Under "Audio Playback Device Preference for the Music Category", the headphones appear but they are greyed out.  Under "Audio Setup" they don't appear at all.  Yet under "Bluetooth" they are shown as paired.

---

### Post by pwabrahams on 2016-10-16
I found this on AskUbuntu and it worked for me:



To enable Bluetooth audio device discovery in Pulse Audio we need to make sure we had loaded the bluetooth packages for pulseaudio (pulseaudio-module-bluetooth Install pulseaudio-module-bluetooth should be installed by default).

The module-bluetooth-discover then is responsible to add a bluetooth audio device as sink (or source in HSP/Telephony mode) to the known audio devices.

To load this module we can issue

pactl load-module module-bluetooth-discover

To always load this module on startup of the pulseaudio sound server we add the following lines to our /etc/pulse/default.pa (or to our custom user-based ~/.pulse/default.pa, or ~/.config/pulse/default.pa resp., if this file exists):

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

---


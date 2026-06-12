---
title: "Need Help to install Alsa"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-05-05
Can't get Alsa to work
Just installed Ubuntu 9.04 for the third time. For some reason Alsa will not install and as a result I can only get sound using OSS. Checked synaptic and it shows Alsa installed. Ran dpkg-reconfigure in terminal and it says Alsa not installed.
Can anyone help me to install alsa. Even though I can get most applications running with OSS Myth TV needs Alsa.
Thanks Norm

---

### Post by durand on 2009-05-05
MythTV does apparently support pulseaudio, the sound system that ubuntu uses. This is on top of alsa so alsa is also there by default. MythTV should really work automatically. You could try changing the sound options in System > Preferences > Sound.

---

### Post by EV500B on 2009-05-05
Open a terminal;
Desinstall alsa by typing: [B]sudo apt-get remove alsa
[/B]then reinstall it: [B]sudo apt-get install alsa
[/B]
Generally(On some systems) alsa needs to be configured using the **alsaconf** program.
In a terminal type: [B]alsaconf
[/B]
and when you've finish, open your sound mixer and adjust the pcm, master levels, etc...
If the sound doesn't come, type **alsamixer **and adjust it.

---


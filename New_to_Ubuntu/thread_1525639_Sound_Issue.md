---
title: "Sound Issue"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by the2crow on 2010-07-07
I just installed Ubuntu 10.04 on my new laptop, a Gateway nv7915u, but the sound doesn't work. I'm using the 64-bit version, which I hear can have some problems. I'm dual-booting with windows 7, and the sound on it works fine. Anyone know what could be wrong? Help would be greatly appreciated.

---

### Post by Yarui on 2010-07-07
Do you mean there is no sound at all?  You should check to be sure alsa is installed.  If you want to make sure all your channels are unmuted open the terminal and enter the command
```
alsamixer
```
This will open up a tool that allows you to adjust all of your audio channels.  Make sure all the speaker channels are unmuted and have the volume up.  Mute and unmute with the M key.  If the sound starts working and you have constant background noise mute the mic channels.

---

### Post by the2crow on 2010-07-07
Yes, there seems to be no sound at all.
alsa is installed, and the audio channels are all unmuted and at full volume.
Do you have any other suggestions?

---

### Post by plurga on 2010-07-07
hi 
run 
**aplay -l**
If you get a list of your soundcard installed in your system. Your sound just might be mute 
see alsamixer to make the changes that  yauri says.

---

### Post by Yarui on 2010-07-07
> **the2crow said:**
> Yes, there seems to be no sound at all.
alsa is installed, and the audio channels are all unmuted and at full volume.
Do you have any other suggestions?
Unfortunately, this is pretty much the extent of my knowledge on sound.  ALSA has always worked for me with no issues.

---

### Post by the2crow on 2010-07-07
Alright, I ran aplay -l, and the terminal returned
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have no idea what any of that means though, nor why I was running aplay -l. Could you explain a little better?
Sorry, I'm very much a newb.

---

### Post by plurga on 2010-07-07
That means that you have this sound card driver &#8220;ALC272&#8221;

ok, we have to paths:  upgrade the drive or update ALSA. 
To chek out what kinda ALSA version you have 
**Cat  /proc/asound/version**
I know the last version is 1.0.23

---

### Post by lidex on 2010-07-07
And a little more...Can you post the output of these terminal commands for me please:
```
uname -a
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by the2crow on 2010-07-07
Alright... here is the output for each of those commands.
```
Advanced Linux Sound Architecture Driver Version 1.0.21.

``````
Linux davis-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

``````
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

``````
head: l: invalid number of lines

```

---

### Post by the2crow on 2010-07-07
Well, I'm attempting to upgrade alsa to 1.0.23, via these instructions: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Hopefully it will help.

---

### Post by the2crow on 2010-07-07
So, I followed the instructions to upgrade to 1.0.23. I thought everything went well, but upon finishing, when I restarted my computer the speakers began emitting a terrible, loud screeching sound. Is this perhaps because I had turned all of the channel volume setttings up in alsamixer? More importantly, how do I stop it? When it first did it, I turned the computer off. When I tried booting Ubuntu again, it made the noise again, and it was unbearable, so I turned it off before it could boot. Will I have to just suffer through it until I can open alsamixer and change the settings (if that's the problem)?

---

### Post by lidex on 2010-07-07
Try booting into recovery mode. Get to a root terminal shell and mute alsamixer from there. Simply enter;
```
alsamixer
``` at the command line.

---

### Post by the2crow on 2010-07-07
Thanks for the help, but that didn't fix it. It was still making the noise when I went into recovery mode, and typing "alsamixer" into the root terminal resulted in a series of incomprehensible error messages.
Any further suggestions?

EDIT: I noticed that on the boot screen, there were two Ubuntu OS's. "Ubuntu, with Linux 2.6.32-23-generic (and it's recovery mode), AND Ubuntu with Linux, 2.6.32-21 generic (and it's recovery mode)". I booted the "21" one instead this time, and the noise is gone. But so are some updates, and the 1.0.23 version of alsa. My original problem of "no sound" remains.

---

### Post by lidex on 2010-07-07
At this point I would suggest uninstalling 2.6.32-23-generic kernel and header. Now this:
```
sudo apt-get update
sudo apt-get upgrade
```
Reboot into -23 and follow the alsa-upgrade link in my sig to update alsa. Follow the instructions exactly and reboot using the command given when it says to. Do not try to configure anything - especially alsamixer - until after rebooting.

---

### Post by the2crow on 2010-07-08
Alright, but how do I uninstall 2.6.32-23?

EDIT: Nevermind, I figured it out.

---

### Post by the2crow on 2010-07-08
Success! Thank you very much, everything is working now.

---

### Post by lidex on 2010-07-08
Excellent. You do good work!

---


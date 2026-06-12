---
title: "ALSA on 10.04? Any ideas?"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Keir Azuma on 2010-07-28
Hello, I'm planning on getting on a new headset. However I noticed that I have less functionality with PulseAudio than I did ALSA when it comes to output audio. Yeah pulse works, but it doesn't let you do complex setups like ALSA did. For example I used to run music through my stereo system from the rear 3.5mm stereo jack while talking to friends on skype with the incoming audio from skype going to the headset. Now with Pulseaudio I have to chose to run the output from the headset or the stereo, no fancy setup choices anymore like I use to be able to do. So I've decided I want to try to remove PulseAudio and return ALSA to its rightful place on my ubuntu installation or find another debian-based distro still running ALSA. 


tl;dr - How can I get ALSA back on Ubuntu? Are there other Debian distros still using ALSA? If so which ones?

Any input is appreciated.

---

### Post by chopinhauer on 2010-07-28
> **Keir Azuma said:**
> 
tl;dr - How can I get ALSA back on Ubuntu? Are there other Debian distros still using ALSA? If so which ones?


PulseAudio doesn't replace ALSA, it is just a frontend for ALSA (and other sound systems on different platforms), if you don't want to run the PulseAudio server deactivate it in
```
gnome-session-properties
```control should automatically return to ALSA.

You might though want to configure an ALSA plugin such as **dmix** to replace the mixing capabilities of PulseAudio.

---

### Post by ranch hand on 2010-07-28
I would install gnome-alsamixer which gives you all the controls, in a gui, that alsa gives you in terminal.

I think you may like it.

---

### Post by Keir Azuma on 2010-07-28
> **chopinhauer said:**
> You might though want to configure an ALSA plugin such as **dmix** to replace the mixing capabilities of PulseAudio. How would I go about doing configuring it?

> **ranch hand said:**
> I would install gnome-alsamixer which gives you all the controls, in a gui, that alsa gives you in terminal.

I think you may like it. Will that give me the same functionality as the old sound preferences gave me?
--> [http://idyllictux.files.wordpress.com/2008/10/screenshot-sound-preferences.png](http://idyllictux.files.wordpress.com/2008/10/screenshot-sound-preferences.png)

---

### Post by chopinhauer on 2010-07-28
> **Keir Azuma said:**
> 
How would I go about doing configuring it?


After checking it is configured by default. However even if deactivated at login Pulse Audio spawns automatically whenever an application requests it, unless you also add:
```

autospawn = false

```
in your ~/.pulse/client.conf file.

I tried to reproduce your configuration with the tools of Ubuntu 10.04. With the following results:
* If Pulse Audio is activated all other ALSA devices are still available (as shown by 'aplay -L'), however for some unknown reason Skype doesn't allow you to select them. If you use a Bluetooth headset, however, you should be able to choose between 2 PulseAudio devices.
* If Pulse Audio is deactivated Skype let you choose among all ALSA devices (real or virtual), however I don't think there is an application that allows you to select the audio device according to usage (Multimedia vs. Voice).

---

### Post by ranch hand on 2010-07-29
Actually it should do better than that in many ways.

---

### Post by Keir Azuma on 2010-07-31
> **chopinhauer said:**
> After checking it is configured by default. However even if deactivated at login Pulse Audio spawns automatically whenever an application requests it, unless you also add:
```

autospawn = false

```in your ~/.pulse/client.conf file.

I tried to reproduce your configuration with the tools of Ubuntu 10.04. With the following results:
* If Pulse Audio is activated all other ALSA devices are still available (as shown by 'aplay -L'), however for some unknown reason Skype doesn't allow you to select them. If you use a Bluetooth headset, however, you should be able to choose between 2 PulseAudio devices.
* If Pulse Audio is deactivated Skype let you choose among all ALSA devices (real or virtual), however I don't think there is an application that allows you to select the audio device according to usage (Multimedia vs. Voice). There is no client.conf file in ~/.pulse, should I create a file named that and add that line in?

---

### Post by Keir Azuma on 2010-07-31
Also would this tutorial help me at all? [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

---

### Post by chopinhauer on 2010-08-01
> **Keir Azuma said:**
> Also would this tutorial help me at all? [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

Yes, you can use this to disable PulseAudio. Or create the ~/.pulse/client.conf file.

---


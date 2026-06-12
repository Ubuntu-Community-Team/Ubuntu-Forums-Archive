---
title: "Music not working on Kubuntu"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Zopiac on 2009-07-12
I have installed kubuntu-restricted-extras and updated, but I cannot hear music playing. I can hear the login noise, but not music. I have tried playing it with Amarok, Exaile, and Rhythmbox, but all to no avail. Does anyone know how to fix?

Thx in advance!

---

### Post by Zopiac on 2009-07-12
Sound is now working on Amarok, but in the other music players and games it does not. Can anyone help me?

---

### Post by izizzle on 2009-07-12
What's the order of the listings in System Settings > Multimedia?

---

### Post by Zopiac on 2009-07-12
> **izizzle said:**
> What's the order of the listings in System Settings > Multimedia?

HDA ATI SB (ALC1200 Analog)
PulseAudio

---

### Post by nynoah on 2009-07-12
This is a problem dealing with the priorities of what driver amarock is using.  In Kubuntu go to systems settings - multimedia - then move up and down what diver is default.  mess with that and let me know if that works.  I had the same problem till I reconfigured what Amarock used as default.  I assume you have Ubuntu also.  The Gnome based programs are using the settings files from Ubuntu.

---

### Post by Zopiac on 2009-07-12
> **nynoah said:**
> This is a problem dealing with the priorities of what driver amarock is using.  In Kubuntu go to systems settings - multimedia - then move up and down what diver is default.  mess with that and let me know if that works.  I had the same problem till I reconfigured what Amarock used as default.  I assume you have Ubuntu also.  The Gnome based programs are using the settings files from Ubuntu.

I have tried both, and only the first I listed worked, but only for Amarok and system sounds. I just installed PulseAudio (as I found that it wasn't installed) and now I am getting absolutely no sound at all :mad:

Edit: sudo apt-get purge pulseaudio and it is back to how it was...

---

### Post by Ekeluo on 2009-07-13
I have but gnome and kde 4.3 rc2 and all of them play together well. I think the trick is pulse audio. My config is currently [checks config...] pulse audio for everything (video, communications, etc) and the xine backend. I have totem, vlc, audacious, amarok, moovida and all work together.

Check what your kde multimedia configuration is.

---

### Post by Zopiac on 2009-07-13
> **Ekeluo said:**
> Check what your kde multimedia configuration is.

...I already have, and posted it...

---

### Post by Ekeluo on 2009-07-14
> **Zopiac said:**
> ...I already have, and posted it...

Oops, didn't realise that..):P

In mine, I set pulse audio as the preferred for all the categories at the top. I have both environments (kde & gnome) installed though, so pulseaudio always starts at boot. Need it to do the same for you.

---

### Post by Zopiac on 2009-07-14
> **nynoah said:**
> This is a problem dealing with the priorities of what driver amarock is using.  In Kubuntu go to systems settings - multimedia - then move up and down what diver is default.  mess with that and let me know if that works.  I had the same problem till I reconfigured what Amarock used as default.  I assume you have Ubuntu also.  The Gnome based programs are using the settings files from Ubuntu.

I already tried that. I also already said it didn't work. :neutral:

---

### Post by Ekeluo on 2009-07-14
Is pulseaudio (the process) installed and running? Should have it start at boot up. padevchooser will help in configuring pulseaudio after installing. Didn't need it though.

---

### Post by Zopiac on 2009-07-14
> **Ekeluo said:**
> Is pulseaudio (the process) installed and running? Should have it start at boot up. padevchooser will help in configuring pulseaudio after installing. Didn't need it though.

It was installed, and when I rebooted the computer (I'm not sure whether pulse started up or not) I got no sound at all. I got an error message saying something like, "HDA...not working, falling back to Pulse Audio."

What is padevchooser? And how do I get pulse audio to start at boot?

---

### Post by Ekeluo on 2009-07-17
The message (that ends with ...falling back to pulse audio) shows that pulseaudio isn't at the top of the audio device preference list. Try moving it to the top.

To get it to start at boot, (recommend you first do the above and restart, then check system activity to see if it's running already) you can add it to the kde autostart list (system settings>advanced>autostart). Didn't do this on mine though, so it's not there.

If you still encounter problems (along with pulseaudio is configured in PerUser mode [or similar] message), then you need to add yourself to the  pulseaudio group. Not sure how to do this in kde 4 yet.

---


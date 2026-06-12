---
title: "gtk-recordmydesktop sound (ALSA)"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-20
I want to know how to record sound with only ALSA present. I don't have pulseaudio, and I know you can use pulse audio device selector to record audio using pulse, but what about just plain ALSA?

I'm talking about audio that my machine is currently outputting, not inputting.

---

### Post by NCLI on 2010-01-20
Does [this]("http://recordmydesktop.sourceforge.net/rug/p1_3c.php") help?

---

### Post by Psumi on 2010-01-20
I didn't need to do that actually. I went into alsamixer in terminal, unmuted capture, and set the capture type to mix, then it all worked.

---

### Post by Askar450 on 2010-01-21
How did you get the output sound from the PC? I don't need the mic to work I just want the sound from the videos I'm recording.

---

### Post by Psumi on 2010-01-21
> **Askar450 said:**
> How did you get the output sound from the PC? I don't need the mic to work I just want the sound from the videos I'm recording.

If you have a default ubuntu install, you'll need to use the pulse audio device selector. Then, in the advanced dialog in the sound tab, instead of DEFAULT, type in pulse. when you record, gtk-recordmydesktop will appear in the application/device selector and make sure it's checked so that pulseaudio knows that it should send sound to that program.

---

### Post by Askar450 on 2010-01-21
So I need pulseaudio? cause I don't use it.

---

### Post by Psumi on 2010-01-21
> **Askar450 said:**
> So I need pulseaudio? cause I don't use it.

Then you don't need to change anything in gtk-recordmydesktop.

Install alsa-utils if you haven't already: **sudo apt-get install alsa-utils**

and make sure you really don't have pulseaudio: **sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio**

as removing pulseaudio doesn't remove the gstreamer pulseaudio. Also make sure that gstreamer-properties is set to autodetect for sound output.

Once you do that, go into alsamixer in terminal: **alsamixer**

then hit the tab button on your keyboard to move over to capture. There should be a list of capture devices and a volume control for capture. Put the volume for the capture at a suitable level, then select your capture device by pressing space on the capture device you wish to use. But this is based on my IBM T41. Your computer may be different. Mix is the device that your sound outputs on, so you'll want to capture it.

---

### Post by Askar450 on 2010-01-21
I can tell you which audio card I have? I'm desperate to get this working lol.

---

### Post by Psumi on 2010-01-21
> **Askar450 said:**
> I can tell you which audio card I have? I'm desperate to get this working lol.

The only experience I have is either with pulse or what I just mentioned. You can state your hardware and hope someone comes by to help, start a new topic, or just wait.

---


---
title: "Totem only plays sound with other things don't"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Hmmster on 2011-01-31
Okay, let me explain this.
All in-OS music/video players, like VLC, Rythmbox, Totem, etc. etc. only plays sound when non-OS things do sound, like a youtube video. Let me show some examples.

Starting Totem first, then a YouTube video = Only totem giving sound
Starting a Youtube video first, then Totem = Only Youtube giving sound
Opening two youtube videos = Both do south
Do Totem twice = Both do sound

---

### Post by Hmmster on 2011-01-31
Bump

---

### Post by Hmmster on 2011-02-01
Bump

---

### Post by Hmmster on 2011-02-01
Bump

---

### Post by Hmmster on 2011-02-01
BUmp

---

### Post by Hmmster on 2011-02-02
Aaaaah, buump :(

---

### Post by Sylos on 2011-02-02
Could you give some details as to what OS version you are on, Your soundcard and any relevant sound settings/drivers.

Cheers

---

### Post by sydbat on 2011-02-02
What are you using for your sound server? Alsa? Did you remove Pulseaudio?

If you removed Pulse, the problem could be that. Alsa is what I use for overall sound, but I still have Pulse installed and run everything through it, so I can play multiple sound sources. Alsa, by itself, can only play one sound source at a time.

---

### Post by Hmmster on 2011-02-02
I've tried with all sound servers i could chose from, and it was the same thing on everything.
Right now It's on ALSA, it was on "Automatic" by default.
And yes, i have pulseaudio installed.

My sound chip is build into my motherboard, ASUS P7P55D
And i'm running Ubuntu 10.04

---

### Post by sydbat on 2011-02-02
Post #2 in [this thread]("http://ubuntuforums.org/showthread.php?t=1469881") might help...

---

### Post by Hmmster on 2011-02-02
I updated ALSA to  1.0.23 a couple of days ago, that's when I noticed this problem, but I'm not sure that it's not been there all along.
Also, the command "alsamixer" does nothing.

---

### Post by sydbat on 2011-02-02
> **Hmmster said:**
> I updated ALSA to  1.0.23 a couple of days ago, that's when I noticed this problem, but I'm not sure that it's not been there all along.
Also, the command "alsamixer" does nothing.I believe you have to install alsamixer. It is in Synaptic. Also install (if it is not already there) gstreamer-properties. This allows you to configure what gstreamer uses for sound.

Also, as an aside, you should update your profile to show 10.04 instead of 9.10.

---

### Post by Hmmster on 2011-02-02
Synaptic says that I had gnome-alsamixer installed.

Oh wait, i just remembered, i have it in the menu =p 
The F-keys do nothing here though, i unmuted everything, which I've done before, but it didn't help.
Aah! Somewhere in messing with the options of stuff I made my mic not work anymore D:

---

### Post by Hmmster on 2011-02-06
*sigh*
Bump

---

### Post by Hmmster on 2011-02-12
Come on guys, help me :(

---

### Post by Hmmster on 2011-02-15
Guys, this is so incredibly annoying, come on...

---

### Post by sydbat on 2011-02-15
> **Hmmster said:**
> Guys, this is so incredibly annoying, come on...Go to Applications > Accessories > Terminal and type```
alsamixer
```This will bring up the fully interactive version of alsamixer inside the terminal. Make sure everything is unmuted and the volume is turned up all the way on those inputs that allow it.

Hit "Esc".

Now type in```
gstreamer-properties
```This will open a window that allows you to choose which device to use for gstreamer devices (there are many) and to test if they work.

---


---
title: "Newb who Needs Audio"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Foreseer on 2009-02-27
Hello,

I use my default audio card supplied with my a8r32-mvp delux motherboard.
My headset currently being a Logitech USB Headset w/ mic.

How do I get my audio to function >.> I just got Ubuntu running a few days ago..

---

### Post by Foreseer on 2009-02-28
I just went through the following Guide:
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I'm unsure if it helped or not... I'm using a USB headset only enable to get sound from Rhythembox when I select:

System>Preferences>Sound
Logitech Logitech USB headset USB Audio
Under all the Sound Events / Music & Movies.

My Headset / Keyboard Volume Control. Unsure which lever they control either.
Edited: Apparently when I control my headset/keyboard Vol. Ctrl it changes the line values for my Realtek ALC882 inside the Applications>Sound&Video>Gnome Alsa Mixer

---

### Post by Foreseer on 2009-02-28
After playing with it for a while it my controls:

PulseAudio Preferences
Simultaneous Output: (x) Add virtual output device for simultaneous output on all local sound cards.

System>Preferences>Sounds
Sound Events:
Playback: PulseAudio Sound Server
Music and Movies:
Playback: PulseAudio Sound Server
Audio Conferencing
Playback: PulseAudio Sound Server
Capture: PulseAudio Sound Server
Default Mixer Tracks
Device: Playback: Simultaneous output to ALSA PCM on front:0 (ALC882 Analog) via DMA, ALSA PCM on front:1(USB AUdio) via DMA (Pulse Audio Mixer)

With this setting it seems to control a simultaneous volume output to my Speaker Jacks / USB Headset.

Then I max my Headset Volume Control for Headset in Gnome Alsa Mixer...
Temporarily Mute my Realtek ALC882 since I'm not using it...
Making the volume control lever on desktop all but useless, but allowing my keyboard and headset control usable...

There is probably a better way, proper way I should do this... But I don't know it and I guess this works. If someone has suggestions on how I can control my On-board Audio & Headset properly please let me know >.>

Now I have to figure out how to get my Microphone working >.<

---


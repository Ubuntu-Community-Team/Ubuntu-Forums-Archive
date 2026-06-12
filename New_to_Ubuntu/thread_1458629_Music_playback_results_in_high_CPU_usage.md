---
title: "Music playback results in high CPU usage"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by krijg87 on 2010-04-20
I'm running XUbuntu 9.10 on my laptop (Compaq Presario V4000). I installed it 3 days ago from the live CD, as a lighter alternative for XP since the laptop is low on RAM (512 MB) and not too quick.

The problem is, whenever I play music files (MP3), the program uses between 40-60% CPU, sometimes spiking to 100%. This happened to me when using Exail, Amarok and VLC. I currently only have VLC still installed and even when I pause or stop playback, the CPU usage still sits between 40-60% CPU usage as long as the program is not closed.

Is this because my laptop CPU is just that old, or is Linux music playback CPU intensive or is there something wrong with my XUbuntu installation?

---

### Post by sydbat on 2010-04-20
> **krijg87 said:**
> I'm running XUbuntu 9.10 on my laptop (Compaq Presario V4000). I installed it 3 days ago from the live CD, as a lighter alternative for XP since the laptop is low on RAM (512 MB) and not too quick.

The problem is, whenever I play music files (MP3), the program uses between 40-60% CPU, sometimes spiking to 100%. This happened to me when using Exail, Amarok and VLC. I currently only have VLC still installed and even when I pause or stop playback, the CPU usage still sits between 40-60% CPU usage as long as the program is not closed.

Is this because my laptop CPU is just that old, or is Linux music playback CPU intensive or is there something wrong with my XUbuntu installation?It could be gstreamer. I noticed a high CPU usage with it and switched to another player that uses a less resource intensive backend (mplayer).

---

### Post by cgroza on 2010-04-20
Try rhythmbox... you never know.

---

### Post by jkxx on 2010-04-20
Follow the advice above and see if it helps.

To answer your original question, no, mp3 playback on linux isn't that wasteful or bad on your CPU. Even if your CPU is old, it should not be taking more than 10% during playback.

---

### Post by krijg87 on 2010-04-20
> **sydbat said:**
> It could be gstreamer. I noticed a high CPU usage with it and switched to another player that uses a less resource intensive backend (mplayer).

MPlayer looks better, it sits around 10% CPU usage. I get an error popup for each song it plays though, saying:

> AO: [pulse] Init failed: Internal errorBut it plays the songs fine. 

I'm now trying the playlist menu, is there a way to put all files in a directory+subdirectories in a playlist rather than only the music files in one directory? (I'm used to foobar playlist management)

Thanks for the replies.

edit: I'm viewing the preferences menu atm, and the audio driver is set to pulse. Should I try alsa instead to get rid of the error popup? I need to press a "configure driver" button so I'm not sure what it'll do with my sound, I don't want to mess anything up.

---

### Post by sydbat on 2010-04-20
> **krijg87 said:**
> MPlayer looks better, it sits around 10% CPU usage. I get an error popup for each song it plays though, saying:

But it plays the songs fine. 

I'm now trying the playlist menu, is there a way to put all files in a directory+subdirectories in a playlist rather than only the music files in one directory? (I'm used to foobar playlist management)

Thanks for the replies.

edit: I'm viewing the preferences menu atm, and the audio driver is set to pulse. Should I try alsa instead to get rid of the error popup? I need to press a "configure driver" button so I'm not sure what it'll do with my sound, I don't want to mess anything up.You can set your sound driver to whatever you want. It shouldn't mess things up and ALSA might work better for you.

As for mplayer, I use it as a backend, meaning I use a media player that accesses mplayer to play music. (I think I confused myself with that :P). The media player I use is called gmusicbrowser and is found in Synaptic. It's basic, but supports things like playlists, etc, depending on what backend you use (which is changed by going into settings).

---

### Post by achase79 on 2010-04-20
Audacious is another good audio player, it is a fork of the old XMMS.

---

### Post by krijg87 on 2010-04-20
> **sydbat said:**
> You can set your sound driver to whatever you want. It shouldn't mess things up and ALSA might work better for you.

As for mplayer, I use it as a backend, meaning I use a media player that accesses mplayer to play music. (I think I confused myself with that :P). The media player I use is called gmusicbrowser and is found in Synaptic. It's basic, but supports things like playlists, etc, depending on what backend you use (which is changed by going into settings).
This is perfect! CPU usage is now only 5% too and I have all the settings I need. Setting the driver to ALSA fixed my error popup as well. Thanks a lot.

---

### Post by Todamont on 2010-12-02
I have a very similar problem. When using Rhythmbox, processor use goes to 100% and the sound skips and Rhythmbox randomly crashes and has to be forced closed. This is on Kharmic Koala... Anyhow, when I "test sound" using gstreamer-properties using ALSA, I reproduce the problem and processor use goes to 100%. Whe I test sound using Pulseaudio, everything is fine, processor use is at about 1%. So it seems that I need to figure out how to tell Rhythmbox to use pulseaudio because it is trying to use ALSA? Does that even make sense? 

I tried some other programs, like Audacius, Amarok, Exaile, gmusicbrowser, JuJak... They were all either terribly, TERRIBLY written peices of software or didn't support ipod connectivity. Why is it so hard to get a simple jukebox music program working properly on my ubuntu box? This is really really ridiculous... I just want to make rhythmbox work properly. Please help?

BTW this is issue is definitely NOT SOLVED as far as I'm concerned. Just telling the user to use a different program is not really a solution...

---

### Post by Alejanddro on 2011-01-31
> **Todamont said:**
> I have a very similar problem. When using Rhythmbox, processor use goes to 100% and the sound skips and Rhythmbox randomly crashes and has to be forced closed. This is on Kharmic Koala... Anyhow, when I "test sound" using gstreamer-properties using ALSA, I reproduce the problem and processor use goes to 100%. Whe I test sound using Pulseaudio, everything is fine, processor use is at about 1%. So it seems that I need to figure out how to tell Rhythmbox to use pulseaudio because it is trying to use ALSA? Does that even make sense? 

I tried some other programs, like Audacius, Amarok, Exaile, gmusicbrowser, JuJak... They were all either terribly, TERRIBLY written peices of software or didn't support ipod connectivity. Why is it so hard to get a simple jukebox music program working properly on my ubuntu box? This is really really ridiculous... I just want to make rhythmbox work properly. Please help?

BTW this is issue is definitely NOT SOLVED as far as I'm concerned. Just telling the user to use a different program is not really a solution...

I agree, I don't think this should be considered "as solved". Having the same problem.

---

### Post by imtifade on 2011-03-23
[FONT=monospace]Fix posted by [/FONT][Azakus]("http://ubuntuforums.org/member.php?u=186049")

run vlc with this
DISPLAY=:0 vlc

---


---
title: "No sound in Rhythmbox"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Milind on 2010-04-16
I'm using Ubuntu Lucid Lynx beta. There is no sound when playing audio files in Rhythmbox. The indicator moves at normal speed.However, Amarok and Movie Player play without problems. I have installed the GStreamer plugins, ffmpeg xine, and Medibuntu repository. Any ideas what I, a noob, can do to solve this.

N.b. In the recent past I have had the opposite problem where Rhythmbox worked but Amarok was silent.Thanks to helpful people on this forum I could solve that. But, later, for unrelated reasons (don't ask. :( ) I had to reinstall Ubuntu. Post reinstall I have the current problem. Never a dull moment with Linux, is there ? :rolleyes:

---

### Post by skymera on 2010-04-16
Are the correct codecs insalled?

I believe Rhythmbox uses GSsteamer whilst Amarok uses something esle.

---

### Post by Milind on 2010-04-16
> **skymera said:**
> Are the correct codecs insalled?

I believe Rhythmbox uses GSsteamer whilst Amarok uses something esle.

I believe so. GStreamer is installed.

---

### Post by skymera on 2010-04-16
Do you have other sounds, from maybvwe video player, or Firefox, or system sounds?

---

### Post by 3rdalbum on 2010-04-16
The folder /usr/share/example-content has an Ogg Vorbis audio file. If this plays in Rhythmbox, then you have a codecs problem.

Another possibility is that Pulseaudio might be sending your Rhythmbox audio to another device or muting just that program.. Try playing a file, then going to Sound Preferences in your volume control applet. Go to the Applications tab and see.

---

### Post by Milind on 2010-04-17
> **skymera said:**
> Do you have other sounds, from maybvwe video player, or Firefox, or system sounds?

Yes, I have other sounds from video player. I'm not sure, but I think I've turned off system sounds.

---

### Post by Milind on 2010-04-17
> **3rdalbum said:**
> The folder /usr/share/example-content has an Ogg Vorbis audio file. If this plays in Rhythmbox, then you have a codecs problem.

Another possibility is that Pulseaudio might be sending your Rhythmbox audio to another device or muting just that program.. Try playing a file, then going to Sound Preferences in your volume control applet. Go to the Applications tab and see.

I can't play that file too. The Applications tab shows Rhythmbox.

---

### Post by 3rdalbum on 2010-04-17
> **Milind said:**
> I can't play that file too. The Applications tab shows Rhythmbox.

Is the volume control there turned up? Is the Mute button on?

And under the Output tab, is the correct device selected?

---

### Post by Milind on 2010-04-17
> **3rdalbum said:**
> Is the volume control there turned up? Is the Mute button on?

And under the Output tab, is the correct device selected?

The volume control is turned up, the Mute button is off, and the correct device is selected. (In fact, I tried them all.) Yet there is no sound.

---

### Post by sch3j on 2010-05-21
I am now also experiencing this problem in Lucid as well.  I have audio from other applications but cannot play mp3 files in Rhythmbox.

Anyone?

---

### Post by amvx86 on 2010-05-28
Okay buddy this is going to sound cheezy but it worked for me. If you open the sound prefs, in ubuntu 10.4 and go to applications. Leave that window open and the window to your audo files. You'll see the window contents change under the "applications" tab. if you line up the windows side by side you can hover your mouse over the music file and use your tab, left / right keys to raise and lower the sound volume. When you finish with that, head into rhythmbox and play a song, and see if the volume is up on that. If it's not crank it up. Enjoy =) 

./x86

---

### Post by gm__ on 2010-05-28
Thanks a lot man!

I went there and it was on mute! :)

---

### Post by amvx86 on 2010-06-03
no problem brethren. =)

---

### Post by balise on 2011-11-18
> **Milind said:**
> I'm using Ubuntu Lucid Lynx beta. There is no sound when playing audio files in Rhythmbox. The indicator moves at normal speed.However, Amarok and Movie Player play without problems. I have installed the GStreamer plugins, ffmpeg xine, and Medibuntu repository. Any ideas what I, a noob, can do to solve this.

N.b. In the recent past I have had the opposite problem where Rhythmbox worked but Amarok was silent.Thanks to helpful people on this forum I could solve that. But, later, for unrelated reasons (don't ask. :( ) I had to reinstall Ubuntu. Post reinstall I have the current problem. Never a dull moment with Linux, is there ? :rolleyes:
This is the way that Ubuntu Linux
is designed.  Audio not to work by default.
I've spent hours screwing around.  Whether or
not pulseaudio is at fault, I hate it.

---

### Post by shaon3343 on 2012-08-30
Works like charm !! thanks a lot buddy !

---

### Post by shaon3343 on 2012-08-30
> **3rdalbum said:**
> The folder /usr/share/example-content has an Ogg Vorbis audio file. If this plays in Rhythmbox, then you have a codecs problem.

Another possibility is that Pulseaudio might be sending your Rhythmbox audio to another device or muting just that program.. Try playing a file, then going to Sound Preferences in your volume control applet. Go to the Applications tab and see.


Works like charm !! thanks a lot buddy ! :guitar:  :guitar:

---


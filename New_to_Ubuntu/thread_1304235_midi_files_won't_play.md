---
title: "midi files won't play"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by henrodon on 2009-10-29
I can't figure out how to play midi files from the web. They don't play within either Fireox or Midori, but I get a download window and when I double-click on the files, I'm given a choice of programs to open the file. But neither Audacious nor GNOME MPlayer does anything. Other audio files play normally.

EeePC 1004 HA running kuki (Januty by any other name would smell as sweet).

New here -- lost.  :(:(:(:(

---

### Post by mcduck on 2009-10-29
Your problem is that MIDI is not an audio file format. (just like Musical notes are not audio, just instruction about how the instruments should be played)

If you have Gstreamer codecs installed, ten any player that sues Gstreamer should be able to play bac MIDI files. Otherwise you need to use Timidity or some software synth to play the files into audio.

---

### Post by henrodon on 2009-10-29
Thanks. I located the Gstreamer-bad-plugins but I can't install them because they conflict with something already installed. I'm referred to something called the synaptic package manager to resolve this. As an experienced user, perhaps you can point me in the right direction for that?

---

### Post by Zoot7 on 2009-10-29
```
sudo apt-get install timidity
```

That should allow you to play midi files, at least in stuff like Audacity and Gnome mplayer.

---

### Post by mcduck on 2009-10-29
You'll find Synaptic in System/Administration/Synaptic Package Manager. Jst do a search for "gstreamer", right-click the packages you want and select "mark for Installation". When done, click the Apply-button and synaptic will start downloading & installing.

---

### Post by henrodon on 2009-10-29
Thanks. I tried to install timidity but it looks like that didn't work. At the end of the install process, here's what I got:

Setting up timidity (2.13.2-20ubuntu3) ...
 * Starting TiMidity++ ALSA midi emulation...                                                       E: core-util.c: Home directory /home/don not ours.
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
                                                                                             [fail]
invoke-rc.d: initscript timidity, action "start" failed.
The timidity sequencer init script failed.
If you rely on a running sequencer, please start it manually

Processing triggers for menu ...

I'll try the advice from McDuck and see if that will let me play the midis.

---

### Post by henrodon on 2009-10-29
Success! Thank you very much.

---

### Post by henrodon on 2009-10-29
Except now I can't stop it! I have to wait until the end of the midi, which sometimes is way longer than I want to hear. When I download a midi it plays in a Movie Player window, so I have control. But when I clicked on a link to a midi at this website
[http://ingeb.org/folkAb__.html](http://ingeb.org/folkAb__.html)
the midi played allright, but it's still playing and there's no player window (it opened in timidity) so I can't stop it -- at least, I can't see how.

---

### Post by Fancycakes on 2009-11-08
If it acts like that, then perhaps you could stop timidity?

```
ps aux | grep -i timidity
```and then either
```
kill -KILL #PID
```or
```
killall timidity
```

I'm not certain how timidity works, but this is usually the catch-all be-all for ending programs.

---

### Post by Browner87 on 2010-06-16
sorry, I know this is an old thread. But if you just run timidity from the command line you can hit ctrl+c to end it. That's what I do.

---

### Post by andrew.46 on 2010-08-21
I have been trying to convince people for a while that vlc can quite easily play midi files if it is built correctly and has access to a sound font. I attach a screenshot to demonstrate this, goom is running as well :).

Andrew

---

### Post by Demetris Tziambazis on 2011-05-21
> **andrew.46 said:**
> I have been trying to convince people for a while that vlc can quite easily play midi files if it is built correctly and has access to a sound font. I attach a screenshot to demonstrate this, goom is running as well :).

Andrew


and how do i do that?

---

### Post by weezyrider on 2011-05-21
Mine open with Movie Player. I use MID for ringtones, so I have a mess of them on the XP drive. Click on it and Movie Player opens in Ubuntu.
Weezy

---

### Post by andrew.46 on 2011-05-28
> **Demetris Tziambazis said:**
> and how do i do that?

You need to get hold of a copy of vlc that has been compiled against linfluidsynth and has access to some soundfonts. As far as I know this is not possible from the Ubuntu Repository or from PPAs. However some fellow has written a guide that shows how to build your own copy:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

that will play midi files, there is a link to some suitable soundfonts. Don't build the git version unless you really want to, there are directions down the bottom for the release version.

---


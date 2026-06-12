---
title: "video disappeared and sound playing up"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by artificialname on 2009-10-15
Help!
i am a newbiw. any ideas how to fix this?

I first loaded Ubuntu about 2 weeks ago. to start, all was fine, and then...

Ubuntu 9.04 on Dell laptop
All video and sound used to work fine
Suddenly, Totem started crashing as soon as i played an mp3, but another mp3 player worked ok (I can't remember what it was called!).
Then Totem started crashing as soon as i loaded a video file.
So I downloaded VLC media player, which works fine for MP3's but closes as soon as i load a video file.

Amarok never played mp3's - actually it looks like it does play them (all jerky), but no sound comes out.

Ive tried heaps of upgrades/downloads from different threads on this forum, including the sticky in "multimedia" which recommended::
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

I have also deleted/installed heaps of things in "synaptic packet manager"


nothing has worked! and i am worried i have mutilated my system with all the packet manager downloads/delete/installs. 

any ideas?

---

### Post by RichardLinx on 2009-10-15
Open a terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```
Enable Medibuntu repositories: ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu))
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
DVD codec:
```
sudo apt-get install libdvdcss2
```
w32 codecs:
```
sudo apt-get install w32codecs
```
I recommend the kaffeine multimedia player for video:
```
sudo apt-get install kaffeine
```

And Banshee for music: (Although if you already have Rhythmbox install I recommend you use that instead)
```
sudo apt-get install banshee
```
Then:
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```

---

### Post by artificialname on 2009-10-17
thanks richard

i just went through and did everything you suggested.

some improvements, some problems still:

when i play an mp3 with rhythmbox or VLC, they work fine
when i play an mp3 with totem, it opens for a split second then crashes straight away (same problem as before - it just closes)

when i play a video with kaffeine or VLC, there is an improvement - i can now hear the sound from the video and can navigate to any point on the video smoothly (it used to be jerky). BUT still no picture/image comes up when i play video in either of these applications.
when i play video with totem, same problem as before - totem crashes a split second after opening.

something i forgot to mention that was happening before and still happens now:
when i am listening to an mp3 in rhythymbox, if i click on the "visualisation" button, rhythmbox crashes (it just closes)


** i dont know if this is significant, but i have never had problems watching video on you tube.

any idea what to do next? i still have no images on screen when i watch video files!

is it time to format/reinstall the operating system?

---

### Post by RichardLinx on 2009-10-20
> is it time to format/reinstall the operating system?
Not yet, though since it's been 3 days since you replied I figure you already have? Did MP3's work in Totem when you first installed? It is strange that they play fine in Rhythmbox and VLC. Maybe reinstalling totem will fix the problem?

Go into Synaptic and mark "totem-gstreamer" for complete removal, along with the dependancies it pulls. (Which it should do automaticaly)

Then just reinstall it from the CLI:
```
sudo apt-get install totem-gstreamer
``` 

> when i play a video with kaffeine or VLC, there is an improvement - i can now hear the sound from the video and can navigate to any point on the video smoothly (it used to be jerky). BUT still no picture/image comes up when i play video in either of these applications.
What kind of graphics card do you have, is it installed?
In a terminal type:
```
glxgears
```
Post part of the output here, though if the gears rotate smoothly then it means video is installed. If they don't then it means there is some sort of video card problem.

Have you tried installing from System --> Administration --> Hardware Drivers ?

---


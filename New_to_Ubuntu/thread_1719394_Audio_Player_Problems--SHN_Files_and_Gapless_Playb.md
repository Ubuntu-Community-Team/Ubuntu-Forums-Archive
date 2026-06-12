---
title: "Audio Player Problems--SHN Files and Gapless Playback"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by pianoporsche on 2011-04-01
I'm completely new to the Ubuntu scene, so there's a very good chance that I'm mucking things up. I need an audio player that can play both FLAC and SHN files as well as support gapless playback. The default audio player works perfectly fine for FLAC and gapless playback, but it doesn't support SHN. By default, SHN files open with the video player. That's fine, but it inserts a huge gap between each song.

I've looked through tons of forum posts here and elsewhere for suggested audio players, and haven't had any luck. I tried mplayer and smplayer, but there's the same problem with the lack of gapless playback for SHN files.

I'm wondering, what's the best option for playing back SHN files without gaps? I've seen some recommend foobar200 through Wine, but I ran into problems installing that as well.

Any and all help would immensely appreciated. Thanks in advance!

---

### Post by lidex on 2011-04-01
Banshee can do that, at least 1.9.5 can.

[http://ubuntu-tweak.com/source/search/?q=banshee](http://ubuntu-tweak.com/source/search/?q=banshee)

---

### Post by cozmicharlie on 2011-04-03
I don't believe Banshee plays shn files.

Deadbeef is good for playing shn files.  Add the deadbeef ppa

```
sudo add-apt-repository ppa:alexey-smirnov/deadbeef
```
```
sudo apt-get update
```
```
sudo apt-get install deadbeef
``` 

(or alternatively, add the ppa then install from synaptic).  Once installed go to edit>preferences>playback and change the replaygain mood to album

I beleive deadbeef uses ffmpeg, but if the shn files do not play then add the shn codec via a terminal.  Just copy and paste the following.

```
wget http://www.etree.org/shnutils/shorten/dist/src/shorten-3.6.1.tar.gz
```
```
tar xvf /shorten/dist/srs/shorten-3.6.1.tar.gz
```
```
./configure
```
```
make
```
```
sudo make-install
```

This adds the shorten folders to your /home directory - once installed delete the shorten-3.6.1 folders that were added.

---

### Post by lidex on 2011-04-03
> I don't believe Banshee plays shn files.
Do you not think I wouldn't confirm it first?

---

### Post by pianoporsche on 2011-04-29
Wow, sorry it took me so long to see these posts. I tried Banshee, and it wouldn't play them. Deadbeef plays the SHN files, but it places a weird sort of gap between the tracks, which kinda ruins song segues and stuff. I think I might try to figure out how to install xmms, but that's proving difficult as well. Cozmicharlie (how do you do?), do you know how to fix that problem with Deadbeef?

---

### Post by lidex on 2011-04-29
I realize now i got banshee to play shn by opening via 'Media > Open Location' so probably not good for what you're trying to do.

---


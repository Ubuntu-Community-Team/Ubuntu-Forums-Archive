---
title: "Rhythmbox fails to recognize Blackberry as mp3 player"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by drew_halverson on 2010-02-08
I have a Blackberry Curve 8330 with an 8GB microSD card that I use as an mp3 player and manage with Rhythmbox. Everything was working well until my old card failed and I replaced it.  Rhythmbox no longer recognizes the device as a music player. I get the following import error in Rhythmbox:

"/media/9262-E1BD" is a directory

I've done some digging and the solution seems to lie in placing a file called .is_music_player in the root of the devices file system with some parameters in the file identifying where the music is stored on the device. Most of what I've found suggests that the info in the file should be something like:

audio_folders=Music/

This doesn't work. I get the same error as I get without the file. The path to my music folder is /media/9262-E1BD/BlackBerry/music. 

I'd like to understand what the .is_music_player file is doing. I suspect I am borking up the path somehow. When I enter the full path to the music on the device I get the same import error and a bunch of missing file errors for the music on the device.

I'm running Ubuntu 9.10 32 bit. 

Thanks in advance for any help.

---

### Post by drew_halverson on 2010-02-08
No takers? Am I posting this in the right forum?

---

### Post by Tahakki on 2010-02-08
Surely it should be:

audio_folders=/BlackBerry/Music

?

---

### Post by drew_halverson on 2010-02-08
That's what I thought, or some variant on the actual path, but it doesn't work. I've tried multiple variants without any success.

---

### Post by usererror on 2010-02-08
On my old curve, the mp3s were saved in /blackberry/music.  and it only would see it if mass storage device was enabled on the blackberry.  did it get turned off somehow when the new card was put in?

---

### Post by Tahakki on 2010-02-08
It may well be some setting on the device itself.

---

### Post by kostkon on 2010-02-08
Actually the filename should be
```
.is_audio_player
```
and just leave it empty, don't put anything in it, for a start.

---

### Post by drew_halverson on 2010-02-08
Thank you, kostkon. That did the trick.

---

### Post by kelvin.illa on 2010-09-19
> **kostkon said:**
> Actually the filename should be
```
.is_audio_player
```
and just leave it empty, don't put anything in it, for a start.

Amazing! That worked!

---

### Post by kelvin.illa on 2010-09-19
For future reference:

To force Rhythmbox to see your mass storage as a music player, create a file (text file) with filename ".is_audio_player" (without the quotes). 

If you want to specify a directory for Rhythmbox to use, follow these instructions: 
Since the file is hidden because it starts with a ".", have your file manager show hidden files/folders. Open the file with your favorite text editor (gedit). Type "audio_folders=[your preferred path]." Mine looks like this: "audio_folders=kelvin/Music"

---


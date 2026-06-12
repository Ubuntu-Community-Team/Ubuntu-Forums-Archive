---
title: "vlc randomly loses audio during movies"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-07-07
I'm using ubuntu 9.04 on a dell inspiron mini 10.

When I'm watching a movie stored on the HD or playing a long playlist in vlc, 10 to 20 minutes in I randomly lose all audio until I restart vlc, and sometimes the entire operating system.

Now, I've concluded that it's not the computer because this does not happen in other media players. I have to use vlc because it can play audio twice as loud as all other players, which is important on a netbook because they're not known for good speakers. I'd use MPlayer, which is decent, but it gives me incredibly low framerate (this is on all of my pcs) if the video window is any larger than about 150x200 pixels.

The audio lose is random, but consistent with any video I play. I think there was only one time when I didn't lose audio and that was during Office Space, when I watched it a second time, lost audio in the first half an hour. So, what could be wrong here?

---

### Post by jbrown96 on 2009-07-07
Need some more info. What version of VLC (Help-->about)? In the preferences dialog, what audio output method is it using (alsa, pulseaudio)? Don't say default because it's one of the others. Try alsa and pulse to see if that fixes it. In System-->Preferences-->Sound what is your audio output? If it's pulseaudio, try switching to alsa and restart. You can use ```
alsamixer
``` in a terminal to turn up the volumes on the channels, which might help. Note: only turn up what you need, the extra channels might add buzzing. You should probably have (the available channels vary depending on your hardware) master, pcm, and front maxed out. Make sure to change VLC to alsa if you change the ubuntu setting.

---

### Post by mattbutsko on 2009-07-08
Sorry I was so slow to reply, Cox malfunctions, whatcha gonna do, eh?

Anyway, it's vlc version 0.9.9a. The audio output was set to default, I tried changing it to every setting to no avail. I was hoping alsa would work but it didn't make a difference.

My audio output choices are:
default
dummy audio output function
alsa output audio
unix oss audio output
file audio output

pulse audio is not an option.

I even tried "vlc --reset-config" thinking I messed with a preference I shouldn't have with the same ending result. Anyone have any suggestions?

---


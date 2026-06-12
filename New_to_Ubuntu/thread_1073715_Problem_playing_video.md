---
title: "Problem playing video"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by omni504 on 2009-02-18
For some reason, everytime i try to play a video on my computer (doesnt matter if its on VLC, or gnome player, or anything) the video player pops up, looks like its about to play, and then the player just closes itself.. no warning no message nothin.. I dwnloaded every update i was told to download and its still the same.. What could the problem be? Never had a problem with video on this computer before (ran slax, xp, and vista on this laptop before... never a problem with video except now).

---

### Post by Rolcol on 2009-02-18
Did you install the codecs?  (I would assume the answer is yes)  What format is the video in?

```
sudo apt-get install ubuntu-restricted-extras
```

If you have already done so, have you tried launching the application from the terminal to see if it gives you some kind of error message as it's exiting?

---

### Post by Bablefish on 2009-02-18
Rolcol is right you can't just start to play any media file in Ubuntu you need codecs. Also I would suggest GStreamer plugins and Medibuntu.

---

### Post by omni504 on 2009-02-18
Alright, so I went and followed the instructions on [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) that thread (installed some java and different codecs, then went to go update everything) and everything went through without a hitch. But the problem is stillthere, and it doesnt matter whether i try to play video on mplayer, or if its vlc, the gnome player, just doesnt matter it'll do the samething; itll open up and start to load up and then the video player closes itself.
I'm running ubuntu 8.10, help would be greatly appreciated, thx.

---

### Post by omni504 on 2009-02-18
Oh, and i don't know if it's relevant but its a  "avi" video file.

---

### Post by omni504 on 2009-02-19
Anybody? This is the only real problem i got on this OS.

---

### Post by cjv8888 on 2009-02-19
Does it happen with 1 or 2 particular avi files or every different avi files?

I had this happen too sometimes with some avi files but if you open the player from nautilus then it will play

---

### Post by omni504 on 2009-02-19
I have 4 video players on here right now (Gnome, Mplayer, movie player, and VLC), and i went and i opened every one of them and tried to playdifferent files on em. Gnome was the one that worked for me and that only after i put "video output" to "x11". But on the rest of the players, not even sound files could be played on em (wav)s. I don't know why it's like that, but hey i really don't mind now that i can watch video on here :)

---

### Post by gackt on 2009-02-19
Try running the vlc or other player trough the terminal. If the program exit then it will leave some comments, like cpu soft exhausted terminating.....post the comment here and we'll see what we can do with your problem (provided with more information)

---


---
title: "A Simple Musician..."
date: 2010-09-30
forum: New to Ubuntu
---

### Post by ahenriquez31 on 2010-09-30
Hey Ubuntu Forums!
I'm pretty new to Ubuntu, but just from this last week of fiddling around I'm already sold on Ubuntu and open source software. I do, however want to do something pretty bad that I used to be able to do in Windows that I can't figure out how to do here. 

I have an external sound card that is recognized by the computer, I see it in the Sound Preferences Input and Output tabs as "CM106 Like Sound device Analog Stereo". I'm actually using it now to listen to music, so I know that thats the right one. Now before, I used to be able to plug my bass or guitar into the Line In slot on this card and listen to myself play whenever. I would be able to play and hear it while listening to music to play along with whatever artist, and I could put on a metronome program to listen to while I recorded. 

Now I can't seem to figure out how I would go about doing all that. I'm running 10.04 Lucid with the Ubuntu Studio upgrade (followed the instructions from [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)). Its on a laptop that only has a headphone and mic jack, which is why I bought the external card that can support much more. Any ideas? 

-crosses fingers-

Thanks. 

:guitar:

---

### Post by sanderd17 on 2010-10-01
Ubuntu doesn't listen to the line in by default. You need an app for that. Audacity can do a "playtrough" while recording but I don't know if it can while doing nothing.

You do have to change the preferences. 

I know VLC can stream from the line in to the line out but vlc always needs a buffer. Maybe you can make the buffer small enough so it sounds life.

---

### Post by alphacrucis2 on 2010-10-01
Maybe this would help:


[http://ubuntuforums.org/showthread.php?t=1324135&page=2]("http://ubuntuforums.org/showthread.php?t=1324135&page=2")

---

### Post by mikechant on 2010-10-01
Possibly
```
pactl load-module module-loopback
```
might help (connects line-in to output)
Plus make sure line-in isn't muted in the audio mixer.

---

### Post by cchhrriiss121212 on 2010-10-01
Gtick is a good metronome. If you want to try some FX, then try rakarrack which is included in studio, it requires that you use the jack sound server as will the more advanced recording programs like Ardour.

---

### Post by ahenriquez31 on 2010-10-01
hrmmm, still having a bit of trouble...maybe a way to just listen to the laptops built in mic jack then? ill just rig my amp up to it lol

---

### Post by transmogrifox on 2010-10-01
alsamixer is a great program to run from the terminal.  It doesn't look pretty, but I don't think I've seen a mixer application more useful and complete as alsamixer.

From there you should be able to identify the different inputs and mix levels from anything so it is audible.

From the sound menu, you should be able to bring up a gnome mixer panel, which I think would be able to adjust enough levels to make your bass audible.  

Don't give up because this is a relatively simple thing to do...just takes some time fiddling around before you learn about how to manage your audio sources in Linux.

take care

---

### Post by ahenriquez31 on 2010-10-05
> **transmogrifox said:**
> alsamixer is a great program to run from the terminal.  It doesn't look pretty, but I don't think I've seen a mixer application more useful and complete as alsamixer.

From there you should be able to identify the different inputs and mix levels from anything so it is audible.

From the sound menu, you should be able to bring up a gnome mixer panel, which I think would be able to adjust enough levels to make your bass audible.  

Don't give up because this is a relatively simple thing to do...just takes some time fiddling around before you learn about how to manage your audio sources in Linux.

take care

NICE! :D
I searched for alsamixer in the ubuntu software center and found something called GNOME ALSA Mixer. Right away I noticed the Line In had mute ticked and record unticked, both of which i didnt want. I just reversed it, turned up the input volume and it works! :D

Ubuntu seems to be a keeper for me now, especially now that I have Starcraft 2 running also (the only Windows game I still play). Thanks for the help! Hopefully I'll learn a little more with time and help someone in the future also. ^_^

---


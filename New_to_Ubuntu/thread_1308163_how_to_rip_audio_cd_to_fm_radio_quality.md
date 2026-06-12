---
title: "how to rip audio cd to fm radio quality"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by gigaferz on 2009-10-31
so ive been working during the night for the last few months....

  i just need to do a simple task.... yeah the one mentioned above...
i do not want to hear this is better quality or better bitrate stuff...

i dont care that much about it.

anywyas, is it me or Ubuntu has no decent gui app to get it done?

  maybe i could figure it out tru the whoole week, im only awake and available during 2 or 3 hours per day ,why not spend that time googling how to rip audio cd in ubuntu...

  Just let me know if you can help me, if not then  thanks for looking....

and if possible if this "wonderful" program could read the name of the song and artist and stuff like that would be great (i know im asking 4  miracles here)

sound juicer didnt work, brasero is not flexible enough  ( i need small file size )

  please...thnx....

---

### Post by yeleek on 2009-11-03
> **gigaferz said:**
> 
anywyas, is it me or Ubuntu has no decent gui app to get it done?


Its you - Look at Rhythymbox.  It can record to the level you want (can create new recording profiles (Edit, Preferences, Music)).  You will need to know 1) exactly what you want 2) specify this in the gstreamer pipeline i.e. know what parts of this you want to change for example

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

Can also get the names of tracks cds etc.

---

### Post by jward3010 on 2009-11-03
I recommend "sound-juicer", a gnome app, very easy to use. But at the same time I agree with yeleek above, its pretty similar to what Rhythmbox does.

```
sudo apt-get install sound-juicer
```
Then look for it in "Sound and Multimedia" menu under "Applications", it might be called "Audio CD Extractor".

---

### Post by Dayofswords on 2009-11-03
audacity is good

---

### Post by whitethorn on 2009-11-03
Give grip a try.  

```
sudo apt-get install grip
```

---

### Post by gigaferz on 2009-11-09
thanx for the reply guys ,hopefully everything will just work, 

  im kinda tired of cli for now, i dont have the time to learn what i want, but i do exactly know what  i need low space , dont-care-quality-that-much mp3 s ,

the thing is I "ubuntized" acouple of guys long time ago, and when they come with the simplest demands and there is no easy way out, they hunt me down to get it done,lol

  ive been trying to throw em back to windows, they still have their old xp , licenses in the back of their pc,  its just hard to deal with people that do not wanna learn how to run a script..... sorry im just still in zombie mode , nor awake nor sleeping.....

---

### Post by jward3010 on 2009-11-09
The good news is none of these are CLI based, they're all GUI based, easy to use programs with a desktop window. The above commands just installs them the fastest way...

---


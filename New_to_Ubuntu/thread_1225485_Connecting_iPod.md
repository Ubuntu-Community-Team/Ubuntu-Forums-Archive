---
title: "Connecting iPod"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by CharlesWelsh on 2009-07-28
I am currently running Ubuntu "Ju7anty Jackalope" 9.0.4. I am trying to find a way to connect and sync my ipod to this computer. If I run iTunes 7 in WINE will my iPod connect and sync? Any help would be greatly appreciated. Thanks in advance -CJ:confused::confused::confused::confused::confused::confused::confused:

---

### Post by SuperSonic4 on 2009-07-28
iTunes simply won't work in Linux.

The level of success depends on the age of your iPod - the older the better.

gtkpod is my favourite although I believe rhythmbox can do it too

---

### Post by CharlesWelsh on 2009-07-28
iPod touch 2g =[ Man... Well, off to try VB :popcorn:

---

### Post by philcamlin on 2009-07-28
i use songbird with ipod support plugin and it works great!

iphone doesnt work for me though

---

### Post by CharlesWelsh on 2009-07-28
I guess I am going to try VB then...:popcorn:

---

### Post by SuperSonic4 on 2009-07-28
It is always worth a try first, perhaps they've advanced their tech.

Rockbox may also be able to help - they dual boot your ipod so to speak

---

### Post by philcamlin on 2009-07-28
> **SuperSonic4 said:**
> It is always worth a try first, perhaps they've advanced their tech.

Rockbox may also be able to help - they dual boot your ipod so to speak

thatsd only ipod nanos and stuff the touch version of that is iphonelinux wich is in extreme beta stages

---

### Post by ahndoruuu on 2009-07-28
Their information is downright false.

If you're gonna use iTunes in Wine, you're gonna wanna use 8.0

I have it installed on mine, it works flawlessly.  Though the install process is a little complicated.  But it'll recognize iPods and everything (not iPhone or iTouch I don't think though) and sync if you apply a patch.

So yes, it is possible to run iTunes in Wine.

---

### Post by philcamlin on 2009-07-28
> **ahndoruuu said:**
> Their information is downright false.

If you're gonna use iTunes in Wine, you're gonna wanna use 8.0

I have it installed on mine, it works flawlessly.  Though the install process is a little complicated.  But it'll recognize iPods and everything (not iPhone or iTouch I don't think though) and sync if you apply a patch.

So yes, it is possible to run iTunes in Wine.


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16848](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16848) 

it still has bugs :) but its better then dualbooting and if it syncs im getting rid of windows and installing karamic :popcorn:

i was told it wouldent work last week but aparently they made it work

---

### Post by ahndoruuu on 2009-07-28
Yeah it's all possible it's just difficult for the Wine developers to implement all this because Apple is bent on locking their stuff down. >.> the jerks.

But I'm sure the day will come when we have a perfectly functioning iTunes in Wine, it just might take a while.  Every small software update Apple releases can completely destroy the program's functionality in Wine, so it's really commendable that the Wine developers have even been able to get it running at all.  

The best-running version of iTunes for Wine is 8.0 though (it has a silver rating while most of the others are bronze), however I'm not sure if iPhones will work with that version.

Also, I would advise against installing Karmic quite yet, especially if you're planning on having the iPhone support in Wine, because Wine isn't very well tested or documented with Karmic quite yet.

---

### Post by vinutux on 2009-07-28
Try native apps like gtkpod, banshee

```
sudo apt-get install banshee
```

---

### Post by elboeufx on 2009-09-01
Hi--

I'm having some trouble connecting my iPod (30 gig, video, four years old) to Jaunty. I've tried gtkpod, Hipo, Banshee, Rhtymbox. I can mount okay (does it automatically), and read (can play tunes off it), and delete (remove files from iPod), but I can't, for the life of me, figure out how to write to the thing. Any help would be greatly appreciated.

Elboeufx

---

### Post by gjoellee on 2009-09-01
iTunes does run in WINE, but it does not run well at all! You may however use:

-Banshee (my favorite)
-Rhythmbox
-Songbird
-gtkPod
-Amarok
...and more!

I think at least one of those media players should work for you. All of those does also support syncing with iPods.

---

### Post by acornbrain on 2009-09-02
A newb myself, 
 
Have not yet tried the full-fledged Wine/Itunes route yet.
 
I got rhthmbox to connect to my wife's (older 80GIG) ipod. However:
 
1. Rhythmbox/Ubuntu will not play stuff she's dowloaded from the itunes store, I must have a plugin missing? (shows up with red circle/minus sign)
 
2. I think some podcasts are carried exclusively by itunes (?) which means I will still have to sync with itunes to get them?
 
I plan on dual booting to keep Windows XP alive *just in case*, but I really don't want to be ever booting in with Windows if I can help it for 90%+ of desktop tasks. I'd love to find a native solution, because if my wife needs to be booting into windows weekly(daily?), then it is kind of defeating the purpose of switching to Ubuntu.
 
please help..any thoughts from users in my situation?

---


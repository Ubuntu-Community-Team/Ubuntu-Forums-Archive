---
title: "No sound in Firefox, sound everywhere else."
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Neon_Knight on 2009-04-10
First, do *not* tell me to search the forums, because I have done so repeatedly, and attempted many of the fixes.  Which is why I've resorted to posting here.

Now, before it was working absolutely fine.  In fact, it's been working absolutely fine for *years*.  I upgraded to 8.10 a few days ago, but after that, it was *still* fine, and still played sound in firefox and youtube just fine.  

And yet, suddenly, for no explicable reason, it's just stopped.  Everything else just works fine.  (I meddled a bit with the sound drivers, set then to ALSA instead of OSS, but even switching them back to OSS hasn't helped).  

One of the supposed fixes is to edit a file called firefoxrc in /etc/firefox.  Well, let me tell you, that file doesn't exist, nor does the directory.   There is a firefox-3.0 folder, in /etc/, but no firefoxrc file in there, so that advice is useless.   Before anybody tells me to find the "real" firefox install directory, well, how on Earth am I supposed to know where it's installed to?  Doing a search for "firefox" comes up with so many folders called "firefox" in so many different places, it would take hours to search them all. I don't understand why install directories can't just be standard between machines, none of my install directories are anywhere near where they're "supposed" to be, but oh well.  

Back on topic, I randomly have no sound in youtube, restoring the sound drivers to default doesn't help, at all, playing it in songbird browser doesn't help either, so I'm completely stumped.

---

### Post by pah99 on 2009-04-10
Next time this happens try the following. Open a terminal and type in pulseaudio. If it says that its already running, open a task manager and kill the pulseaudio, and then go back to the terminal and type it in again to restart it. It might just be dying whenever you try to play something in Firefox.

---

### Post by barnard on 2009-04-12
I have the same problem.............no sound in YouTube in Ubuntu. I've tried everything from re-istalling both Flash from Adobe to Firefox itself. I solved the problem by downloading Opera browser which gives me sound and a very friendly and neat browser with a mail function as well. So.........its Opera for me

---

### Post by hovzio on 2009-04-12
> **pah99 said:**
> Next time this happens try the following. Open a terminal and type in pulseaudio. If it says that its already running, open a task manager and kill the pulseaudio, and then go back to the terminal and type it in again to restart it. It might just be dying whenever you try to play something in Firefox.

My boss was having the same problem.. "all of the sudden". Was not able to figure out the cause.. as "workaround" I also ended up doing similar to what  pah99 said. by typing ```
killall pulseaudio
``` will stop any instances of PA and it should restart it on its own again. Doing this at the beggining of a session did the trick for my boss's pavillion, sound was well in firefox again.

Nevertheless this is an ugly workaround since it needs to be repeated somtimes, especially reboot. Would be nice to know the cause of things..

---

### Post by hesjnet on 2009-04-12
I have also experienced this problem. Is it possible the problem may be with the sound mixing between programs?

I have noticed that my sound problems start when I already have a program using the soundcard(like songbird or totem).

---

### Post by gandaran on 2009-04-12
```
killall pulseaudio
```
instead kill pulseaudio [fix it]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by hovzio on 2009-04-12
> **gandaran said:**
> ```
killall pulseaudio
```
instead kill pulseaudio [fix it]("http://ubuntuforums.org/showthread.php?t=789578")

Thanks, and right you are, fixing the problem is definately better. One question; In the link you mentioned, part C, number 2. So this is telling me to add some sources and then to do an:

```
$ sudo apt-get update && sudo apt-get dist-upgrade
```

I just wanna play it safe, isn't this for..well, a distribution upgrade? I haven't yet seen the command in this context. Or are these like experimental packages or something that dist-upgrade would install. Can someone explain please. Thank you :)

---

### Post by Neon_Knight on 2009-04-13
I've done that, and now the problem seems to have randomly gone, permanently, strangely enough. I also reinstalled flash beforehand.

One of them seems to have randomly worked, so thanks for your help.

---

### Post by Jakey_TheSnake on 2009-04-13
If it worked before, deleting ~/.mozilla and then restarting Firefox should solve it. Note you will lose bookmarks and saved passwords.

---

### Post by DigiTan on 2009-04-13
I had the exact same youtube problem.  I think my first flash plugin was incomplete or something.  One day it wasn't working, I downloaded the flash player from the repository, and it just started working.

---

### Post by thesuperjman on 2009-04-13
> **barnard said:**
> I have the same problem.............no sound in YouTube in Ubuntu. I've tried everything from re-istalling both Flash from Adobe to Firefox itself. I solved the problem by downloading Opera browser which gives me sound and a very friendly and neat browser with a mail function as well. So.........its Opera for me

i have this problem, but with video. it will load but wont play.

---


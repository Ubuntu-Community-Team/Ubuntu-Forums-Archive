---
title: "Problem with Music Players"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by serbforce on 2010-03-30
Hello, i have a slight problem with music players in Ubuntu. I have Audigy SE sound card, and everything works great, but i can only listen music with Banshee, even tho i really really prefer Listen. In Listen and all others song wont even start playing. Does anyone know what can be the problem? Thank you very much in advance.

-serbforce

---

### Post by uRock on 2010-03-30
Do you have ubuntu-restricted-extras installed?

---

### Post by serbforce on 2010-03-30
> **iRock said:**
> Do you have ubuntu-restricted-extras installed?

Yes i do. I also did a lot of searching about this issue, but nobody ever seemed to have this problem. Strange.

Edit: I probably wouldnt need it for this anyway, since most of my music is .ogg.

Edit #2: Heres what happans

[[IMG]http://img707.imageshack.us/img707/7438/screenshotfha.png[/IMG]](http://img707.imageshack.us/i/screenshotfha.png/)

Its not that i cant hear the sound but the player itself wont start playing.

---

### Post by serbforce on 2010-03-30
Excuse me for bumping but nobody responded in 10 hours :(

---

### Post by lidex on 2010-03-30
What version is this? I have 0.6.4 and it's working well. Is this with all audio files or just ogg?

Try this in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge listen && sudo apt-get install listen
```

---

### Post by serbforce on 2010-03-30
I had 0.6.2, i just installed 0.6.5 which seems to be the latest and its still not working.

Edit: Its with all audio files, in all players but Banshee which i hate the most!

---

### Post by lidex on 2010-03-30
> **serbforce said:**
> I had 0.6.2, i just installed 0.6.5 which seems to be the latest and its still not working.

Edit: Its with all audio files, in all players but Banshee which i hate the most!

Yeah, me too.
May be gstreamer. Try this howto:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by egalvan on 2010-03-31
> **serbforce said:**
> Excuse me for bumping but nobody responded in 10 hours :(

Forums Rules ask that poster wait at least 24 hours between "bumps".

---

### Post by serbforce on 2010-04-10
Bump

---

### Post by grobar87 on 2010-04-10
i have simular problem like this,only bunshee works ok :confused:

---

### Post by uRock on 2010-04-10
Personally, I'd toss the sound card. Maybe when Lucid comes out there will be support for it.

---

### Post by serbforce on 2010-04-11
Okay then, i made Exaile work as it should, so ill stick with that for the time being.

---


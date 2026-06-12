---
title: "No sound on Ubuntu"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by BilleeSugger on 2010-04-21
I have  just installed Ubuntu  & I have no sound on videos. Speakers are OK & on. What do I need?

---

### Post by MooPi on 2010-04-21
We will need some system specs and as much info about your system to start.
Open a terminal and type ```
lspci>specs
``````
sudo lshw>hardware
```These two commands will drop text files by the same names (specs/hardware) in your home folder. You can copy and paste the info back here. What version of Ubuntu are you using as well.

---

### Post by Bob Bertrands on 2010-04-21
Maybe a stupid question but did you try a different media player.

also, did you install ubuntu-restricted.

If not or if you can't remember

Enter this in your terminal:

```
gksudo apt-get install ubuntu-restricted-extras 
```

---

### Post by mockingbird on 2010-04-21
Open your mixer and make sure the "PCM" slider is up.

---

### Post by lidex on 2010-04-21
Do you have sound elsewhere - is it just missing when you play video? If yes, go here and work through part 1/5:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---


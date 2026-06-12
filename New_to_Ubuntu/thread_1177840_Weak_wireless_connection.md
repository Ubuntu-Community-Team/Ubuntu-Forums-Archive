---
title: "Weak wireless connection"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by gmc1200 on 2009-06-03
I'm trying to get off of windows right now, so I just installed ubuntu on my netbook (Asus EEE 1000he).  I noticed that the wireless range is significantly weaker than when I had windows 7 on it.  I usually have flawless connectivity from my bedroom, but now i can barely get a connection.  Once I move closer to my router, im able to connect.

Has anyone experienced this?  Any fixes known?

---

### Post by venator260 on 2009-06-03
Sounds like the issue that I and several others were/are having with Atheros wireless cards. 

[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367) is that thread

Typing

```
lshw -C network
```

into a terminal will allow you to see what network hardware that you have. 

I, as well as a few others, have had sucsess by installing the linux-backports-modules-jaunty package which includes updated drivers for some cards. 

```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by gmc1200 on 2009-06-03
You are freaking awesome. Wireless is 100% better.  I really like using ubuntu netbook remix, glad I can still use it!  I was really close to switching back to windows.

---

### Post by venator260 on 2009-06-04
Glad I could help.

---


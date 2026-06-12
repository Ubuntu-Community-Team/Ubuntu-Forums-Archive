---
title: "Cannot find wireless connection"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Icyyrobe on 2008-09-21
Hello all,

I've had Ubuntu for some days now and these past days the internet worked on wireless... but today I can only find:

Wired Connection
Point to point connection...

And of all the FAQ's I've been reading these hours noone could give me an answer...

So If anyone got an idea of what this might be please reply...

PS: This is in "Network settings"-> "Connections".


-Icyyrobe

---

### Post by nixscripter on 2008-09-21
First, check to make sure that the card is detected. You should see it in this command's output: ```
lshw -C network 
```

If it's there, see what it's network status is: ```
ifconfig -a
```

---


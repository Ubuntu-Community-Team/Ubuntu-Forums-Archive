---
title: "Complete uninstall of XBMC?"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by got2av8 on 2009-09-28
Well, the title says it all...

Synaptic doesn't recognize it, *apt-get uninstall* doesn't get rid of it, Google is unhelpful, and the wiki just tells me that page needs to be written.  It's like the cockroach of media players. Any suggestions welcome, 8.04 on a Dell Inspiron if it's relevant.

---

### Post by Zeedok on 2009-09-30
> **got2av8 said:**
> *apt-get uninstall*

Thats not the correct command (although it would seem logical if it was).

Try ```
sudo apt-get remove
``` 
Then if you want to clean up un-needed dependencies ```
sudo apt-get autoremove
```

---

### Post by zbuzz90 on 2010-05-18
Tried that and its still there. The only reason I installed it was to sync with the Xbox360, which I couldn't get it to do. Now I just want it off my computer.

---

### Post by kelvin spratt on 2010-05-18
How did you install xbmc

---

### Post by zbuzz90 on 2010-05-24
I used terminal. The code at the XBMC wiki
This:
sudo apt-get install python-software-properties pkg-config
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update

---

### Post by SRST Technologies on 2010-05-24
sudo apt-get remove xbmc xbmc-standalone

sudo apt-get remove by itself does nothing.

You could also try:

sudo apt-get purge xbmc xbmc-standalone

---

### Post by zbuzz90 on 2010-06-11
:DFinally. The code:   sudo apt-get purge xbmc xbmc-standalone  is what did it. Removed the program completely. Thanks.

---

### Post by eumajevi on 2012-01-24
I am having the same problem with XBMC.
 
Where did you type in the code: sudo apt-get purge xbmc xbmc-standalone ??

---

### Post by eumajevi on 2012-01-24
**Re: Complete uninstall of XBMC?** 
I am having the same problem with XBMC.

Where did you type in the code: sudo apt-get purge xbmc xbmc-standalone ??

---

### Post by Cheesemill on 2012-01-24
Most probably in the terminal :)

---


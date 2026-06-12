---
title: "Widget that wont go away"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-09-21
I had the Now Rocking widget installed on my Kubuntu desktop, and I removed it expecting it not to appear on the desktop when I restart.  But it keeps reappearing, I don't want it anymore how do I remove unwanted widgets?

---

### Post by ~sHyLoCk~ on 2009-09-21
I don't know if this will work but give it a try:

```
kwrite ~/.kde/share/config/plasmarc
``` and then from 


```
[Applet Browser]
used=,notifier,systemtray,digital-clock,tasks,pager,launcher,folderview,clock,nowplaying,plasma_applet_daisy,sm_cpu,activitybar,lockout
```

Remove the one you want. Obviously this list will be different for you.

---

### Post by Dobbie03 on 2009-09-21
Thanks!

---

### Post by ~sHyLoCk~ on 2009-09-21
> **MattDobson said:**
> Thanks!

You're welcome, did it work? :P

---

### Post by Dobbie03 on 2009-09-22
No id didnt :(

---

### Post by ~sHyLoCk~ on 2009-09-22
> **MattDobson said:**
> No id didnt :(

Ok do this:
```
cd /usr/share/kde4/services/
```

and then see if you find the applet and delete it.

Else, do this:

```
sudo updatedb
locate applet_name
```

then go there and delete it. Hope his works! ;)

---

### Post by Dobbie03 on 2009-09-22
Ok will let you know.

---

### Post by Dobbie03 on 2009-09-23
Ok it didn't work.  It was back when I booted up tonight.

---


---
title: "Scrobble Rythmbox plays with Last.fm Client"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by Atreideskid on 2011-02-11
Can anyone help me figure out how to scrobble my Rythmbox to Last.fm with the last.fm client.

I've read this over and over, but can't get it to work.

[http://blog.blackdown.de/2007/05/19/lastfm-for-rhythmbox-new-style/](http://blog.blackdown.de/2007/05/19/lastfm-for-rhythmbox-new-style/)

Just need someone to walk me through it step by step.

---

### Post by sffvba[e0rt on 2011-02-12
Ok... lets start off with asking: What version of Ubuntu are you using?


404

---

### Post by Atreideskid on 2011-02-12
> **not found said:**
> ok... Lets start off with asking: What version of ubuntu are you using?

10.10

---

### Post by sffvba[e0rt on 2011-02-12
According to the link you should now edit the "/etc/apt/sources.list" and add the following two lines the document:

deb [http://blog.blackdown.de/static/debian/rhythmbox/](http://blog.blackdown.de/static/debian/rhythmbox/) maverick main
deb-src [http://blog.blackdown.de/static/debian/rhythmbox/](http://blog.blackdown.de/static/debian/rhythmbox/) maverick main

Any problems thus far?


404

---

### Post by Atreideskid on 2011-02-12
> **not found said:**
> According to the link you should now edit the "/etc/apt/sources.list" and add the following two lines the document:

deb [http://blog.blackdown.de/static/debian/rhythmbox/](http://blog.blackdown.de/static/debian/rhythmbox/) maverick main
deb-src [http://blog.blackdown.de/static/debian/rhythmbox/](http://blog.blackdown.de/static/debian/rhythmbox/) maverick main

Any problems thus far?


404

I added them to my software sources list, does that work?

---

### Post by sffvba[e0rt on 2011-02-13
Now in terminal:

```

aptitude update
aptitude install rhythmbox

```

This is according to the link you sent... I suspect that you might have to remove the version of rhythmbox you are using but lets first see if this works...



404

PS - Sorry for the late reply... working night shift and also sleeping in between :p

---


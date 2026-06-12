---
title: "Internet connection problem"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by Max_Scott on 2014-02-07
I'm new here but previously used vers 10.04.1 (in 2010) successfully. Now trying to run Ubuntu 10.04.1 from a CD on different computer (on home network). Get error "Firefox can't find the server at start.ubuntu.com/..." No problems with typing errors network connection or firewalls, at least Firefox works in Windows okay. Have tried other URLs (mozilla.com, e.g.) with same problem

---

### Post by Dennis N on 2014-02-07
The server is probably shut down for 10.04 as that version is no longer supported for desktop systems. Suggest you try latest 12.04 release instead.

Just released:

[http://cdimage.ubuntu.com/releases/12.04.4/release/](http://cdimage.ubuntu.com/releases/12.04.4/release/)

---

### Post by Max_Scott on 2014-02-08
I just tried 12.04 (not latest, but...) and I have the same problem...can't find server.

---

### Post by Iowan on 2014-02-08
This looks like a networking problem - I'll move it there - at least for awhile...
Start with a terminal (Ctrl-Alt-T).
Post results of:
```
ifconfig -a
```

---

### Post by Max_Scott on 2014-02-08
I did not have wireless connection set up...so my fault! Working fine now. Thanks for the quick responses.

---

### Post by Iowan on 2014-02-08
AMAZING what being in the right forum can do. ;)
Are we [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---


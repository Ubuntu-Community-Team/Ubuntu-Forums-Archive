---
title: "Network manager problems"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Viva on 2009-05-08
I just updated to jaunty. Everything is perfect except for the network manager. I'm unable to connect to the Internet sometimes. It says "Unable to connect" and when I restart, it works. I have a cable connection which requires authentication.

---

### Post by Viva on 2009-05-08
Bump:(

---

### Post by Viva on 2009-05-08
I can connect after multiple tries. Is there an alternative to network manager?

---

### Post by Viva on 2009-05-08
Update: This is the message I'm getting in the system log everytime a connection fails.

```
Remote message: Too many simultaneous sessions for user:
```

---

### Post by durand on 2009-05-08
There is a good alternative called wicd: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I've never used it but I've heard good things about it.

From your error, it seems that you are connecting to your router too many times?

---

### Post by djbushido on 2009-05-08
Make sure that you don't have other users connected to the router, or other computers connected to the router. This may be causing the problem as well.
Also, it currently appears that NetworkManager is not causing the problem, and as such it would be a very good idea to leave it intact, as many other applications use it.

---

### Post by wabbalee on 2009-05-08
WICD is good, used it all the time under hardy but now I have no need for it as Jaunty does a good job at it (including wireless)

bumping is rude (imo) and not allowed within 24hrs after posting, bare in mind nobody gets paid to answer your questions and we are all here out of free will..

---

### Post by djbushido on 2009-05-08
Agreed. Please only bump every 24 hours, and if you absolutely NEED help right this very instant, use irc - "sudo apt-get install xchat".

---

### Post by RedSingularity on 2009-05-08
Yeah wicd is a good manager.  I have it on my laptop.

---


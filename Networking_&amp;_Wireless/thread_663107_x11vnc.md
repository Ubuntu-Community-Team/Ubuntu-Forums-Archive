---
title: "x11vnc"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by magikx21 on 2008-01-09
I got this working and connected to my desktop from my laptop with no problems. However when I exit my session on the client the server closes x11vnc and I am unable to start another session. Is there a way I can fix this so I disconnect and reconnect throughout the day while I'm away?

---

### Post by krunge on 2008-01-09
> **magikx21 said:**
> However when I exit my session on the client the server closes x11vnc and I am unable to start another session. Is there a way I can fix this so I disconnect and reconnect throughout the day while I'm away?

Yes, take a look at this x11vnc option:
```
-forever
```
Also, the "-shared" option allows simultaneous connections.

---

### Post by magikx21 on 2008-01-10
Thanks, now I don't have to worry about closing the session.

---

### Post by magikx21 on 2008-01-11
This has actually raised another question. Can I get x11vnc to automatically start with this effect rather than type x11vnc -R forever everytime I open it?

---

### Post by krunge on 2008-01-11
> **magikx21 said:**
> This has actually raised another question. Can I get x11vnc to automatically start with this effect rather than type x11vnc -R forever everytime I open it?
Yes, just add "-forever" to the x11vnc command line:
```
x11vnc -forever
```
If you are using a GUI filemanager somehow to start x11vnc, either configure it to add "-forever", or make a shell script with "x11vnc -forever" in it and click on it instead.

---

### Post by magikx21 on 2008-01-15
Thanks, I guess I was overlooking the obvious on this one.

---


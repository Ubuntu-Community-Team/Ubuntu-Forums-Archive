---
title: "Hidden SSID without encryption"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by Geekboy on 2008-05-06
I am trying to configure an IBM Thinkpad T42 to connect to our open network at work.  The network has a Hidden SSID but does not have any encryption (WEP,WPA).

I see that I can enter the SSID in Network Manager but I cannot set the network to open.  Is there something I am missing?

Thanks.

---

### Post by jimv on 2008-05-06
I think that in network manager you just don't put a password and that makes it open.

But I use WICD, so I don't know for sure.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Geekboy on 2008-05-06
But I don't want to enable WEP or WPA.  It's really just an open wireless connection.  It's just the SSID is not broadcasted.

---

### Post by subzero316 on 2008-05-07
try that command and see if the hidden networks are listed 
```
iwlist scan
```
 enter name as metioned.

---

### Post by Geekboy on 2008-05-07
Well, I got the wireless working.  I finally gave up on Network Manager installed WICD from the repositories.  It found the hidden SSID immediately, I didn't even have to add it.

---

### Post by jimv on 2008-05-07
Doesn't WICD rock compared to NM?

---

### Post by Geekboy on 2008-05-07
Yeah, it worked right away.  Solved my problem.

---


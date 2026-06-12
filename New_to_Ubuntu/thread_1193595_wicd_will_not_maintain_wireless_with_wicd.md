---
title: "wicd will not maintain wireless with wicd"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-06-21
connecting to my wireless via wicd will not hold a connection about every 15 seconds or so it will retry the connection my wired is ok. this does not happen with network manager anyone able to help?

---

### Post by kerry_s on 2009-06-21
why not just use network manager or go manual and skip a manager all together.

---

### Post by RedSingularity on 2009-06-21
Can you connect at all wirelessly with wicd?

---

### Post by PatrickMoore on 2009-06-21
it connects then disconnects automatically in about 15 seconds.
i was switching to wicd on advise to resolve the wireless issue with jaunty. my speeds are pitiful

---

### Post by RedSingularity on 2009-06-21
Just in case look in 

System>Admin>Hardware drivers   and see if you can activate anything.

Also post the output of "lspci"

---

### Post by imdano on 2009-06-22
Most likely your signal strength is showing up as 0 in iwconfig when you're connected wirelessly.  If that keeps up for 12 seconds wicd declares the connection dead and tries to reconnect you.  You can try to disable this by unchecking the "Automatically reconnect on connection loss" checkbox in the preferences window.

---

### Post by TeoBigusGeekus on 2009-06-22
Look at the last post.
[http://ubuntuforums.org/showthread.php?t=1173119]("http://ubuntuforums.org/showthread.php?t=1173119")

---


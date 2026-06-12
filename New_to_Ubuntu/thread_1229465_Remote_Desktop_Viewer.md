---
title: "Remote Desktop Viewer"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-08-02
I am trying to reset up my Remote Desktop Viewer......but I keep getting this message when I try to access the second PC.

Connection to host pj-weather.local:5900 was closed.

The port is closed automatically it would seem....how do I reopen it and keep it open?

---

### Post by hellmet on 2009-08-02
You might have to open up a port on the firewall on the second PC and/or enable Remote Desktop

---

### Post by dunbrokin on 2009-08-02
Remote desktop is enabled and there is no firewall on the remote machine....there is a firewall on this machine but I have disabled it...

---

### Post by gn2 on 2009-08-02
You might have to open port 5900 on the routers?

[http://www.realvnc.com/support/portforward.html](http://www.realvnc.com/support/portforward.html)

---

### Post by dunbrokin on 2009-08-02
Sorryn nothing there seemed to help me open port 5900

---

### Post by dunbrokin on 2009-08-02
Apologies to all....problem solved....basic user error....

---

### Post by hellmet on 2009-08-02
And that was? You owe the community an answer, my friend.

---

### Post by dunbrokin on 2009-08-03
While Remote Viewer was switched on in the master pc it was actually switched on in the slave PC.....I was sure it was.....checking again revealed otherwise...

---

### Post by HermanAB on 2009-08-03
Please note that VNC is insecure and a prime reason why Ubuntu machines get hacked.  Rather install SSH.  It is secure and can do everything VNC does and much more.

---

### Post by dunbrokin on 2009-08-03
This is behind my firewall....

---

### Post by HermanAB on 2009-08-03
VNC is OK on a LAN.  Just don't ever expose it to the Wild Wild World.

---

### Post by LarryJ2 on 2009-11-04
I have two pcs in a local LAN.  One is Karmic and the other is Hardy updated.   I kept getting the   "connection to host was closed" error message from Karmic while attempting to connect to Hardy   until I opened up System->Preferences->Remote Desktop->Advanced  on the Hardy machine then UNCHECKED the box by "only allow local connections".   

Now that would seem expose this PC to the internet  but I am behind a wireless / router firewall anyway.   Steve Gibsons  grc.com doesn't show any open 5900 port and  the remote desktop program "vinagre" (Applications -> Internet -> Remote Desktop Viewer)  is working again.  

Un- checking this  box certainly is counter intuitive. A bug?

---


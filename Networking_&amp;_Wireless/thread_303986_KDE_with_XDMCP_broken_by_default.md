---
title: "KDE with XDMCP broken by default?"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by whizbaby on 2006-11-21
I have the following problem:
when I connect to a standard ubuntu-client with Xnest and chose a kde session, wait a bit (10 secs) and then logout the remote xserver crashes and will show a grey fuzzy screen until you restart the xserver on the client. There is no problem logging out remotely with gnome or xfce, it's only KDE-related. And it has nothing to do with custom settings on the client because it also happens on a fresh clean desktop install on different hardware. Anybody?

---

### Post by whizbaby on 2006-11-21
Here some additional info:
Above happens on Ubuntu Dapper 6.06 install. I installed edgy just to see if there's any difference. Following happens if you remotely log out from KDE on edgy:
an error message with backtracing will pop up (see attachment). Then the xserver restarts as expected, so on 6.10 you only get a strange error message and the xserver-crash doesn't occur.

---

### Post by andresin on 2006-11-24
Same problem here. I have googled a lot without any luck. I have 15 terminals don't working because of this.

---

### Post by whizbaby on 2006-11-30
We have like 50 ThinClients...
It has something to do with the changed ksmserver package. I was able to logout (two times) normally with copying a ksmserverrc to a users home just after login. However, that one stopped working...](*,) 
Will this ever be fixed or do people think it's not so important?

---

### Post by andresin on 2006-12-07
About 20 thin clients here.

The main difference between breezy & dapper I am seeing on this is that restarting gdm doesn't kill any session, so the temporary solution I found is restarting it every 10 minutes. We use openLDAP for auth so I sun:

gdm stop
nscd restart
gdm start


I guess it's no so important for most of the userbase: it comes from dapper and hasn't been fixed yet.

---


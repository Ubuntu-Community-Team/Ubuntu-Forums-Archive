---
title: "Only via proxy server but not direct connection."
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by mahinda on 2008-04-01
In my university we had two options to get connected to internet. One is via proxy server and other one with direct connection.

Due to some unknown reason, Ubuntu OS let me connect via only proxy, but not direct connection. But same machine allow me to connect both ways in Windows.

My problem is university terminated proxy option and now we have only direct connection. So now I can’t connect to internet with Ubuntu OS. Please help me in very basic steps since I am new to Linux.

---

### Post by bapoumba on 2008-04-01
Where do you change the proxy settings?
Please look in:
```
gnome-network-preferences
```

---

### Post by mahinda on 2008-04-01
I set to  'direct internet connection'  in preferences > network proxy

early it work with proxy, now problem is I can't use it since university allow direct connection only. 
(With Windows it working well with same setting but not with Ubuntu.)

Probable I need to say we use static IP.

bapoumba, 
Not clear what you mean with this......
gnome-network-preferences

---

### Post by bapoumba on 2008-04-03
gnome-network-preferences, if entered in a terminal, will get you to the menu where you can configure the proxy settings, but you have already found it.
Static IP should not be an issue.
If you are using Firefox, did you also change the proxy in Edit > Prefs > Advanced > Network > Connexion > Settings ?

---

### Post by mahinda on 2008-04-03
Yes, I changed in Ffirefox setting as well. Anything else I need to think of ?

---


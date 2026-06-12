---
title: "TightVNC"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by Hyuukai on 2008-08-16
Ok i installed TightVNC.exe on my windows xp machine and i installed TightVNC on ubuntu via synaptic package manager but being new to ubuntu and sometimes a little stupid i couldnt find where to run TightVNC from as there was no shortcut and i couldnt find it in the applications places or system? i know this is very trivial but could someone help me out please?

---

### Post by kool_kat_os on 2008-08-16
Do you want to connect to the ubuntu computer or connect to another computer through the ubuntu computer?

---

### Post by Scotty Bones on 2008-08-16
Remote Desktop Viewer
it should be in the internet menu

---

### Post by Hyuukai on 2008-08-17
I found tht but wasnt sure if it was TightVNC where is the server side?

---

### Post by Scotty Bones on 2008-08-17
The server-side of TightVNC is cli. Ubuntu does have a built-in server called vino.  This link might help.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by Hyuukai on 2008-08-22
managed to get tightvnc working on ubuntu but i cannot seem to connect to my windows pc using tightvnc i have done the port forwarding on the router but i guess i have done it wrong because i can do it over my local ip 192.168 ip but when i try do it over my internet ip it doesnt work.

---

### Post by Sooner Al on 2008-08-22
Remember that if your behind a router then calling the VNC host/server PC from another PC on the same LAN using the public IP of the router may not work. Many consumer grade routers do not support that loopback function. You really need to test from a remote location, ie. public wireless hotspot or friends house. Make sure TCP Port 5900 is forwarded through the router.

---

### Post by Hyuukai on 2008-08-22
I never thought about that but i got my friend to try and he failed, but he could of done something wrong i will remotely try it soon

---


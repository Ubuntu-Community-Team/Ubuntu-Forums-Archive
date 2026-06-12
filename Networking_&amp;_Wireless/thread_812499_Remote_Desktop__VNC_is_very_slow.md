---
title: "Remote Desktop / VNC is very slow"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by elperrillo on 2008-05-29
I have Ubuntu at home and at work, If I do a remote desktop from a Windows machine at work to my Ubuntu server (gigabit connection) is very slow I have to reduce the colors and even like that it is still slow. 

If I do the same on my home network it is very fast, almost real time and at full colors. 

How can I determine whats causing this?

---

### Post by bluefrog on 2008-05-30
your home adsl upload must not be very high.

anyway, use ssh with putty, it will be fast. you could eventually try X forwarding if you cannot manage your server by command line, but you would need a linux pc (ssh -Y user@IP)

---

### Post by elperrillo on 2008-05-30
How come when I connect via VPN to my Windows Servers using Windows Remote Desktop it works fast? Is Windows Remote Desktop more efficient than VNC?

---

### Post by bluefrog on 2008-05-30
could be.

---

### Post by jimv on 2008-05-30
I've noticed at home and at work that Windows Remote Desktop is a lot faster than VNC.

---

### Post by elperrillo on 2008-05-31
ok thats all I wanted to know, thanks guys.

---


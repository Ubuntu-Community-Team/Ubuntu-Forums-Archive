---
title: "Ics for xbox through ethernet"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by cheeseburgerman1 on 2009-01-22
Okay, so here's my setup. I have my cable router connected to the pc through a usb cable, it shows up as auth1. I have my xbox connected to the pc through the ethernet cable. It shows up as auth0. Now ive been trying to get this setup to work in ubuntu. Ive been trying to use firestarter. The problem happens when i try to start the firestarter firewall with ics enabled for the xbox. I get an error message saying auth0 not ready, please check something somewhere and try again.

---

### Post by Nepherte on 2009-01-22
Why do you need firestarter? The firewall iptables is already running and doesn't require firestarter to run at all. The default rules of iptables are also good enough for a typical user.

That being said, I believe you have to pick auth0 somewhere in the preference window of firestarter instead of auth1.

---


---
title: "Network Icon not appearing"
date: 2022-03-15
forum: Networking &amp; Wireless
---

### Post by annieuk on 2022-03-15
When I boot up my Raspberry Pi the Network Icon is missing from the task bar I have to run the command "**sudo systemctl start NetworkManager**" to get the icon back before I can apt update etc without errors

Anyone know how to fix this?

I have applied a work-a-round by running a script at startup that starts the NetworkManager but would like a proper fix

---

### Post by slickymaster on 2022-03-15
*Thread moved to **Networking & Wireless**.*

---

### Post by ActionParsnip on 2022-03-15
Does the networking work without the icon present?

---

### Post by annieuk on 2022-03-15
Mostly it works but if I use APT UPDATE then I get errors, the Pi is a web server and that seems to works OK also I use SSH to access it and that works

---

### Post by ActionParsnip on 2022-03-15
What errors do you get with apt, please?

---

### Post by annieuk on 2022-03-15
Typical I cannot get the thing to break now ???

I'm so confused, I renamed my script but the error still has gone

NetworkManager status used to give an unexpected error GetNameOwner() from systemd[1] but that has vanished as magically as it appeared

---


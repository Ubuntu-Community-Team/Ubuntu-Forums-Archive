---
title: "Network manager issue"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by joselin on 2007-06-20
For the last times, when I switch on my computer, the network manager ask me for the keyring password to connect me to wireless network even if my ethernet cable are connected.

After NM connect me to wireless network, my wired network is working too. So, I'm connected to both networks.

Is there a way to tell NM to use only wired network in this situation?

Regards.

---

### Post by benanzo on 2007-06-20
I think the easiest way is to just right-click the NM applet and select to disable the wireless.  I am surprised that NM allows both connections simultaneously.  I thought it always preferred the wired connection.

---

### Post by joselin on 2007-06-21
The easiest way is obvious, what about the hardest one?

---

### Post by benanzo on 2007-06-21
did the easiest way not work?

In my experience, if I start NM with my ethernet connected then the wireless doesn't even try to connect.  But if I start without ethernet, then the wireless connects - but if I connect the ethernet later, the wireless disconnects and just goes with ethernet.

This isn't very ideal, however, since a practical use of having two network connections would be for connecting to a public and a private network simultaneously.  I think the newest revisions of NM address this issue by allowing for location-based profiles.

---

### Post by joselin on 2007-06-22
> **benanzo said:**
> 
In my experience, if I start NM with my ethernet connected then the wireless doesn't even try to connect.  But if I start without ethernet, then the wireless connects - but if I connect the ethernet later, the wireless disconnects and just goes with ethernet.

This is what I want. When I connect the ethernet my wireless does not disconnect.

---


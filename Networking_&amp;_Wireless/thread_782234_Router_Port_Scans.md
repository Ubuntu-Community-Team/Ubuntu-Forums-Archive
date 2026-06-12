---
title: "Router Port Scans"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Helios1276 on 2008-05-04
Is it normal for me to be getting port scans from my router? It's not noticeable in Hardy but my Sygate firewall in xp is kicking up a fuss and momentarily blocking the router address when it happens, this is about the third occasion it has happened in 2 weeks .

---

### Post by Monicker on 2008-05-04
> **Helios1276 said:**
> Is it normal for me to be getting port scans from my router? It's not noticeable in Hardy but my Sygate firewall in xp is kicking up a fuss and momentarily blocking the router address when it happens, this is about the third occasion it has happened in 2 weeks .

Seems unusual on the face of it.  Are you sure the scans are coming directly from your router?  What kind of router is it, and could you post of logs showing these scans?

---

### Post by Helios1276 on 2008-05-06
Excuse the massive delay(exams).Here is an example of one of the logs from my Sygate firewall. 

"Somebody is scanning your computer.
 Your computer's UDP ports: 
 1900, 28179, 48563,  and 42188 have been scanned from 192.168.2.1.."

---

### Post by Monicker on 2008-05-06
> **Helios1276 said:**
> Excuse the massive delay(exams).Here is an example of one of the logs from my Sygate firewall. 

"Somebody is scanning your computer.
 Your computer's UDP ports: 
 1900, 28179, 48563,  and 42188 have been scanned from 192.168.2.1.."

Is your workstation set up as dmz host on router?  I could see that causing you to get a lot hits on your firewall, but it still should show the original source host for the traffic, and not the router itself.

---


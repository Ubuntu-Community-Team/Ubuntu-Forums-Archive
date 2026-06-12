---
title: "Can't view Windows hidden network shares"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Ryzol on 2008-06-11
There are two hidden shares on a windows network that I need to be able to access. How do I view files on them? When I use Places -> Network and browse to the right place the servers show as empty.

---

### Post by estamand on 2008-06-11
> **Ryzol said:**
> There are two hidden shares on a windows network that I need to be able to access. How do I view files on them? When I use Places -> Network and browse to the right place the servers show as empty.

That is why they are hidden so you can't see them without having to specifically specify the share name.

Try "Connect to Server" and specify the windows machine and the share (ie c$ or share$)

---

### Post by sbrandon on 2008-06-11
In the same boat and the shared$ is mine on the windows server.  When I try to connect to server - smb cannot mount the file.  I have connected to the network via Likewise.  Any thoughts would be helpful.

---

### Post by imnok1 on 2009-03-07
(this is one of those "i know it's 9 months later but..." in case someone else searches and finds this forum like i did)

i had the same issue but then mine turned out to be a simple solution.
i was using login credentials of *localusername* instead of *localhost\localusername*

---

### Post by sbrandon on 2009-04-08
imnok1 - are you talking about the localhost of your Ubuntu box or your windows box that you would use to log into the network and access those hidden shares?

---


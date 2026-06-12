---
title: "Hostname not seen by other computers on network"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by paulgb on 2007-01-09
I have a server running Ubuntu. I can connect to it on the local network through its IP, but not through the hostname. Pinging the hostname from Win XP gives "Ping request could not find host". I have tried resetting both computers and the router, and running "sudo hostname domino", but no luck. I searched the forums and found other people with similar problems, but no one seemed to have an answer.

---

### Post by meng on 2007-01-09
Try editing your hosts file on Windows, I always forget the location, but according to wikipedia:
Windows NT/2000/XP/Vista: %SystemRoot%\system32\drivers\etc\ is the default location, which may be changed. The actual directory is determined by the Registry key

---

### Post by paulgb on 2007-01-09
Thanks, the only problem with that is that IPs are dynamically assigned and I need to access the server from multiple computers, which would result in a lot of hosts file editing. I noticed that the windows computers can ping each other by hostname, but the Ubuntu server is not able to be pinged by name or ping other servers by name. Is this handled by SAMBA or something?

I forgot to mention, I have only SSH access to this server and it does not have any GUI installed.

---

### Post by meng on 2007-01-09
> **paulgb said:**
> Thanks, the only problem with that is that IPs are dynamically assigned and I need to access the server from multiple computers, which would result in a lot of hosts file editing.

Gotcha. I feared it may be something like that. I've never got that working despite having an Ubuntu as the WINS.

---


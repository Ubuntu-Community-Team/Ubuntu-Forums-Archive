---
title: "How I should configure MythTV Backend"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by loudestnoise on 2007-08-15
I am rather unsure of what I should be setting as the IP address for my MythTV Backend.  I started off with the default 127.0.0.1, but then as I started playing with Mythweb and other things I ended up changing it. Now I when I run mythfrontend it tells me that it could not connect to the master backend server.  I have it set now to be 127.0.0.1 and I made sure that frontend is looking for the same IP. Or should I set front end to look for localhost as the Host Name.  I'd like to be able to use Mythweb, but right now I just want frontend to work again.

---

### Post by praet on 2007-08-16
127.0.0.1 is the private non routable localhost address. It will only be accessible from the machine itself.  If you are running the frontend and backend on the same machine then this ip address is fine.  If you are connecting a frontend through a network to the backend on a different machine, you will need to set a different ip address (preferably one that doesnt change).

With mythweb running on the same machine, you also will not have to change the backend ip from 127.0.0.1.  To access mythweb from another computer, you will need to know the ip address to connect to (like http://mymythbox/mythweb or http://192.168.1.10/mythweb)

---


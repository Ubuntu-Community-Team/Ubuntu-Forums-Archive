---
title: "UFW and nginx reverse proxy"
date: 2020-07-05
forum: Networking &amp; Wireless
---

### Post by vwenberg on 2020-07-05
Hello!

I've hit a wall trying to figure this out. I use nginx to do a reverse proxy to a docker app running on port 82. However, I would like to prevent people from accessing port 82 and only access the app through the reverse proxy domain name. Both the docker app and nginx are running on the same machine. I've allowed connections to port 82 from the IP and 127.0.0.1, but I can't seem to access it through the reverse proxy unless I open 82 up to everyone.

Any help would be greatly appreciated.

---

### Post by TheFu on 2020-07-07
This is a docker question first.

I use nginx as a reverse proxy and ufw as a simple firewall, usually with ipset to block thousands of nasty subnets, and don't have a clue how to help you due to the docker aspect. 

If you can, put docker as the first word in the thread title.

---


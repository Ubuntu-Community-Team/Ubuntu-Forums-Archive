---
title: "Help - How do I use &quot;host name&quot; or similar in place of [dynamic] IP?"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by tj.milligan on 2007-01-06
New to networking in Ubuntu. I'm using nfs to share files between two edgy machines. The master's IP is [currently] 192.168.1.2, while the slaves is [currently] 192.168.1.3. Problem is, these IPs change depending on the order the computers are started. This presents a big problem in nfs's /etc/exports file, because I have to change the IP by hand all too often. For example, a line from /etc/exports reads

/media/audio 192.168.1.3(ro)

Is there a way to use a name rather than an IP address here? Please explain in detail. I have nothing in the way of networking installed besides nfs (on the master computer) and a connection to the internet supplied by wireless router on the slave and hard connection to [the same] router on the master.

Thanks!

---

### Post by capitalistpiglet on 2007-01-06
The problem is if you assign a name to a ip address then you will have to change the hsot name each time the ip address changes. You need to give each machine a static ip address to solve this problem. Go into your router configuration and set each machine a static ip address that will solve the problem.
Also to give each machine a name you just need to add a entry in the /etc/hosts file of the machine your connecting from something like
"192.168.1.101 desktop" without the quote marks.

---

### Post by tj.milligan on 2007-01-06
Thanks a lot capitalistpiglet!! This is the solution for my problem!

---


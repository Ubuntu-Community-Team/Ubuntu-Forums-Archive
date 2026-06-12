---
title: "Networking Confusion"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by _lynX on 2007-03-12
Before I begin, I want to give a general layout for the LAN:
The DSL line runs from the wall in the basement, to a Westell modem/router device. From the Westell there are two cables, one which runs to a grey router which services the entire basement, and another cable which runs to the upstairs. The upstairs router is a Netgear Wireless Router MR814v2. 

The Westell takes the local address of 192.168.1.1, and the Netgear is assigned the address of 192.168.1.97 (or 192.168.0.1), and assigns all further ip addresses to 192.168.0.*. Connected to the upstairs router, we have three Macbooks (wireless), and one wired Ubuntu 6.10 server install.

The problem that we're running into relates to port forwarding. We want to use the Ubuntu 6.10 server to run services such as SSH and FTP, which install and function perfectly. We can connect to the server's SSH using its local ip of 192.168.0.10. However, when we try to forward ports (we're tried many different configurations; forwarding the port from the Westell to the Netgear, and then to the server, etc.)  so that we can connect using the actual ip address, we are receiving "connection refused" errors.

I hope that I've posted enough information, but if more is needed, please let me know.

---

### Post by koenn on 2007-03-12
ah, confusion.
I read your post twice and still don't see what you're trying to do.
Could you post a little drawing and maybe explain what the NAT and port forwarding is meant for ?

---

### Post by Mr. C. on 2007-03-12
_lynX,

Are you under the impression that you should be from your LAN to use your WAN IP address to connect to your services ?

I'm not sure I was clear on your port fowarding setup, but I understood you to indicate that you are trying for forward A -> B -> C but indicating to A that it should forward to B, which in turn should forward to C.  This won't work.  You need to tell A to foward to C, and let B act as a router to route the traffic.

It would be helpful if this post does not assist you to clarify your network more, as in :

Network 192.168.1.0/24
Westell router: 192.168.1.1

etc.

We'll get you going,
MrC

---

### Post by _lynX on 2007-03-12
> **Mr. C. said:**
> _lynX,

Are you under the impression that you should be from your LAN to use your WAN IP address to connect to your services ?

I'm not sure I was clear on your port fowarding setup, but I understood you to indicate that you are trying for forward A -> B -> C but indicating to A that it should forward to B, which in turn should forward to C.  This won't work.  You need to tell A to foward to C, and let B act as a router to route the traffic.

It would be helpful if this post does not assist you to clarify your network more, as in :

Network 192.168.1.0/24
Westell router: 192.168.1.1

etc.

We'll get you going,
MrC

As soon as I return to my friend's house, I will post more details. From what you said though, I remembered that I tried to tell A (Westell, 192.168.1.1) to forward it to C (Ubuntu server, 192.168.0.10), but A gave me an error saying that C was not part of the private LAN. Could the problem possibly come from A just being outdated? :D

---

### Post by Mr. C. on 2007-03-12
I don't know.  I have to see what your network topology looks like.  Please describe that when you get a chance.

MrC

---


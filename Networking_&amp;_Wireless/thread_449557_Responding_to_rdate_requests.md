---
title: "Responding to rdate requests"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by The Belgain on 2007-05-20
I'm having trouble getting my Ubuntu machine to respond to rdate requests from remote hosts (the remote host being an MVP running mvpmc).  Googling suggests that this should just be a base of enabling the 'time' service in inetd, but this doesn't seem to work for me.

I've added the following lines to my /etc/inetd.conf file:
time stream tcp nowait root internal
time dgram udp wait root internal

What am I doing wrong here?

---


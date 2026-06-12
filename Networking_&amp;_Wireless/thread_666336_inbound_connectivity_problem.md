---
title: "inbound connectivity problem"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by redss on 2008-01-13
I have an ubuntu (7.04) system and a windows system connected to a 4 port router via hardwired static IP.

Often I am able to ssh into the ubuntu server from the windows box.  

However, lately sometimes the ubuntu server exhibits behavior where it does not respond to incoming connections.  When this happens I am unable to telnet to it on any port, and it doesn't respond to ping.

When it happens, the outbound connectivity is not affected at ALL, however for inbound connections, it becomes unreachable for up to half the time, switching between available/unavailable as often as once every couple minutes.  Sometimes I ssh in and my session freezes after 20 seconds.

How can I troubleshoot this?

---

### Post by evanchu on 2008-01-14
Let us collect some basic diagnostic information.  Run ifconfig on Ubuntu and post the output.  Run "ipconfig /all" on Windows and post the output.

---

### Post by redss on 2008-01-14
Well the problem went away when I reset the router from the admin page!

---


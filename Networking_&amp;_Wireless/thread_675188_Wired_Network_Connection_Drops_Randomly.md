---
title: "Wired Network Connection Drops Randomly"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by steve_c on 2008-01-22
I have a computer with a wired connection using a static IP. This is a server so most users connect remotely via SSH. Occasionally the connection will drop which shows up as a lack of response from the server which may eventually time out client-side. I still get responses when pinging the server remotely even when SSH traffic isn't working.

Physically on the server, I am also unable to ping anything beyond localhost. Localhost works. I cannot ssh out. I'm not seeing anything show up in /var/logs/syslog or messages. /etc/init.d/networking restart does not fix the problem, however, and this is interesting, unchecking and re-checking Enable Networking from the NetworkManager's nm-applet fixes the problem.

Anyone care to offer suggestions on what might be the cause and how to fix it, or at the very least tell me what the difference is between restarting NetworkManager and restarting networking from init.d?

Thanks in advance!

---


---
title: "cannot Setup Telnet"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by mys_shekar on 2008-02-18
Hi,
   I am trying to enable telnet on my Ubuntu gusty system..  I followed the following tutorial [http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html)
and installed telnet using the following command: sudo apt-get install telnetd. 
  The installation was successful, but I am not able to find telnet configuration file. when I try to telnet I get the following error..

telnet: Unable to connect to remote host: Connection refused

Can anyone inform me what the problem is

---

### Post by jhetrick62 on 2008-02-19
Check your /etc/inetd.conf file.  Also, you may have to open your firewall, I don't recall as I only am running ssh on mine.

Jeff

---


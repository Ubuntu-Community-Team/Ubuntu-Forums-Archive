---
title: "vnc specific ports"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2014-08-11
I an trying to set up vnc on 10 xubuntu computers and I want to open a incoming specific port for each. Example ubuntu10 is port 5918, ubuntu 8 is port 5916 etc. is there a way to do this I also have port 5900 open for vnc but my router allows me to open an incoming port for each remote connection. So far it works with windows but not xubuntu. x11vnc is working on all the computers. Also is it possible to specify which user it connects to? It has a place to put port range and local port.

---

### Post by TheFu on 2014-08-11
Using VNC over the internet is NOT secure. 
Need to use a VPN or ssh tunnel.  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Of course all the remote machines will need to have static IPs.  Many people will choose to setup a "jump box" that works from the internet, then hop to different internal machines. This reduces the open ports to the internet.  Be certain to use ssh-keys, not passwords.

---


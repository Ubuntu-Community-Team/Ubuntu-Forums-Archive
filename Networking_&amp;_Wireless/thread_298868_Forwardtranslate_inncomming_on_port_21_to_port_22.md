---
title: "Forward/translate inncomming on port 21 to port 22"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by Muffe on 2006-11-13
I have an Ubuntu server at home (Dapper LTS) that works as a router and server. Among other things, I run a SSH server to make me able to access the PC from anywhere in the world. Because of that, the firewall accepts incoming connections on port 22 (and 80 - but that's irrelevant).

The problem is that I will to access my server from the school network, but they block all outgoing connections on port 22. However, they do allow outgoing connections on port 21, witch I do not use on my server. I do not want to change what port the SSH server is listening on, because that would affect other clients and networks as well.

Is it possible to have iptbales to redirect all incoming connections from port 21 to port 22? I want to be able to connect to my SSH server on both port 21 and port 22, where port 22 is the port the SSH server is listening on.

---

### Post by evilghost on 2006-11-13
Check out 'redir', this may do exactly what you want.  You'll likely need to install it:

'sudo apt-get install redir'

---

### Post by bjd on 2006-11-13
Something like this might be sufficient:
sudo iptables -A PREROUTING -t nat -p tcp -i *<interface>* --dport 21 -j DNAT --to-destination *<your-ip>*:22

---


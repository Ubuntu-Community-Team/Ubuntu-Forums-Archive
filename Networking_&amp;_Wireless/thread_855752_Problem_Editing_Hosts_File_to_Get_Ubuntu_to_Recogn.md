---
title: "Problem Editing Hosts File to Get Ubuntu to Recognize Server Hostname"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2008-07-10
I have been trying to edit the /etc/hosts file on my server, so that I can use Connect to Server on my workstation and type in the hostname rather than the ip address for ssh.  However, it still comes back telling me it doesn't recognize the hostname; it only works with the ip address.  This is what the hosts file says:

127.0.0.1       localhost
#127.0.1.1      UbuntuServer
192.168.1.105   UbuntuServer

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I commented out the other ip address, but should I have both?  I am using dhcp right now.  Help!

---

### Post by HalPomeranz on 2008-07-11
You need to change the /etc/hosts file on your workstation, not on the server.  Undo your changes to the /etc/hosts file on the server and add this line to the /etc/hosts file on your workstation:

```

192.168.1.105 UbuntuServer

```

---


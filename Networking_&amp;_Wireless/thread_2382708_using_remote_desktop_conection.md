---
title: "using remote desktop conection"
date: 2018-01-16
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2018-01-16
If I wish to operate an Ubuntu 14.04 computer, not on my lan,  via my 16.04 Ubuntu Gnome. Using the built in application  it seems that I should be able to put in the url of the host computer and it should work (provided the correct permissions  have been ticked). I am wondering what the url should be.  Is it:

IPv4 address
IPv6 Address
Default Route 
DNS

---

### Post by TheFu on 2018-01-16
That isn't how it works, assuming I understand what you seek.

There is a client and there is a server.  The server must be pre-configured on the remote machine and any firewalls and/or routers need to allow the connection.  Plus, the most popular remote desktop tools are NOT secure, so you want a network encryption/tunnel.

The connection from the client to the server needs to use the public IP for the remote server.  That is **not** a 10.x.x.x/8 or a 172.16.x.x/12 or a 192.168.x.x/24 network address.

If the public IP on the remote server has a DNS name, you can use that. It is convenient for humans, usually, but a ~/.ssh/config file can make it just as convenient to use an IP, different userid and non-default port for the ssh connections.

Generally it is best to use **ssh** to access a remote system.  ssh is well understood, low bandwidth, encrypted, and with ssh-keys (never passwords), highly secure.  The remote system must be running the openssh-server package and have whatever port forwarding at the edge router and firewall allowing access.  Using denyhosts or fail2ban to secure against brute-force ssh attacks is smart too.

Once ssh is working, you can use that for an efficient remote desktop connection with the NX protocol.  x2go is the 'best' (for certain values of 'best') solution. NX uses ssh as part of the protocol, so there isn't anything more to setup from a security standpoint.  x2go must be installed. The client on the client and the server on the server.  Google will find the PPA which should be used for both.  The x2go client has a nice connection setup page which is pretty clear.

Clear as mud?

There are other solutions - use openvpn or libreSwan instead of ssh. Use VNC or X11 forwarding instead of x2go (or another NX tool).  X11 forwarding works fine on the same LAN, but not so great over the internet.  VNC is very popular, but about 2-3x slower than NX, plus it requires a separate network encryption and authentication solution to be secure.

---


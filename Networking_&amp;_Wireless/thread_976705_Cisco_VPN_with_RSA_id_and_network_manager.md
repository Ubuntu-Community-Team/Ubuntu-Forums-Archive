---
title: "Cisco VPN with RSA id and network manager"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by zordid on 2008-11-09
How can I configure the vpnc plug-in for the network manager to connect to my work via vpn. Today I start the connection from the command line like this:

```
sudo vpnc work --application-version "Cisco Systems VPN Client 4.8.00 (0490):Linux"

```
and my /etc/vpnc/work.conf looks like this

```
IPSec gateway gateway.address.com
IPSec ID Groupname
IPSec secret grouppassword
Xauth username Username
Xauth password userpassword
Xauth interactive
```

and I will then be asked for the RSA-id password.

---

### Post by joenieburg on 2009-01-08
We also have Cisco with rsa security. (it is a pix a believe with OS 5.1)

I use the networkmanager, but to get it working u need to install the networking-manager-vpnc
and the 
vpnc itself through synaptics. (or apt-get)
Then u can create a connection with your network through the Gui. 
The only trouble I have is u have to give the rsa key and the group passwoord everytime u want to logon.

I am looking for a way that the group password is already filed in so u only have to type the rsa key.

Another good thing about this one is u don need the Cisco Systems VPN Client 4.8.00 (0490):Linux client. And when u get update for Ubuntu it stays working :popcorn:

---


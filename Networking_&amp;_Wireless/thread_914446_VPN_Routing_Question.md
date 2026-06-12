---
title: "VPN Routing Question"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by schapman43 on 2008-09-08
I would like to setup a VPN connection to remote into my work box.  However, I don't want any other traffic going over that VPN connection.  I am able to connect with the VPN server and then remote that machine but my internet connection dies after connecting.  There is the section of the VPN configuration that deals with routing.  I do not have peer DNS through tunnel selected.  I do have 'Only use VPN for these connections' checked and I have the following addresses listed.
172.27.1.0/24 172.5.1.0/24

Through VPN I am assigned a 172.27.5.x address
The box that I am remoting is 172.27.1.x

Can anyone see any obvious issues with my configuration?

--Scott

---

### Post by schapman43 on 2008-09-08
Fixed it.  Under PPP Options I unchecked use peer DNS.

---


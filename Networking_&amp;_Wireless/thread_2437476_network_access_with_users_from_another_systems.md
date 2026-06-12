---
title: "network access with users from another systems"
date: 2020-02-24
forum: Networking &amp; Wireless
---

### Post by nixoft on 2020-02-24
I've connected 5 computers using one switch and installed Samba on the systems and created a network password for each system and shared the public folder of each system on the network but still can't access the folder Shared other system logs I even created a username system with another system name but I can't enter the shared folder again
Do I need to create 5 usernames and 5 passwords for the Samba network in each system? Or is networking architecture in Ubuntu any different?

---

### Post by TheFu on 2020-02-24
Unix systems use IP networking.  The easiest way to make systems be able to find each other is to have a router on the network.  You can keep the switch, but 
a) somehow, each system must have an IP address.
b) somehow, each system must have a netmask.
c) somehow, each system must have a gateway.
Those things can be manually entered for each system on each system, or a DHCP server, usually provided by the router, can provide each client device with compatible settings.

If the computers aren't Windows, there are better choices for sharing storage between them.  Shared storage is a very tiny part of what computer networks can accomplish.  NFS, the native way for Unix-like systems (everything except Windows), requires 1 line of configuration on the server and 1 line of configuration on each client machine.  Much easier to setup than Samba and usually faster.  NFS is server-to-server, not user-to-server.

> Do I need to create 5 usernames and 5 passwords for the Samba network in each system?
Not in my experience. Each samba server needs to have a samba userid and that password must be set.  The clients will access it using the credentials.  If each samba server is configured with the same userid/password, then once the authentication is provided to the server, the connection should work fine.

If there are many users, say 10, it might be worth setting up centralized LDAP for authentication with both Linux and Windows logins. That is a bit of a hassle, but it will make other authentication needs a little easier.

But really, start with putting a router on the network.

---


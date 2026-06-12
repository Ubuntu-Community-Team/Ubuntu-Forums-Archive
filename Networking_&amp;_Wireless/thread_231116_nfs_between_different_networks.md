---
title: "nfs between different networks"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by jinx099 on 2006-08-07
I am having trouble mounting via NFS between 2 different networks.  My NFS server is on the 192.168.100.0 network while the client is on the 192.168.10.0 network.  

I have followed the Wiki article and have even done the portmap part on both the server and client.  My /etc/exports has just a *(rw,sync) entry for dir that I want to mount.  The dir's perms are 777 and both server and client are running ubuntu dapper with the same user, password, and UID.

The reason for being on 2 different networks is that one network is for wireless and the other is for LAN.  I have set my firewall rules to allow access form my laptop (client) to access all parts of the network.  I can ping, ssh, vnc, etc the server box, but for NFS, I get this:  

mount: (server):/pbd failed, reason given by server: Permission denied

When I have the client and server on the same network, it works fine.  Can anyone help?  :(

---

### Post by jinx099 on 2006-08-07
hmmmm, when I try to NFS mount from the server to the client, I get this:

mount to NFS server '192.168.10.5' failed.

But again, works flawlessly when both are on the same network...  

HELP!

---

### Post by jinx099 on 2006-08-07
anyone?

---

### Post by sp4rd on 2006-08-09
I remember doing this many moons ago, it has something to do with assigning portnumbers to you rpc daemons like rpc.statd,rpc.mountd, and rpc.lockd.  Normally nfs will choose the port numbers randomly within a certain range, what you want to do is have a known port number assigned to those so it doesn't confuse your firewall.  I think you can assign the portnumber for rpc.statd/nfs-common through the /etc/defaults/nfs-common file that may be all you need.  If not look at this page [http://fritz.potsdam.edu/man/nfs/nfs_firewall.html](http://fritz.potsdam.edu/man/nfs/nfs_firewall.html)
on tips to set up nfs to use fixed ip ports.  Also if you have any entries in /etc/hosts.allow and /etc/hosts.deny for portmap you may need allow access to both networks that you're trying to reach.

---

### Post by jinx099 on 2006-09-07
I just want to add to this that I've solved the problem in case anyone searches for this.

The problem was that from the seperate network, the NFS request was coming from the router/ firewall.  So to fix the problem, all I had to do was add an allowed IP to NFS for the router.

---


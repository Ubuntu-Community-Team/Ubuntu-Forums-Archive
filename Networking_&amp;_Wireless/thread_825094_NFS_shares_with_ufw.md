---
title: "NFS shares with ufw"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by paapereira on 2008-06-10
I'm using ufw (Uncomplicated Firewall) and I'm having problems mounting my NFS shares with the firewall enabled.

Can someone post the ufw rules used to make NFS work?

Both the client and the server are running Ubuntu Hardy.


Thanks a lot!

---

### Post by jbrown96 on 2008-06-11
you need to open 2049tcp/udp and 111tcp/udp. I believe the command is```
sudo ufw allow tcp 2049
``` obviously you would change the tcp and port number depending on which ports you are opening. The problem is that NFS really sucks security wise. I use NFS on my laptop; if you are doing the same thing; I would just disable ufw when using NFS and reenable it when not. Ubuntu doesn't open any ports by default. Unless you have opened other ports, these (2049 and 111) would be the only ones open anyways, so using UFW without any services running doesn't do anything.

---

### Post by cjsmith on 2008-12-20
I found the solution for me to be binding the rpc.mountd daemon to a specific port.  In Ubuntu you should be able to modify the following file

```
sudo nano /etc/default/nfs-kernel-server
```

You're looking to find the variable RPCMOUNTDOPTS and define a static port like so :

```
RPCMOUNTDOPTS="-p 33333"
```

The 33333 is just an example -- use something that is available on your system and isn't already defined in your services file

After you've done that, you'll need to modify ufw with the following rules :

```
sudo ufw allow from 192.168.1.0/24 to any port 2049
```
```
sudo ufw allow from 192.168.1.0/24 to any port 33333
```

Where 2049 is your nfs port, 33333 is your static rpc.mountd port, and 192.168.1.0/24 is the subnet that contains your allowed clients.  Once this is done you should be able to mount nfs from your remote system (assuming exports are defined correctly).  When possible, it's a good idea to disable ufw temporarily and attempt to mount nfs remotely to be sure that you're working on the correct issue.

Cheers,

Cameron Smith

---


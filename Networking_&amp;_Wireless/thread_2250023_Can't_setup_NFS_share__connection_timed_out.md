---
title: "Can't setup NFS share : connection timed out"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by tnarol on 2014-10-26
Hello I'm trying to setup NFS a share between one machine running 12.04 (192.168.1.4) and another one running 14.04 (192.168.1.47)
They can ping each other over the network

I followed the steps described here [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

Here's my /etc/exports on the server
```

/export       192.168.1.0/24(rw,fsid=0,no_subtree_check,sync)
/export/tnarol 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,sync)

```

/export/tnarol is correctly binded to /home/tnarol

On the client the following command results in a connection timeout :
```

sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.1.4:/tnarol /mnt/nfsmount

```
On the server the same command works perfectly, I got my mount on /mnt/nfsmount

I imagine somehow the client can't reach the server, but I have no idea what to change. Can you help please ?

---

### Post by TheFu on 2014-10-26
Try```

sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.1.4:/export/tnarol /mnt/nfsmount
```

BTW - I thought nfsv4 required kerberos. Try NFSv3 with the command above.
I've never used most of the options you are pushing.

I'd use 
```
sudo mount -t nfs  192.168.1.4:/export/tnarol /mnt/nfsmount

```

---

### Post by tnarol on 2014-10-28
Found the solution... was an Ubuntu firewall issue. Not very easy to configure port by port, I had to disable it totally.

---

### Post by TheFu on 2014-10-28
Glad you solved it!  And extremely happy that you reported back so others can learn too.

So ... all versions of Linux use the same firewall - iptables. There are 10-100 interfaces to it. Some are easy, some are powerful, but they all modify iptables underneath.  Of course, for complete power, using iptables directly is the way folks do it. Iptables is NOT just a port-blocking firewall - it can track connections, limit bandwidth and probably 50 other things I don't know.  Of course, for someone new to it, the interface can seem overly complex.  

Depending on what I need on the system, I'll use ufw, gufw or iptables directly. I do not mix the tool used on a single machine.

---


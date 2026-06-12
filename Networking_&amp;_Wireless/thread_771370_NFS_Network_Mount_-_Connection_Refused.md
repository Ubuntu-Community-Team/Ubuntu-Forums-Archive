---
title: "NFS Network Mount - Connection Refused"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by hansoffate on 2008-04-27
Host Computer with files located at "/share/Musik" on ip 192.168.1.115

I am trying to add this to fstab so it will be mounted on boot to /share/Musik (it's the same structure).  I have added this line to fstab:
```
192.168.1.115:/share/Musik /share/Musik nfs defaults 0 0
```

When I try to sudo mount -a, I get this error.
```
mount.nfs: mount to NFS server '192.168.1.115' failed: System Error: Connection refused
```

Any ideas on how to fix this?

Thanks,
Hans

---

### Post by blastus on 2008-04-27
What's in the /etc/exports file on 192.168.1.115 and what's the IP address of the client machine?

---

### Post by hansoffate on 2008-04-27
My client machine is 192.168.1.109.  There is nothing written in /etc/exports or /etc/exportfs.  Should there be?

---

### Post by blastus on 2008-04-27
> **hansoffate said:**
> My client machine is 192.168.1.109.  There is nothing written in /etc/exports or /etc/exportfs.  Should there be?

On the server (192.168.1.115) you should install...
```
sudo aptitude install nfs-kernel-server nfs-common portmap
```

The etc/exports file should contain the following line if you want just one client to have access to the share...
```
/share/Musik 192.168.1.109(rw,async,no_subtree_check)
```

OR if you want all clients to have access to the share... 
```
/share/Musik 192.168.1.0/24(rw,async,no_subtree_check)
```

Then restart the server with...
```
sudo /etc/init.d/nfs-kernel-server restart
```

On the client (192.168.1.109) you should be able to mount the share with...
```
sudo mount 192.168.1.115:/share/Musik /share/Musik
```

Edit: Instead of using IP addresses you can use host names. If the server host name is server1 and the client host name is client1 then you should be able to use server1.local and client1.local instead of IP addresses.

---

### Post by hansoffate on 2008-04-27
Thanks for the help.  I got it shared and now I'm listening to music on the client pc.

---

### Post by blastus on 2008-04-27
That's great :) 

Just remember the client has to be connected to your network before you can start the server. If you connect the client afterwards, you'll have to restart the server.

---


---
title: "nfs not showing on clients"
date: 2019-12-06
forum: Networking &amp; Wireless
---

### Post by rw342 on 2019-12-06
I have a five node cluster (server +4 clients) running Ubuntu 16.04 LTS. I can ping from all nodes. 
I want to install an NFS on the cluster. I installed nfs on the server and nfs-common on the clients.

However, NFS doesn't show on the client. 

**SERVER**

```
clusteruser@c1:~$ ss -at
State      Recv-Q Send-Q Local Address:Port                 Peer Address:Port                
LISTEN     0      128        *:44747                    *:*                    
LISTEN     0      64         *:37710                    *:*                    
LISTEN     0      128        *:sunrpc                   *:*                    
LISTEN     0      128        *:51859                    *:*                    
LISTEN     0      128        *:ssh                      *:*                    
LISTEN     0      64         *:nfs                      *:*                    
LISTEN     0      128        *:44132                    *:*                    
ESTAB      0      0      192.168.1.1:38744                192.168.1.2:ssh                  
ESTAB      0      0      10.22.200.65:ssh                  10.22.162.209:41706                
ESTAB      0      36     10.22.200.65:ssh                  10.22.162.209:41704                
LISTEN     0      128       :::46668                   :::*                    
LISTEN     0      128       :::35055                   :::*                    
LISTEN     0      128       :::sunrpc                  :::*                    
LISTEN     0      128       :::49072                   :::*                    
LISTEN     0      128       :::ssh                     :::*                    
LISTEN     0      64        :::46590                   :::*                    
LISTEN     0      64        :::nfs                     :::* 
``` 

**CLIENT**


```
clusteruser@c2:~$ ss -at
State      Recv-Q Send-Q Local Address:Port                 Peer Address:Port                
LISTEN     0      128        *:sunrpc                   *:*                    
LISTEN     0      128        *:ssh                      *:*                    
ESTAB      0      0      192.168.1.2:ssh                  192.168.1.1:38744                
LISTEN     0      128       :::sunrpc                  :::*                    
LISTEN     0      128       :::ssh                     :::*    

```

---

### Post by TheFu on 2019-12-06
Did you mount storage from the server?  Clients don't have listeners, usually.
Is the server /etc/exports file setup? Does it export storage to the clients?

A simple /etc/exports file:
```
/D      lubuntu(rw,async,root_squash) romulus(rw,root_squash,async)
```
/D is the location, directory to be shared.
lubuntu & romulus are specific clients. The NFS server knows how to find them using those names - DNS or /etc/hosts.
The options are for read-write, async, and root on other systems don't have any special access - chown won't work.

The server name is istar. All the clients know how to fine it using that name.

On the client side, ```

sudo mkdir /D
sudo mount     -t nfs       -o proto=tcp,intr,rw,async,vers=3    istar:/D      /D
```

I strive to have NFS storage mounted in the same locations across all systems, even the NFS server.  This prevents my confusion.

That's pretty much it. Forcing NFSv3 probably isn't needed.  NFSv4 has much better security through Kerberos, if you want to configure it.  Also, v4 supports VPN-like encryption.

---

### Post by TheFu on 2019-12-06
If you want storage that is redundant, there are solutions.  NFS really isn't it.  If you use KVM + libvirt, something like sheepdog for the backend storage will handle replication with N nodes having the same block data. There's also CEPH and a few other options to block storage replication.

If I needed redundant storage for a cluster of VMs, I'd use sheepdog.

---


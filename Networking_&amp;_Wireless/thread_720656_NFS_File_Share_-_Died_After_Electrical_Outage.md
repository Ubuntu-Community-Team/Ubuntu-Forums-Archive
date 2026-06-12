---
title: "NFS File Share - Died After Electrical Outage"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by Ingla on 2008-03-10
Hello.

I have had file sharing (NFS) between to Linux boxes - One running Ubuntu Feisty and one Dapper.

Occasionally, sudden power outages have taken down the house and, of course, the computers.

When this happens, something gets killed in the network. I run through a list of commands on each box:

sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart
sudo gedit /etc/exports
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a
sudo /etc/init.d/portmap restart
/etc/init.d/nfs-common restart

REBOOT and then the share mounts on both machines

This time, an electric company worker cut power from outside to do some work and the results were worse. I lost my screen resolution, the GUI options for reboot and shutdown and, of course, file sharing.

Got the first two fixed, but the network is dead. 

_**On Feisty**_, I get:
mount to NFS server '10.0.0.2' failed: server is down.

_**On Dapper**_ it's:
mount to NFS server '10.0.0.139' failed.

I've run the usual commands and rebooted several times. No go. I can't find what's wrong.

Here are some outputs:

_**On Feisty**_ (IP 10.0.0.139) (10.0.0.2 is Dapper's IP):

rpcinfo -p 10.0.0.2
    rpcinfo: can't contact portmapper: RPC: Remote system error - No route to host
----------------------------------------------------------------------------------------------------------------------
rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  59605  nlockmgr
    100021    3   tcp  59605  nlockmgr
    100021    4   tcp  59605  nlockmgr
    100005    1   udp    860  mountd
    100005    1   tcp    863  mountd
    100005    2   udp    860  mountd
    100005    2   tcp    863  mountd
    100005    3   udp    860  mountd
    100005    3   tcp    863  mountd
    100024    1   udp  32771  status
    100024    1   tcp  60599  status
----------------------------------------------------------------------------
 exportfs -ra
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "10.0.0.2:/home/aba".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "10.0.0.3:/home/aba".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
---------------------------------------------------------------------------
_**On Dapper:**_

rpcinfo -p 10.0.0.139
No remote programs registered.
----------------------------------------------------------------------------
rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32768  nlockmgr
    100021    3   udp  32768  nlockmgr
    100021    4   udp  32768  nlockmgr
    100021    1   tcp  44970  nlockmgr
    100021    3   tcp  44970  nlockmgr
    100021    4   tcp  44970  nlockmgr
    100005    1   udp   1000  mountd
    100005    1   tcp   1003  mountd
    100005    2   udp   1000  mountd
    100005    2   tcp   1003  mountd
    100005    3   udp   1000  mountd
    100005    3   tcp   1003  mountd
    100024    1   udp    661  status
    100024    1   tcp    664  status
-------------------------------------------------------------------------------
exportfs -ra
exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
-------------------------------------------------------------------------------

_**It looks like the daemons are running. /etc/hosts.allow, /etc/hosts.deny, and /etc/hosts all look normal as far as I can recall.**_

_**I cannot ping Dapper from Feisty, but the other way around works.**_

Any ideas what could be wrong?

---

### Post by Eiríkr on 2008-03-10
Is your router borked?  Not being able to ping is a bit of a clue that there's more at issue than just NFS / RPC.  

Cheers,

Eiríkr

---

### Post by Ingla on 2008-03-10
As mentioned, I **can** ping from Dapper to Feisty - just not from Feisty to Dapper. The router seems to fulfill all of its other functions fine.

---

### Post by Eiríkr on 2008-03-10
I understand that pinging happens in one direction; my thought was that perhaps the router is malfunctioning on one of its ethernet ports.  Can both computers access the internet?  

Cheers,

Eiríkr

---

### Post by Ingla on 2008-03-10
> Can both computers access the internet? 

Yes.

---

### Post by Eiríkr on 2008-03-10
Any possibility it might be firewall settings, either on the individual machines or on the router?

---

### Post by Ingla on 2008-03-11
I'm not running a firewall except for Linux built-in protection. Sometimes ports need to be allowed in the router for various programs, but none of these settings has been changed . Everything was working before the power outage.

---


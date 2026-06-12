---
title: "mount: mount to NFS server '192.168.0.3' failed: System Error: Connection refused."
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by go_beep_yourself on 2008-04-08
That's the error I get. I am trying to mount a /home on nfs to /mnt/debian_home on the client computer.

```
[root@localhost ~]# mount -a
mount: mount to NFS server '192.168.0.3' failed: System Error: Connection refused.
[root@localhost ~]# 
```

Here are my configuration files on the client. I highlighted with red the two computers.

```
[root@localhost ~]# cat /etc/fstab
/dev/md0                /                       ext3    defaults        1 1
/dev/md2                /home                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/md1                swap                    swap    defaults        0 0
/dev/sda1               /mnt/sda1               ntfs-3g defaults        0 0
/dev/sdb1               /mnt/sdb1               ntfs-3g defaults        0 0
192.168.0.3:/home       /mnt/debian_home        nfs     rw,hard,intr    0 0
[root@localhost ~]# cat /etc/hosts*
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1       localhost.localdomain   localhost       localhost
::1     localhost6.localdomain6 localhost6
[COLOR="Red"]192.168.0.3     debian  debian-server[/COLOR]
#
# hosts.allow   This file contains access rules which are used to
#               allow or deny connections to network services that
#               either use the tcp_wrappers library or that have been
#               started through a tcp_wrappers-enabled xinetd.
#
#               See 'man 5 hosts_options' and 'man 5 hosts_access'
#               for information on rule syntax.
#               See 'man tcpd' for information on tcp_wrappers
#

portmap : 192.168.0.3
ALL:ALL
#
# hosts.allow   This file contains access rules which are used to
#               allow or deny connections to network services that
#               either use the tcp_wrappers library or that have been
#               started through a tcp_wrappers-enabled xinetd.
#
#               See 'man 5 hosts_options' and 'man 5 hosts_access'
#               for information on rule syntax.
#               See 'man tcpd' for information on tcp_wrappers
#
#
# hosts.deny    This file contains access rules which are used to
#               deny connections to network services that either use
#               the tcp_wrappers library or that have been
#               started through a tcp_wrappers-enabled xinetd.
#
#               The rules in this file can also be set up in
#               /etc/hosts.allow with a 'deny' option instead.
#
#               See 'man 5 hosts_options' and 'man 5 hosts_access'
#               for information on rule syntax.
#               See 'man tcpd' for information on tcp_wrappers
#
#
# The portmap line is redundant, but it is left to remind you that
# the new secure portmap uses hosts.deny and hosts.allow.  In particular
# you should know that NFS uses portmap!
#

portmap : ALL
#
# hosts.deny    This file contains access rules which are used to
#               deny connections to network services that either use
#               the tcp_wrappers library or that have been
#               started through a tcp_wrappers-enabled xinetd.
#
#               The rules in this file can also be set up in
#               /etc/hosts.allow with a 'deny' option instead.
#
#               See 'man 5 hosts_options' and 'man 5 hosts_access'
#               for information on rule syntax.
#               See 'man tcpd' for information on tcp_wrappers
#
#
# The portmap line is redundant, but it is left to remind you that
# the new secure portmap uses hosts.deny and hosts.allow.  In particular
# you should know that NFS uses portmap!
#
[root@localhost ~]# 
```

Here are my configuration files on the server.

```
chris@debian:~$ cat /etc/hosts
127.0.0.1 localhost debian
127.0.1.1 debian

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[COLOR="Red"]192.168.0.1 fedora-desktop[/COLOR]
chris@debian:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/home 192.168.0.1(rw,sync,subtree_check)
chris@debian:~$ 
```

Now I am trying to make it work.

```
chris@debian:~$ sudo /etc/init.d/nfs-kernel-server restart && sudo /etc/init.d/nfs-common restart && sudo /etc/init.d/portmap restart && sudo exportfs -ar
Stopping NFS kernel daemon: mountd nfsd.
Unexporting directories for NFS kernel daemon....
Exporting directories for NFS kernel daemon....
Starting NFS kernel daemon: nfsd mountd.
Stopping NFS common utilities: idmapd statd.
Starting NFS common utilities: statd idmapd.
Stopping portmap daemon....
Starting portmap daemon....
chris@debian:~$ 
```

```
[root@localhost ~]# mount -a
mount: mount to NFS server '192.168.0.3' failed: System Error: Connection refused.
[root@localhost ~]# 
```

```
[root@localhost ~]# !nmap
nmap -p 0-65535 debian-server

Starting Nmap 4.52 ( http://insecure.org ) at 2008-04-08 02:40 CDT
Interesting ports on debian (192.168.0.3):
Not shown: 65523 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
110/tcp  open  pop3
113/tcp  open  auth
139/tcp  open  netbios-ssn
143/tcp  open  imap
445/tcp  open  microsoft-ds
631/tcp  open  ipp
656/tcp  open  unknown
901/tcp  open  samba-swat
993/tcp  open  imaps
1310/tcp open  unknown
2049/tcp open  nfs
2226/tcp open  unknown
MAC Address: 00:A0:C9:A3:3A:05 (Intel - Hf1-06)

Nmap done: 1 IP address (1 host up) scanned in 2.961 seconds
[root@localhost ~]# mount -t nfs 192.168.0.3:/home /mnt/debian_home
mount: mount to NFS server '192.168.0.3' failed: System Error: Connection refused.
[root@localhost ~]# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  ns2.gvtc.com         anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns2.gvtc.com         anywhere            
ACCEPT     tcp  --  ns1.gvtc.com         anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns1.gvtc.com         anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             default             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.0.1         
INBOUND    all  --  anywhere             192.168.1.109       
INBOUND    all  --  anywhere             192.168.0.255       
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.109        ns2.gvtc.com        tcp dpt:domain 
ACCEPT     udp  --  192.168.1.109        ns2.gvtc.com        udp dpt:domain 
ACCEPT     tcp  --  192.168.1.109        ns1.gvtc.com        tcp dpt:domain 
ACCEPT     udp  --  192.168.1.109        ns1.gvtc.com        udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             default             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.0.2          anywhere            
ACCEPT     all  --  debian               anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:distinct 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:distinct 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:7881:7889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:7881:7889 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:http 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:27960:27969 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:27960:27969 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:quake 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:quake 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:sunrpc 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:sunrpc 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:nfs 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:nfs 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
[root@localhost ~]# 
```

---

### Post by bruban on 2008-04-08
It looks like a firewall problem.

I'm using shorewall to help configure my firewall on my Debian servers.

It appears that nfs uses dynamic ports.

This url should get you on the right track:

[http://lists.shorewall.net/~kb/action.AllowNFS](http://lists.shorewall.net/~kb/action.AllowNFS)

---

### Post by go_beep_yourself on 2008-04-08
> **bruban said:**
> It looks like a firewall problem.

I'm using shorewall to help configure my firewall on my Debian servers.

It appears that nfs uses dynamic ports.

This url should get you on the right track:

[http://lists.shorewall.net/~kb/action.AllowNFS](http://lists.shorewall.net/~kb/action.AllowNFS)

That's the firewall on the client. The server has no firewall because it's behind 2 firewalls/routers. The client is the second firewall providing nat to the server.

```
debian:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
debian:~# 
```

---

### Post by Eiríkr on 2008-04-08
What's the /etc/exports file on the server look like?  And do the UIDs match on your server and client, or are you mapping them somehow (mapping files, NIS, kerberos, etc)?

---

### Post by go_beep_yourself on 2008-04-08
> **Eiríkr said:**
> What's the /etc/exports file on the server look like?

Copied from above:

```
chris@debian:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/home 192.168.0.1(rw,sync,subtree_check)
chris@debian:~$
```

>   And do the UIDs match on your server and client,

The root uids match. My user ids do not match. Does that cause a problem? How? Are the other uids important?

> or are you mapping them somehow (mapping files, NIS, kerberos, etc)?

No.

---

### Post by Eiríkr on 2008-04-08
Samba authenticates based on usernames -- so if you log in with a username of "Fred", there must be an Ubuntu username "Fred" or the login will fail (I'm ignoring mapping here).  

NFS, meanwhile, authenticates based on UID.  So if you access a share with a UID of 1001, either you will see permissions within the share that apply to that UID, or if that UID has none, your access attempt might fail out.  

Have a look at the man page for exports, specifically the **User ID Mapping** section.  This is an excerpt:
> **nfsd** bases its access control to files on the server machine on the uid and  gid  provided in  each  NFS  RPC request. The normal behavior a user would expect is that she can access her files on the server just as she would on a normal file system. This requires that  the same uids and gids are used on the client and the server machine. This is not always true, nor is it always desirable.

Very often, it is not desirable that the root user on a client machine is also treated  as root  when  accessing  files on the NFS server. To this end, uid 0 is normally mapped to a different id: the so-called anonymous or **nobody** uid. This mode of operation (called  &#8216;root squashing&#8217;) is the default, and can be turned off with **no_root_squash**.

There's quite a bit more in that section that is probably relevant to your situation.  I'd also recommend that you read over [post=4387032]this post[/post], wherein I describe how to set up an NFS server with UID mapping in files (to avoid the complexities arising from either having to manually change UIDs on the server or client, or having to set up NIS).  The post also describes configuring Avahi to advertise the NFS shares, in case you happen to have a use for that.  

Cheers,

Eiríkr

---


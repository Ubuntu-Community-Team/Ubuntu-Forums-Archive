---
title: "NFS - server is down"
date: 2004-11-29
forum: Networking &amp; Wireless
---

### Post by Sintara on 2004-11-29
I have been wrestling with NFS and Ubuntu for about 20 hours now.  My network is as such:

192.168.1.1 -- DSL modem, has absolutely nothing to do with the network, except as a failsafe nameserver

192.168.0.1 -- D-Link DI-514 wireless router; I do not use wireless - I'm running the LAN  through the 4-port switch

192.168.0.2 -- Desktop machine running an up-to-date Ubuntu Warty installation; trying to export an NFS share from this machine

192.168.0.3 -- iBook; my primary production machine, because Macs are simply incredible

192.168.0.4 -- An older K6-2 machine running an up-to-date Fedora Core 3 installation; trying to export an NFS share from this machine

When trying to mount the Ubuntu share from the Fedora box, I get this:

[john@fedora-server ~]$ sudo mount -t nfs 192.168.0.2:/home/john /mnt/ubuntu-desktop
Password:
mount to NFS server '192.168.0.2' failed: server is down.

# /etc/exports
/home/john      192.168.0.0/255.255.255.0(rw,sync)

# /etc/hosts.allow
ALL:192.168.0.0/255.255.255.0

# /etc/hosts.deny
<No entries>

# /etc/default/portmap
ARGS=""

I'm running Firestarter with 192.168.0.3 and 192.168.0.4 as trusted hosts.  (I'll tighten config file security when everything is working correctly.)

When I try to mount the Fedora share, I get this:

mount: RPC: Unable to receive; errno = No route to host

None of my machines use DHCP for IP addressing.  My /etc/hosts file lists each of the computers' FQDN and hostname-only.

What's going on?  Why is this so complicated?  I know it shouldn't be, but things just aren't working out.  Should I switch to the non-kernel NFS server?  Would my problems disappear then, or is the root cause hidden elsewhere?

---

### Post by Sintara on 2004-11-29
Oh, yeah.  The appropriate services are running, as confirmed by rpcinfo -p.

---

### Post by Sintara on 2004-11-29
Well, Fedora's GUI firewall was the culprit behind my lack of access to Fedora's NFS share.  I've resolved that issue, and have achieved my primary goal.  Because I'm considering Ubuntu for a major project, however, it is important that I figure out the problem with Ubuntu.  Any ideas?

---

### Post by Magneto on 2004-11-29
[QUOTE=Sintara]Well, Fedora's GUI firewall was the culprit behind my lack of access to Fedora's NFS share.  I've resolved that issue, and have achieved my primary goal.  Because I'm considering Ubuntu for a major project, however, it is important that I figure out the problem with Ubuntu.  Any ideas?[/QUOTE]
 did you install portmap?

---

### Post by Sintara on 2004-11-29
Yup.  As far as I can see, there really is no reason for it not working.  I have a feeling there is some sort of security measure blocking it, because I've noticed that Ubuntu installed a tighter system than most Linux distributions I've worked with (and that's a lot).  It would be nice if there were an authoritative document discussing in detail the security features implemented and configured in the default installation.

---

### Post by Magneto on 2004-11-29
what does netstat -l show you? 
its just a matter or verifying every aspect necessary is enabled- something is not setup right

---

### Post by Sintara on 2004-11-29
Sorry it's not very easy to read, but here is the output of netstat -l.

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:2049                  *:*                     LISTEN
tcp        0      0 *:swat                  *:*                     LISTEN
tcp        0      0 *:smux                  *:*                     LISTEN
tcp        0      0 *:35176                 *:*                     LISTEN
tcp        0      0 *:sunrpc                *:*                     LISTEN
tcp        0      0 *:ftp                   *:*                     LISTEN
tcp        0      0 localhost.localdoma:662 *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
tcp        0      0 *:postgresql            *:*                     LISTEN
tcp        0      0 localhost.localdom:smtp *:*                     LISTEN
tcp        0      0 *:923                   *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN
tcp6       0      0 *:postgresql            *:*                     LISTEN
tcp6       0      0 ip6-localhost:smtp      *:*                     LISTEN
udp        0      0 *:2049                  *:*
udp        0      0 *:898                   *:*
udp        0      0 *:920                   *:*
udp        0      0 *:snmp                  *:*
udp        0      0 *:sunrpc                *:*
udp        0      0 *:32881                 *:*
udp        0      0 *:895                   *:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     13740    /tmp/orbit-root/linc-16f4-0-7214173827c0
unix  2      [ ACC ]     STREAM     LISTENING     13747    /tmp/orbit-root/linc-16f2-0-144f15713f2c
unix  2      [ ACC ]     STREAM     LISTENING     50239    /tmp/orbit-john/linc-298a-0-50b50bd9f1ea5
unix  2      [ ACC ]     STREAM     LISTENING     9339     /var/lib/backuppc/log/BackupPC.sock
unix  2      [ ACC ]     STREAM     LISTENING     10864    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     9391     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     16011    /tmp/orbit-john/linc-1812-0-359fb50fbbfd2
unix  2      [ ACC ]     STREAM     LISTENING     10288    public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     10295    private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     10299    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     10303    private/defer
unix  2      [ ACC ]     STREAM     LISTENING     10307    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     10311    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     10315    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     10319    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     10323    private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     10327    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     10331    public/showq
unix  2      [ ACC ]     STREAM     LISTENING     10335    private/error
unix  2      [ ACC ]     STREAM     LISTENING     10339    private/local
unix  2      [ ACC ]     STREAM     LISTENING     10343    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     10347    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     10351    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     10355    private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     10359    private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     10363    private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     10367    private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     10371    private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     10152    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     10437    /var/run/postgresql/.s.PGSQL.5432
unix  2      [ ACC ]     STREAM     LISTENING     10806    /var/run/apache2/cgisock
unix  2      [ ACC ]     STREAM     LISTENING     11027    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     11203    /tmp/ssh-tnHgcV5692/agent.5692
unix  2      [ ACC ]     STREAM     LISTENING     11217    /tmp/orbit-john/linc-166a-0-4757450844b4f
unix  2      [ ACC ]     STREAM     LISTENING     11226    /tmp/orbit-john/linc-163c-0-74a2d2e2482b6
unix  2      [ ACC ]     STREAM     LISTENING     11246    /tmp/.ICE-unix/5692
unix  2      [ ACC ]     STREAM     LISTENING     11252    /tmp/keyring-SYUXHV/socket
unix  2      [ ACC ]     STREAM     LISTENING     11259    /tmp/.esd/socket
unix  2      [ ACC ]     STREAM     LISTENING     11333    /tmp/orbit-john/linc-1671-0-235723175b80e
unix  2      [ ACC ]     STREAM     LISTENING     11375    /tmp/orbit-john/linc-1673-0-552f8dcad1d71
unix  2      [ ACC ]     STREAM     LISTENING     11746    /tmp/orbit-john/linc-1697-0-6d5e18ab44f1
unix  2      [ ACC ]     STREAM     LISTENING     11812    /tmp/orbit-john/linc-169f-0-14128c2189aed
unix  2      [ ACC ]     STREAM     LISTENING     11829    /tmp/orbit-john/linc-16a3-0-14128c2196a45
unix  2      [ ACC ]     STREAM     LISTENING     11894    /tmp/orbit-john/linc-16a1-0-42c6627c4b1a8
unix  2      [ ACC ]     STREAM     LISTENING     11936    /tmp/orbit-john/linc-16a9-0-42c6627cdba3a
unix  2      [ ACC ]     STREAM     LISTENING     12028    /tmp/orbit-john/linc-16ae-0-4f2b0593d2703
unix  2      [ ACC ]     STREAM     LISTENING     12103    /tmp/mapping-john
unix  2      [ ACC ]     STREAM     LISTENING     12226    /tmp/orbit-john/linc-16bc-0-d0ec47ce5253
unix  2      [ ACC ]     STREAM     LISTENING     12353    /tmp/orbit-john/linc-16be-0-7be68c47cefe1
unix  2      [ ACC ]     STREAM     LISTENING     12415    /tmp/orbit-john/linc-16c5-0-29336922b53a5
unix  2      [ ACC ]     STREAM     LISTENING     12448    /tmp/orbit-john/linc-16c7-0-171832f648c3c
unix  2      [ ACC ]     STREAM     LISTENING     12488    /tmp/orbit-john/linc-16cb-0-171832f6abbc0
unix  2      [ ACC ]     STREAM     LISTENING     12521    /tmp/orbit-john/linc-16cd-0-45d622162db9a

---

### Post by Magneto on 2004-11-30
2049 is nfs so it seems to be listening

username and passwords setup right?

You installed nfs-common?

what does "nfsstat -s" say?


Hey you're trying to mount from a Fedora box right?
try nfsvers=2 or =3


mount -o nfsvers=2 192.168.1.2:/home

---

### Post by Sintara on 2004-11-30
A double-check of installed NFS software revealed that I have nfs-user-server installed, not nfs-kernel-server.  I'm going to swap them out to see if that resolves the issue.  If that fails, I'll provide you with the information you requested in your last post.  Thanks for your help, by the way.

---

### Post by Sintara on 2004-11-30
nfs-user-server was installed as a dependency of replicator.  I swapped the nfs server software, installing nfs-kernel-server, and the issue is resolved.  I can now mount and access the Ubuntu share from the Fedora machine.  Now I just need to figure out why my Mac isn't mounting the share.  But that's a Mac issue, and so I will take care of it through other support channels.  Magneto, you were a great help.  Thanks a lot!

---


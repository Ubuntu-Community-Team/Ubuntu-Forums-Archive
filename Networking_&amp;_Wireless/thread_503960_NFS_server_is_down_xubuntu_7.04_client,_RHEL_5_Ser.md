---
title: "NFS server is down? xubuntu 7.04 client, RHEL 5 Server"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by Steelangel on 2007-07-18
I'm trying to mount a drive from my server (RHEL 5 x86_64) to my workstation (xubuntu 7.04 i386). I've tried to google the answer, yet there doesn't seem to be any that seems to work for me. I'm coming from a background working with Red Hat primarily. I'm quite the noob at the specifics of this distro, so I may be missing something obvious. 

I have installed portmap, nfs-common and nfs-kernel-server on the xubuntu box. 

Here's the terminal:
[INDENT]>sudo mount -t nfs supernova:/data /supernova/data
Password:
mount to NFS server 'supernova' failed: server is down.[/INDENT]

Here's the hosts file on the client: 
[INDENT]127.0.0.1 localhost
<IP Address 1> antares.phys.ut.edu antares
<IP Address 2> supernova.phys.ut.edu supernova

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/INDENT]

The server's hosts file: 
[INDENT]127.0.0.1 localhost
<IP address 1> antares.phys.ut.edu antares
<IP address 2> supernova.phys.ut.edu supernova
::1 localhost6.localdomain6 localhost6[/INDENT]

The Server has in it's hosts.allow:
[INDENT]portmap mountd nfsd statd lockd rquotad : <IP address 1> <IP address 2>[/INDENT]

And hosts.deny
[INDENT]portmap mountd nfsd statd lockd rquotad : ALL[/INDENT]

The server is exporting exactly one directory: 
[INDENT]/data antares(rw,no_root_squash)[/INDENT]

I realize that no_root_squash is a bad option to have, but I need to allow access by the system administrator. 

I know that NFS is running on the server, it's sitting in my office. There's got to be something that I am completely missing

---

### Post by dougfractal on 2007-07-18
Is the server UDP or TCP?
nfsver3?

I have a debian NFS server to ubuntu clients, and I've not found ubuntu to have any problems, because at heart  is a debian system, so check out debian admin howtos.

---

### Post by Steelangel on 2007-07-19
I'm pretty sure that the server is NFS v4, although even 
[INDENT]> mount -o nfsvrs=3 server:/data /data[/INDENT]
still gives me the same answer: Server is down. 

It's running under TCP - 

From netstat -l (on the server)

[INDENT]# netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address               Foreign Address             State      
tcp        0      0 localhost.localdomain:2208  *:*                         LISTEN      
tcp        0      0 *:nfs                       *:*                         LISTEN      
.
.
.  
udp        0      0 *:nfs                       *:*                                     
.
.
.                              
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
.
.
.[/INDENT]

Since the server is not a Debian-based system (it's Red Hat Enterprise) I don't think that debian admin docs are going to help. I can easily mount any shared directory on the ubuntu system to the RHEL system, so it has to be something on the server.

---

### Post by dougfractal on 2007-07-19
```
mount -o nfsvers=3,tcp server:/data /data
```

is there a typo in nfsvrs=3?

your exportfs looks more nfsv3 than v4

[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-nfs-client-config.html#S2-NFS-CLIENT-CONFIG-OPTIONS](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-nfs-client-config.html#S2-NFS-CLIENT-CONFIG-OPTIONS)
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-nfs-server-export.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-nfs-server-export.html)

---

### Post by Steelangel on 2007-07-20
Yes, that was a typo when I typed it into the post, it should be nfsvers. Even with the correct option, the server will not connect. 

I can connect the server to it's own NFS mounts, if that's worth anything. So there has to be some sort of issue with the server not wanting to talk to anyone else.

---

### Post by dougfractal on 2007-07-20
Just to clearify, xubuntu is "<IP Address 1> antares.phys.ut.edu antares"?
and xubuntu can ```
ping -c 4 supernova 
``` is fine?

---


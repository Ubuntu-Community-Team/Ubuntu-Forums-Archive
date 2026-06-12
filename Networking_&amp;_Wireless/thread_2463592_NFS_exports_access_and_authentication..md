---
title: "NFS exports access and authentication."
date: 2021-06-14
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-06-14
We don't use NFS and haven't for a long time since all of the clients are Windows. We use SAMBA for file sharing.
I have used NFS in the distant past when we ran a number of SUN and other Unix workstations, but it's been years and I've forgotten much and NFS has evolved.

I have recently considered using NFS to share files between servers and had a question about default NFS access.

Does Ubuntu NFS limit access to an exported file system in any way?
Does Ubuntu NFS require user authentication to access an exported directory?

For example, who could access this file:

```
/file *(rw,sync)
```

Would this require the user to be a actual system user?

Is there a ufw command to limit access to the local network?

---

### Post by SeijiSensei on 2021-06-14
Authentication is usually handled by the normal *nix mechanisms like /etc/passwd.  I export a /home share from my server and mount it to a separate mount point on client.  Both the export and the mount are handled by the root user.  However access to the directories in the mounted share depends on their ownership.  I can look at the directories owned by my user on the server, but not other directories unless I'm granted group access.

In my setup the user IDs and group IDs are identical across the server and client.  Remember that what matters are the user ID numbers not the textual names.  So user 1000 on the client will have access to the exported files on the server to which user 1000 also has access.

In the case you present, it would depend on the ownership of /file on the server. 

And, yes, mounts can be made by ordinary users, but a better practice is to mount the shares by root via /etc/fstab when the server boots.

If you're thinking about transferring files for backup purposes, rsync is a better tool.  I run a script each night that uses rsync to suck down the variable files on my cloud servers.

---

### Post by TheFu on 2021-06-14
> **rsteinmetz70112 said:**
>  
Does Ubuntu NFS limit access to an exported file system in any way? 
Yes. Multiple ways, but mostly it provides access to a file system that behaves like a local mounted file system, except in a few ways, which can be controlled by the exports file.  Also, by default, only the root account on the server where the storage is actually attached has root authority. There is an override for this, but it is poor security, especially in a poorly networked setup with mixed clients.

> **rsteinmetz70112 said:**
>  
Does Ubuntu NFS require user authentication to access an exported directory?
 
NFS is server-to-server, not user-to-server.  NFS v3 and v4 use IP addresses to determine access by default.  If you allow the entire LAN access, then there won't be any restrictions.

NFSv4 added both Kerberos and strong encryption - both are optional.  The Kerberos would be server-to-server authentication.  I've never used it.  Dynamic DHCP addresses on our networks don't get NFS access.  In my world, only specific machines are provided with an export config and the LAN firewall prevents NFS access from the wrong subnets.  We don't allow subnet-based exports. That's a policy violation just like allowing remote root is a policy violation.

The NFSv4 encryption is considered sufficiently strong to be used over the internet, though I'd only allow read-only access regardless.

For a userid on a client machine to access an NFS directory, the normal directory and file permissions have to allow the access required.  Chmod, chown, chgrp are used for that.  Without centralized userid and groupid management, NFS can be a hassle.  The numbers (uid/gid) on the server and clients really need to match to prevent undesirable outcomes.  Forget usernames. Those don't matter. It is the numbers that count.  The idmapd daemon doesn't do what people want it to accomplish.  It won't fix incorrect uid/gid mappings. It just fixed the displayed username and groupnames, nothing more.  The best practice is to use LDAP for POSIX user/group management, then uid/gid all align for the most likely NFS usernames.

---

### Post by rsteinmetz70112 on 2021-06-15
> NFSv4 added both Kerberos and strong encryption - both are optional.

How does one invoke encryption on an NFS share? Is that an /etc/exports option or is it through ssh port forwarding?
All of the examples I've looked at show Kerberos.

---

### Post by TheFu on 2021-06-15
> **rsteinmetz70112 said:**
> How does one invoke encryption on an NFS share? Is that an /etc/exports option or is it through ssh port forwarding?
All of the examples I've looked at show Kerberos.

I don't know. Never done that myself.  Only know from reading - years ago.

---


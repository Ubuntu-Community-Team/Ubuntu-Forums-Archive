---
title: "What's my domain name?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by bob12 on 2007-10-25
I'm setting up a small home LAN and have no idea where my domain name is or if I even have one.

I need it to set up local file sharing using NFS so I'm assuming I just need my local LAN domain name.

Where can I find it?

If I don't have one, and I think I don't, how do I set it and where do I find it after that?

Thanks

---

### Post by fain on 2007-10-25
You need to set up a bind server to have a local domain. So i assuming you dont have bind configured therefore you do not have a domain name.

you dont need a nameserver for NFS. all you need is the package nfs-kernel-server nfs-common 
and portmap and the ip of the machine with the share.

edit the file /etc/exports
and add your share in there

when you want to access it you need to mount it with the pc you want to access it with by, ip address no need for a name server.

this how to for gutsy nfs will give you more details
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server")

---

### Post by bob12 on 2007-10-26
Thanks very much, that did the trick.

---


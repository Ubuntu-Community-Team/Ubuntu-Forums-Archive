---
title: "Unsolvable dropouts with NFS"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by spauldingsmails on 2008-09-04
I've got NFS set up on my file server with two mounts set up; the user's home directory and a shared directory.

/etc/fstab
```

192.168.5.1:/home/haydeny /media/<userhome> nfs rsize=8192,wsize=8192,timeo=14,intr,nolock
192.168.5.1:/home/shared /media/shared nfs rsize=8192,wsize=8192,timeo=14,intr,nolock

```

The server's /etc/exports

```
/home 192.168.5.1/24(rw,sync,no_root_squash,no_subtree_check)

```

The issue is that I constantly get dropouts, especially if playing music on the client via Amarok, with the following error showing up in the client's /var/log/messages;

```
nfs: server 192.168.5.1 not responding, still trying
```

This can go on for minutes, but will always eventually recover. The server logs no errors that I know about.

So far I can't find any answers about how to diagnose or fix the problem. Even when this is going on I can still ssh, browse web pages served by the machine and Samba shares without problem.

The only thing I can think of is that my wireless connection is causing problems, as I've heard NFS is not good at handling connection dropouts and errors.

Has anyone experienced this issue and successfully resolved it or am I better off moving to Samba? I was thinking about having all client machine's /home directories exported by nfs but am not about to with this problem occurring.

Any help much appreciated.

---

### Post by spauldingsmails on 2008-09-19
Well it seems I was able to solve the problem by specifying udp instead of tcp in my fstab;

```

192.168.5.1:/home/haydeny /media/<userhome> nfs rsize=8192,wsize=8192,timeo=14,intr,nolock,udp
192.168.5.1:/home/shared /media/shared nfs rsize=8192,wsize=8192,timeo=14,intr,nolock,udp

```

Not sure why this works but it's solved the dropout/freeze problem. Maybe it's something to do with the statelessness of the tcp connection, but perhaps someone can shed more light on it.

---


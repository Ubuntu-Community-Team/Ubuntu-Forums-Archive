---
title: "NFS Trouble"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2008-07-28
I'm running Ubuntu 8.04 on my server (192.168.1.37) and Debian Sid on my client (192.168.1.29). The server responds to ping from the client.

I have nfs-kernel-server, nfs-common, and portmap installed on the server. I had NFS working fine with this server and another client, so I didn't change anything on it except the IP address in /etc/exports to match the current client. Then, I restarted nfs-kernel-server and portmap.

On the client machine, I made a directory /nfs, then ran the command
```

mount 192.168.1.37:/home/daniel /nfs

```

I got this error message
```

mount.nfs: mount to NFS server '192.168.1.37' failed: timed out, retrying

```

What isn't set up right?

---

### Post by Ayuthia on 2008-07-28
> **dbbolton said:**
> I'm running Ubuntu 8.04 on my server (192.168.1.37) and Debian Sid on my client (192.168.1.29). The server responds to ping from the client.

I have nfs-kernel-server, nfs-common, and portmap installed on the server. I had NFS working fine with this server and another client, so I didn't change anything on it except the IP address in /etc/exports to match the current client. Then, I restarted nfs-kernel-server and portmap.

On the client machine, I made a directory /nfs, then ran the command
```

mount 192.168.1.37:/home/daniel /nfs

```

I got this error message
```

mount.nfs: mount to NFS server '192.168.1.37' failed: timed out, retrying

```

What isn't set up right?

Do you have portmap and nfs-common installed on the client?

---

### Post by dbbolton on 2008-07-28
> **Ayuthia said:**
> Do you have portmap and nfs-common installed on the client?
Yeah

---

### Post by dbbolton on 2008-07-30
Found the problem- Firestarter. It was running in the background. I just had to stop it to mount the shared folder.

---


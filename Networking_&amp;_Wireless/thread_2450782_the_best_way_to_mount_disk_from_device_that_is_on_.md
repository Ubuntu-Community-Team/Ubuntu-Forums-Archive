---
title: "the best way to mount disk from device that is on wifi connection"
date: 2020-09-20
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2020-09-20
Hi all, 
Looking for the best way to mount disk from device that is on wifi connection. 

Usually I just run mc file manager and connect it using ssh; I have shortcut in mc for this path and also authorize using ssh key, so it is more or less convenient. But as the device is on wifi connection, it can break in the middle of big file transfer and it doesn't allow to continue uploading, so I need to repeat it from scratch. 

Now I'm trying sshfs and the connection also breaks, also uploading speed is extremely low, don't understand why.

Maybe there is another modern way to mount it, please advise.

Upd: testing FileZilla for now.

---

### Post by TheFu on 2020-09-20
> **marchello_lippi2 said:**
> Hi all, 
Looking for the best way to mount disk from device that is on wifi connection. 

The best answer is to use a wired ethernet connection. The faster, the better.  Everything else is a hack for flaky connections.

> **marchello_lippi2 said:**
> Usually I just run mc file manager and connect it using ssh; I have shortcut in mc for this path and also authorize using ssh key, so it is more or less convenient. But as the device is on wifi connection, it can break in the middle of big file transfer and it doesn't allow to continue uploading, so I need to repeat it from scratch. 
Use rsync for a protocol that picks up quickly after failures. rsync uses ssh connections by default the last 15 yrs, so if ssh is the authentication method available, the traffic will be encrypted. This is not a "mount", just a transfer.

> **marchello_lippi2 said:**
> Now I'm trying sshfs and the connection also breaks, also uploading speed is extremely low, don't understand why.
sshfs uses ssh encryption. That has overhead for both sides of the connection.

> **marchello_lippi2 said:**
> Maybe there is another modern way to mount it, please advise.

Upd: testing FileZilla for now.

If you want a mount, use NFS with a read-only connection and force tcp to be used. 
If you need security with the NFS mount (and wifi should never be trusted), use NFSv4 with Kerberos system-to-system authentication and AES encryption. I think there is a 'how-to' to do this in the Ubuntu Server Guide.

---


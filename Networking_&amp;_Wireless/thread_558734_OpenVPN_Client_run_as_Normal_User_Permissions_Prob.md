---
title: "OpenVPN Client run as Normal User Permissions Problem?"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by squibs on 2007-09-24
Hi All, 

Apologies if I get any terminology wrong. 

I have a working OpenVPN Server (Ubuntu 7.04) which the client (Ubuntu 7.04) can connect to if OpenVPN on the client is run using sudo.

CODE]sudo  openvpn --config client.conf[/CODE]

If I run it as the normal user with the following:

```
 openvpn --config client.conf
```

I get the following output:

```
Mon Sep 24 15:51:19 2007 OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] built on Mar  2 2007
Mon Sep 24 15:51:19 2007 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Mon Sep 24 15:51:19 2007 Control Channel Authentication: using 'x' as a OpenVPN static key file
Mon Sep 24 15:51:19 2007 LZO compression initialized
Mon Sep 24 15:51:19 2007 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Mon Sep 24 15:51:19 2007 Attempting to establish TCP connection with xxx.xxx.xx.xxx:xxxx
Mon Sep 24 15:51:19 2007 TCP connection established with xxx.xxx.xx.xxx:xxxx
Mon Sep 24 15:51:19 2007 TCPv4_CLIENT link local: [undef]
Mon Sep 24 15:51:19 2007 TCPv4_CLIENT link remote: xxx.xxx.xx.xxx:xxxx
Mon Sep 24 15:51:20 2007 [Tranquility] Peer Connection Initiated with xxx.xxx.xx.xxx:xxxx
Mon Sep 24 15:51:22 2007 Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Mon Sep 24 15:51:22 2007 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Mon Sep 24 15:51:22 2007 Cannot allocate TUN/TAP dev dynamically
Mon Sep 24 15:51:22 2007 Exiting
```

So firstly, can I run this as a Normal user or must it be run as root.

And then if it can be run as a normal user how can I get it to run?

The error message to me reads that the permissions on /dev/net/tun mean that the normal user can't access the the device tun?

The permissions are:

```
crw-rw---- 1 root root 10, 200 2007-04-15 12:49 /dev/net/tun
```

If this is correct I'm not sure what I need to change them to?

many thanks in advance

Ads

---

### Post by *Legion* on 2007-11-08
I have this same problem. But it's worse than that.

If you chmod /dev/net/tun to give user permissions, you get past the first error, and get this instead:
> Note: Cannot ioctl TUNSETIFF tap: Operation not permitted (errno=1)

Still some permissions problem, changing the permissions of /dev/net/tun isn't enough.

---

### Post by samosamo on 2008-01-05
bump this !

---

### Post by samosamo on 2008-01-21
another bump

---

### Post by glibdud on 2008-06-03
Sorry to resurrect this one, but I'm having the same issue, and there doesn't seem to be a solution yet.

It connects if I sudo it, but gives the permission error from the original post if I try to run it as the normal user, and the TUNSETIFF error from post 2 if I chown /dev/net/tun to the user's permissions.

---


---
title: "DHCP release"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by lfaraone on 2008-05-31
My ISP requires that I either call them to break the lease or release my IP address before changing my computer's MAC address (like plugging another computer in).

How can I tell (K|X|Ed)ubuntu to release the DHCP release when it shuts down, or does this happen automagically?

---

### Post by NilsE on 2008-05-31
DHCLIENT is the tool. In a terminal run:

sudo dhclient -r

Here is the excerpt from the man page for dhclient

The  client  normally  doesn’t  release  the current lease as it is not required by the DHCP protocol.  Some cable ISPs require  their  clients to  notify  the  server if they wish to release an assigned IP address. The -r flag explicitly releases the current lease, and once  the  lease has been released, the client exits.

---

### Post by lfaraone on 2008-05-31
> **NilsE said:**
> sudo dhclient -r
Thanks!

Ok, any way to have it do that automagically on poweroff?

---


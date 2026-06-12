---
title: "Mounting a folder securly across the internet"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by Yoooder on 2007-09-24
I've been trying to find a solution for the following situation:

I have a laptop that I use in the office, and it must run Windows.  I have a server with a public IP address that acts as my network's fileserver.  I would like to be able to map a folder from the server to my laptop across the internet without having to VPN (so as to maintain my local network access).

Ideally I'd like to use SSH as the transport protocol.  I've looked into shfs and its kin but have not found a win32 client.

Does anyone know of a utility for this?

---

### Post by Yoooder on 2007-09-24
I've found a possible solution using putty's port-forwarding and Samba.

[http://blisstonia.com/eolson/notes/smboverssh.php]("http://blisstonia.com/eolson/notes/smboverssh.php")

Any other suggestions though?

---


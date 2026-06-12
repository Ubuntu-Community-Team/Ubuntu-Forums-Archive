---
title: "systemd-resolved changes not &quot;sticking&quot;"
date: 2024-01-03
forum: Networking &amp; Wireless
---

### Post by sbonar on 2024-01-03
HELP!!  I don't know what I'm doing wrong and if someone could point me in the correct direction that would be great.

I am setting up a TUN interface and then I am setting a per interface DNS server on it but it appears that almost immediately something is calling revert and wiping my changes.  

I've used both resolvectl and busctl to do this but it does not seem to matter what I do. 

Any help is appreciated.

---

### Post by sbonar on 2024-01-22
I am still having this issue so any help would be appreciated.  Once I set the DNS servers on my TUN interface something in the system is reverting it back to the primary interface.

Here is the debug log output from systemd-resolved and NetworkManager

[https://paste.ubuntu.com/p/gfbMFZzf5Q/](https://paste.ubuntu.com/p/gfbMFZzf5Q/)

---

### Post by sbonar on 2024-01-23
Going to mark this as resolved since I found the culprit.  Another service was monitoring busctl and because our two services overlap in our networking address space it was the one removing my DNS settings.
Disabling the service "fixed" my issue.

---


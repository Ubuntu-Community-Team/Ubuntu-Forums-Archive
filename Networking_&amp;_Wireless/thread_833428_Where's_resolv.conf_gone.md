---
title: "Where's resolv.conf gone?"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by randysparks on 2008-06-18
Ubuntu Hardy doesn't appear to have /etc/resolv.conf. What's taken its place if I want to configure a network connection's DNS at the command-line?

It still works if I create one from scratch, but I'd rather do this the official way. :)

---

### Post by chili555 on 2008-06-18
It isn't there until either DHCP gets nameserver addresses, or, if you prefer static IP addresses, from System->Admin->Network. Of course, if you are a hard-core terminal freak, then it's created with vim.

---


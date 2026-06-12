---
title: "likewise open domain trust failed"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by freemant on 2008-06-03
Hi,

I've setup likewise open on Ubuntu server edition 8.04.
My DC is a Windows 2003 server. After setting it up,
it seemed to work fine. I could login to it using ssh 
with an AD account and could access its shared folder 
from a Windows client.

However, a few days later (now) I can no longer access
the shared folder from the same Windows client. It
states "The trust relationship between this workstation 
and the primary domain failed". Generally this error 
means the computer account of the file server (Ubuntu)
is incorrect. So I left the domain and joined again
(also tried deleting the computer account). But it made 
no difference. However, I can still ssh using an AD account. 
Similarly, "lwiinfo -u" still works (can list all the AD 
users).

Any idea?

---


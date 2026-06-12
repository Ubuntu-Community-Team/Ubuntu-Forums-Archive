---
title: "restricting internet access on a user group"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by catech on 2007-07-21
Hi,

I have Ubuntu 7.04 Feisty Fawn. I have set up Samba as a PDC. The clients use This machine to resolve DNS.

I want to allow all users to access 1 account, and users who are in the managers group to have full access to the internet. If Non-managers tried to access a disallowed site I want a page to appear advising that they are restricted.

All client machines are WinXP/2K.

Can anyone help with this? I've tried googleing, and searching various forums

James

---

### Post by Koybe on 2007-07-21
Maybe I'm wrong, but I think this as nothing to deal with samba but with a firewall. Is your server also the router and the way out to the internet?

---

### Post by catech on 2007-07-21
I have a draytek router, which assigns ip addresses, the draytek is the gateway, and it assignes the servers ip as the DNS. I can however change the setup to resolve this issue

---

### Post by Koybe on 2007-07-21
If you can change everything should be possible. But I'm not good enough in firewalling to guide you trough a user filtering.

---


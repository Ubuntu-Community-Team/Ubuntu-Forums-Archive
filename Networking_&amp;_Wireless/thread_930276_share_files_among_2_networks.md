---
title: "share files among 2 networks"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by johnbravado on 2008-09-25
i have a main ubuntu router with samba 192.168.2.X i have a linksys wireless router connected to the 4 port switch coming out of the uu=buntu box which dhcps 192.168.1.X. hiw can i file share between the 2 networks? i dont see anywhere in samba where ot set up ip adresses allowed in the wins server

---

### Post by cariboo on 2008-09-25
What happens when you manually try to mount a share eg:

```
sudo mount //192.168.1.X/share /mdeia/share
```

To mount a share manually you have to have smbfs installed

You can also do the same thing using nautilus in the location bar, if you don't see the location bar hit the toggle but at the far left to change between a button and text.

Jim

---


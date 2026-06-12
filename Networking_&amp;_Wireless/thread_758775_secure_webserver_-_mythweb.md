---
title: "secure webserver - mythweb"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by ushills on 2008-04-18
I have a fairly simple networking question and need some advice.

I currently have 3 machines

1. Mythbuntu, running mythweb
2. Main house PC. I SSH into this one.
3. Xubuntu PC

All of the PC's attach to a router and I can port forward from this machine to the various PC's.

What I would like to do is be able to access PC 1 from the internet outside my home network, be able to SSH to PC 1 from machine 2 or 3 and use VNC to administer.

I also use NFS to access music and photo on PC 2 from PC 1.

Do this without compromising my networks security as I will have port 80 forwarding to PC 1.

How can I do this?

---

### Post by HermanAB on 2008-04-18
Configure SSH in /etc/ssh/sshd_config to run on a non-standard port, eg. 2222 and disable root password login.  Forward port 2222 in your router.  If you use SSH, then VNC is redundant.

Cheers,

Herman

---

### Post by zukakog on 2008-05-07
> **HermanAB said:**
> If you use SSH, then VNC is redundant.

Well, if he's using a Linux box, he can do ssh user@host -X to be able to run programs in a GUI. But, if he's on a Windows box, and wants to administer in a GUI, VNC is not redundant.

---


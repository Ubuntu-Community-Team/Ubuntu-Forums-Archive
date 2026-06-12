---
title: "Setting up a Samba Share for a external node"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by Dale_Snowdon on 2016-04-28
I have a VPS and I would like to mount a folder to my computer. How can this be done via SAMBA, I have created the share, now what must I do?

Create Port Forwards ? If so what

Thanks in advance for any input

---

### Post by bab1 on 2016-04-28
> **Dale_Snowdon said:**
> I have a VPS and I would like to mount a folder to my computer. How can this be done via SAMBA, I have created the share, now what must I do?

Create Port Forwards ? If so what

Thanks in advance for any input
You will not be able to use a Samba share (SMB/CIFS)  directly via the Internet.  The Samba TCP ports are blocked by most ISP's.  You will need to use a VPN to connect to your VPS  to use Samba.

---

### Post by Dale_Snowdon on 2016-04-28
Im trying to connect to home computer to my vps, and it worked! I just needed to add a samba password to a user.

---


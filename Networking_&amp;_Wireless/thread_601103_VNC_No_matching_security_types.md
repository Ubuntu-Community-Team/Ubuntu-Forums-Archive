---
title: "VNC No matching security types"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by LAF4SENS on 2007-11-02
Hi,

I'm trying to access my windows pc with VNC from my ubuntu pc.

My 2 windows pc has VNC server running.

I try :

vncviewer 192.168.2.104

and I get this error:

No matching security types


What am I doing wrong?

Thanks for the answers,

Marc

---

### Post by howefield on 2007-11-03
I've just had the same issue, found the following which fixed it for me.

If you set your server to use VNC Authentication and the server's Encryption
setting to Prefer On in order for RFB 3.3 clients to be able to connect.

---


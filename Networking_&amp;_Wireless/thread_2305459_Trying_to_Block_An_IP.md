---
title: "Trying to Block An IP"
date: 2015-12-06
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2015-12-06
I'm trying to block this IPv4 address.  Yet as you can see it's been blocked!  I've used  "sudo ufw deny from 5.9.123.81" and "iptables -A INPUT -s 5.9.123.81 -j DROP" yet it's still there everyday!  Is there something else I could use or maybe the're not actually not getting in and just persitent!?!?!?

Also I can't get the port blocked!  What could I be doing wrong?

---

### Post by matt_symes on 2015-12-06
Hi

```
sudo iptables -A OUTPUT -d 5.9.123.81 -j DROP
```

?

I don't use ufw from the command line.

**EDIT:**

You can copy and paste output from the terminal into posts you make as opposed to attaching images.

Wrap the output in code tags like so.

[noparse]```

```[/noparse]

Kind regards

---

### Post by shane_faulkinbury2 on 2015-12-06
Thanks Matt!

---


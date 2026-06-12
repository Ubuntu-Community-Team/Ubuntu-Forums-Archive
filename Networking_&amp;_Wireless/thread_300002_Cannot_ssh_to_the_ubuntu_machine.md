---
title: "Cannot ssh to the ubuntu machine"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by mesh2005 on 2006-11-15
I installed the openssh-server on my ubuntu machine, I started the sshd and I tested using ssh localhost and it worked.
I tried to ssh to the ubuntu mahcine from any other machine on the network but I got "Connection Timeout", can you explain why?
Thank you

---

### Post by marekdef on 2006-11-15
Do sth like this
# netstat -anlpt | grep sshd
tcp6       0      0 :::22                   :::*                    LISTEN     5193/sshd

See if sshd is listening on 22 port and interface you try to connect to.
Are you using any firewall system?

---

### Post by mesh2005 on 2006-11-15
I did that and yes the sshd is listening on port 22. I think the Linux firewall is enabled, is that a problem?

---

### Post by mesh2005 on 2006-11-15
I think it is related to the firewall, I stopped it then the ssh worked. How can I configure the firewall to allow ssh?

---

### Post by mesh2005 on 2006-11-15
I found it, I used firestarter to add a rule to allow the SSH service. How can I do it without firestarter?
Thank you

---

### Post by FrodoB on 2006-11-15
I am on a machine that just completed a 6.06 install and the firewall is not on it. You evidently got it when you installed firestarter maybe?

---


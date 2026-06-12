---
title: "vpnc: binding to port 500: Permission denied"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by spyke01 on 2007-01-16
Hi guys, i was trying to get networkl manager and vpnc working together, however i need to find a way to get vpnc working correctly without doing
```

sudo vpnc

```

if you dont do that youll get this error:
```
vpnc: binding to port 500: Permission denied
```

any ideas?

---

### Post by Rippey on 2007-01-16
if I'm not mistaken all ports below 1023 are so called privileged ports that only root can bind to. in other words vpnc will need some sort of root privileges to bind to port 500.
a workaround would be to let it use a port above 1023.

---

### Post by spyke01 on 2007-01-16
is there any way to change network-manager to do this?

---

### Post by Rippey on 2007-01-17
I'm not sure, I haven't got any experiance with network-manager, but my guess is that you could change the port vpnc uses in your vpnc settings.

---

### Post by jkernsjr on 2007-01-18
I have been working for the last 4 or 5 hours on this same issue and after all of that I wasn't reading the dialog box correctly!!!!

I installed vpnc and NetworkManager from the repos. Then I found the vpnc NetworkManager plugin here [http://www.linux2go.dk/ubuntu/pool/main/n/network-manager-vpnc/](http://www.linux2go.dk/ubuntu/pool/main/n/network-manager-vpnc/). First make sure you can get connected by using sudo vpnc. Then when you get the vpnc plugin installed in NetworkManager and set up your connection information, pay careful attention to the Password dialog box. I was incorrectly filling out both boxes with the same password instead of actually reading what I was supposed to put in them. After I put my network password in the first box and the VPN password in the second box, all worked great.

---


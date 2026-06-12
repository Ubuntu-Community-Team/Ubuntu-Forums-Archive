---
title: "Getting Winbind and NetworkManager play nicely together?"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by ltmon on 2006-10-15
Hi All,

I love NetworkManager as I change from wired to wireless and change networks quite often in my job.

I also love winbind/nmb because it allows me to refer to all the Windows servers in my environment by netbios name, rather than having to remember IPs.

Unfortunately I can't seem to get the two playing well together.

In my /etc/samba/smb.conf I have to configure this line to get winbind working correctly:
```

interfaces = <list of either ip addresses or interface names (e.g. eth0) go here!>

```
If I use an IP address in this line it works fine, but my IP address keeps changing with the network I'm on and also with new DHCP leases, so I need to reconfigure and restart samba each time I get a new IP.

If I use an interface (i.e. eth0 for wired and eth1 for wireless) it works fine, but samba doesn't start up unless that interface is active.  So "eth0" works when I'm on a wired network and "eth1" works when I'm on wireless, but when I put both in the list of interfaces ("eth0 eth1") samba wont start up.  I can't find any log entries as to why this might happen.

So what I'm looking for is a way to move around networks without having to reconfigure and restart samba every time my interface or ip changes.

Any tips?

Thanks,

L.

---


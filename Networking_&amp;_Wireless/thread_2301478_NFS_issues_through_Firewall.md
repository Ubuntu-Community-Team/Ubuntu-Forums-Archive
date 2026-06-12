---
title: "NFS issues through Firewall"
date: 2015-11-02
forum: Networking &amp; Wireless
---

### Post by Kyle_Kinkaid on 2015-11-02
Hi,  I'm trying to configure NFS to work through a firewall.  On one side I have an Ubuntu 14.04 client and on the other side I have a desktop nas (ReadyNAS) as server.  I think that ReadyNAS runs a Debian variant.

I read up on how to make NFS restrict the ports it uses here [https://wiki.debian.org/SecuringNFS](https://wiki.debian.org/SecuringNFS) and applied the configuration to the server.  I modified the nfs-common, nfs-kernel-server, quota, and services file to include ports I wanted (basically, TCP&UDP 2049, and TCP&UDP 32764-32769).  I also made modifications to the nfs-common and services file on the client to match.  I then opened up those ports on the firewall.

It still doesn't work and when I look at the firewall logs, I see connection attempt from the Ubuntu client to the ReadyNAS server on port from the source port TCP:856 (?) and several "ephemeral" ports (both source and destination) in the TCP 40k-55k range.  Clearly, something in my config isn't taking but Googling around hasn't been fruitful.  

Am I missing something?  Any tips on how to make the client respect the port ranges desired?

Thanks

---

### Post by TheFu on 2015-11-02
Would a full VPN be an option to connect the 2 networks? That way, all traffic between those two machines will be encrypted and only 1 port will be used - the port that the VPN requires.

---

### Post by SeijiSensei on 2015-11-02
Another alternative is [sshfs]("https://help.ubuntu.com/community/SSHFS"), another secure method which works between any two machines that support SSH.

---

### Post by Kyle_Kinkaid on 2015-11-02
A VPN probably won't work since I don't think the ReadyNAS supports VPNs.

SSHFS would probably work but I'd prefer something like smb/cifs because it's a little simpler to impliment.

Thanks for the tips!

---

### Post by SeijiSensei on 2015-11-03
I think sshfs is easier to implement than CIFS myself.  All you need is openssh-server on the server side and the sshfs software on the client.  I use sshfs to mount directories from one of my virtual servers onto another across the country.  All it takes is an entry in /etc/rc.local like this:
```
sshfs -o allow_other,nonempty 10.10.10.10:/path/to/some/directory /path/to/some/mountpoint
```

---

### Post by TheFu on 2015-11-03
Completely agree about sshfs being easier. Plus permissions work  as expected, none of that CIFS-translation stuff which basically ignores Unix permissions.  Plus, ssh is 100000x more secure than CIFS. 

NFSv4 can be secure (full network encryption), if configured in that way.  v3 cannot  -  needs a VPN to encrypt the traffic.

---


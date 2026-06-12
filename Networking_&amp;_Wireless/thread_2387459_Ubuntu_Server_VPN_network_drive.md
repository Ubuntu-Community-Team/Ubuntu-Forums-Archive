---
title: "Ubuntu Server VPN network drive"
date: 2018-03-19
forum: Networking &amp; Wireless
---

### Post by andyjroberts on 2018-03-19
Hi all this its my first post, been using ubuntu server for about a year just as a file server for a small 4 person office. 

However we would all like to be able to access the files on the network drive from wherever we are as we all travel alot plus would give me the chance to work from home! 

Anyway I believe this is possible by using a VPN such as open VPN, the reason I cant just cloud all the files is there a very old but still very well used MS Access database that requires a mapped network drive. 

So my real question is whats the best way to go about this ? Security is important as is speed. 

Thanks

---

### Post by SeijiSensei on 2018-03-19
You could use OpenVPN with the OpenVPN Windows client. However the machine that accepts the OpenVPN connections needs to be publicly visible which I would strongly discourage in your case.  You could build a router with Linux and OpenVPN that sits on the Internet and interconnects between your local network and the tunneled clients.  Some [router software supports OpenVPN]("https://www.dd-wrt.com/wiki/index.php/OpenVPN") as well, so if your external router has that option, you could use that instead.  Or, if possible, flash it with something like DD-WRT.

Make sure the server's smb.conf file limits connections to the local network and those coming over the tunnel using the "hosts allow" directive like this:

```
hosts allow = 127. 192.168.1 10.1.1
```

That would limit access to localhost, machines on the 192.168.1.0/24 subnet, and machines on the 10.1.1.0/24 subnet.

---


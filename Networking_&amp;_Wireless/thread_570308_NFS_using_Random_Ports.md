---
title: "NFS using Random Ports"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by Circus-Killer on 2007-10-08
Last night I was trying to setup my firewall to accept incoming NFS connections. Usually NFS would use only 2 ports, but for some reason, when the client machine kept tryna connect, it was trying to use a whole range of random ports (everything from 500 to 1000). Naturally, I'm not going to open up ports 500 to 1000.

any suggestions on how to make the NFS client only request on the correct ports, instead of randomly trying to connect to random ports?

---

### Post by netztier on 2007-10-08
> **Circus-Killer said:**
> Last night I was trying to setup my firewall to accept incoming NFS connections. Usually NFS would use only 2 ports, but for some reason, when the client machine kept tryna connect, it was trying to use a whole range of random ports (everything from 500 to 1000). Naturally, I'm not going to open up ports 500 to 1000.


Hm - that seems to be intended behaviour:

**From RFC 2623**> 

2.1. Port Monitoring

[....]

To maximize interoperability:

    * NFS clients SHOULD attempt to bind to ports < 1024. In some cases, if they fail to bind (because either the user does not have the privilege to do so, or there is no free port < 1024), the NFS client MAY wish to attempt the NFS operation over a port >= 1024.
    * NFS servers that implement port monitoring SHOULD provide a method to turn it off.
    * Whether port monitoring is enabled or not, NFS servers SHOULD NOT reject NFS requests to the NULL procedure (procedure number 0). See subsection 2.3.1, "NULL procedure" for a complete explanation.


> **Circus-Killer said:**
> 
any suggestions on how to make the NFS client only request on the correct ports, instead of randomly trying to connect to random ports?

NFS (versions 3 and lower) default to UDP  and use RPC to negotiate acutal ports to use. Unless your firewall "speaks" NFS and can eavesdrop on the RPC communication to open ports dynamically, I wouldn't even consider opening it. If at all possible, force the client to configure NFS-over-TCP. nfs-kernel-server in Ubuntu is TCP enabled by default, you just need to adapt the client by specifying "proto=tcp" in the options column of /etc/fstab:

```
<server address>:/<share name>  /path/to/mountpoint/     nfs   rw,proto=tcp
```

I'm not perfectly sure if this prevents  the NFS client from using source ports <1024, but at least it gives your FW a chance to do proper inspection of the (TCP Layer of the) NFS traffic on port **tcp/2049**. I however wonder if there's still RPC communication on tcp/111.

best regards

Marc

---

### Post by Circus-Killer on 2007-10-08
thanks so much for the advice.

unfortunetly, i'm at work at the moment, and tonight i'm doing a fresh install of gutsy beta, so i wont be able to test this out until tomorrow night.

will let you know after i've tested it out tomorrow night.

---


---
title: "X2GO ssh passphrase problem"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by c-m on 2014-11-04
I normally use FreeNx and no machine client on my machine, but on my current install of 14.04 I was recommended x2go.

Installation was easy and there is no configuration needed of the server. However I'm runing into a problem with connecting to the server (via the same computer)

I've set up ssh and a 4096 bit RSA key with passphrase.

The key .pub has been selected in the x2go client and all other server details have been entered i.e IP and SSH port.

When I try to connect I get a prompt asking for the passphrase. The problem is it just won't accept the passprase I'm entering.

I've even tried using a key without a passphrase but still I'm being asked for one.

Any ideas?

Thanks

---

### Post by TheFu on 2014-11-10
I've never considered connecting to the same machine. Since X2go has an X/Server, seems there could be conflict.  Try from a different machine is my only recommendation.  Works from either Ubuntu or Win7 here.

---

### Post by c-m on 2014-11-11
> **TheFu said:**
> I've never considered connecting to the same machine. Since X2go has an X/Server, seems there could be conflict.  Try from a different machine is my only recommendation.  Works from either Ubuntu or Win7 here.

No, if all is working you should be able to connect to the same machine. The same with NX and FreeNX. It's probably the best way to test it.

In any event I've tried from an external machine and get the same issue. 

Yet SSH itself works perfectly. 

Oddly whilst FreeNX actually has a proper configuration file, there doesn't seem to be any such config file for X2go

---


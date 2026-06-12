---
title: "Static IP set-up, possible problem, maybe not, Help?"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by porteclefs on 2008-10-28
Hey,

Ok so I set up /network/interfaces to look like this:

> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.24.200
        netmask 255.255.255.0
        broadcast 192.168.24.255
        gateway 10.0.0.2


and then ran the command:

```
sudo /etc/init.d/networking restart
```

to restart my networking

I'm not sure if this is a symptom of the solution, or if it is letting me know that I've done something wrong. 

I get the following output:

>  * Reconfiguring network interfaces...                                          SIOCADDRT: No such process
Failed to bring up eth0.
                                                                         [ OK ]

I can still ssh into the server, samba is still accessable from my windows pc's and i can still stream from my media servers... is everything ok? and if everything is ok, what does the above output mean?

thanks

---

### Post by porteclefs on 2008-10-28
please??

---

### Post by bogdan.veringioiu on 2008-10-28
Hi.

could you post the output of ifconfig?

Thanks.

Bogdan

---

### Post by ilrudie on 2008-10-28
That doesn't look like a valid gateway for your network.  Its probably 192.168.24.1 or less likely but possibly 192.168.24.254

---


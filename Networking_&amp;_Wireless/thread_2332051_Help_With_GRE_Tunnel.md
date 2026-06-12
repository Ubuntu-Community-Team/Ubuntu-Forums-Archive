---
title: "Help With GRE Tunnel"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by jacob9 on 2016-07-27
Hello, sorry if I post this in the wrong area.

    I've been trying to set up a GRE tunnel for the past 2 days with no luck, I own an NFO VPS running Ubuntu Server and my main computer has Ubuntu in a VM, and also dual boot to see if VirtualBox is causing any conflict.

I've followed this tutorial completely - [http://wiki.buyvm.net/doku.php/gre_tunnel](http://wiki.buyvm.net/doku.php/gre_tunnel)

I can't ping Host A from Host B and vice versa, not a whole lot of documentation on how to troubleshoot this, especially for Ubuntu.

I'll explain how I did this so anyone can see if I messed up, I loaded the module and enabled ip forwarding. I'll give an IP for this example.

Host A: 123.123.123.123

Host B: 123.123.123.124


[SIZE=5]**Host A**[/SIZE]
```
iptunnel add gre1 mode gre local 123.123.123.123 remote 123.123.123.124 ttl 255
ip addr add 192.168.168.1/30 dev gre1
ip link set gre1 up
```

**[SIZE=5]Host B[/SIZE]**
```

iptunnel add gre1 mode gre local 123.123.123.124 remote 123.123.123.123 ttl 255
ip addr add 192.168.168.2/30 dev gre1
ip link set gre1 up
```


If any extra info is needed, I'll give it. Any help is appreciated.

Edit: PS I'm running Ubuntu 16.04 for this.

---

### Post by jacob9 on 2016-07-28
[b]bump
[/b]

---


---
title: "ongoing internet sharing"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by pipross on 2007-03-29
Hi all,
I'm using ubuntu to share it's internet with 3 XP computers. I go through the process of
(as root)

ifconfig eth0 192.168.0.1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
/etc/init.d/dnsmasq restart
dpkg-reconfigure ipmasq
ifconfig eth0 192.168.0.1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
pon dsl-provider

The other computer are 192.168.0.XX with the DNS being mine

and off it goes - works ok... until I restart or something goes wrong at which time I have to run it all again.
I'm sure I could write a scipt (if I knew how). What can I do to automate this, or any other suggestions would be most welcome.

Cheers
Ross

---

### Post by Mr. C. on 2007-03-29
Put your commands in a file that has as its first line :

```
#!/bin/bash
```

and place that file in /etc/network/if-up.d/  .  Let's call it startshare.  Then run:
```

chown root:root /etc/network/if-up.d/startshare
chmod +rx /etc/network/if-up.d/startshare
```

Next time your network comes up, your script will run.  Change the name of the file to suit your taste.  See other examples in the aforementioned directory.

MrC

---

### Post by pipross on 2007-03-29
beauty, I'll give it a go..:)

---


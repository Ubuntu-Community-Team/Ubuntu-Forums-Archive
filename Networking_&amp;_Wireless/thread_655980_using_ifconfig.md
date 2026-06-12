---
title: "using ifconfig"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by deostroll on 2008-01-02
I had been through this site where it says how to configure your network from command line manually:

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html#more-98](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html#more-98)

I have the following things at hand
[LIST=1]
[*]ip address
[*]subnet mask
[*]default gateway address
[*]dns server
[*]alternate dns server
[/LIST]

can someone tell me how can I specify the last two parameters. It would be great if you could write the whole command out for me. Thanx in advance.

---

### Post by Mithrilhall on 2008-01-02
Add your dns and alternate dns in resolv.conf?

```

cd /etc
sudo nano resolv.conf

```

---


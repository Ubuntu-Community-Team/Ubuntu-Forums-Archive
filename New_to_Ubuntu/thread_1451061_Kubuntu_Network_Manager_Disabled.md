---
title: "Kubuntu Network Manager Disabled"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by kittiikat on 2010-04-09
I just put Kubuntu on my laptop. I have 0 experience with this kind of thing.  My network manager says it is disabled, so I cannot get onto the internet, and I have NO idea how to fix this.

---

### Post by Gixxy on 2010-04-10
do this first...

```
lspci
```

see if your network card(s) are listed...

post the output....

---

### Post by MountainX on 2010-07-02
same problem here. My network manager says it is disabled.
 lspci lists both my adapters. I normally only use the nVidia adapter, which the installer finds first and recommends using.

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
05:06.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)

everything works if I manually add lines to /etc/network/interfaces, but I want to use the stock managed approach that worked until something (unknown to me) broke it.

what next?

---

### Post by MountainX on 2010-07-02
Solved

Lost networking connections. It's a bug.
[https://bugs.launchpad.net/ubuntu/+bug/555571](https://bugs.launchpad.net/ubuntu/+bug/555571)

This fixed my problem:
    service network-manager stop
    rm /var/lib/NetworkManager/NetworkManager.state
    service network-manager start

---


---
title: "Server unresponsive until I use server"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Doom2099 on 2008-09-13
My DSL provider changed my IP addresses (without telling me. I had to call to find out, thanks!) I have updated the interfaces config file and the hosts file (and my apache2 config files). I updated the DNS servers with the new numbers. From other machines, the correct address resolves.

The server responds fine initially but then it will stop responding (anywhere from 2 minutes to a couple hours later). All queries (ping, ssh, web) will timeout. It will stay unresponsive until I access the terminal and ping the internet. All I have to do is ping the gateway and suddenly the server responds correctly to all queries.

I've tried swapping the nic card, thinking my old one was dying. That didn't fix it.

my eth0 config
```

# The primary network interface
auto eth0
iface eth0 inet static
        address XXX.XXX.XXX.100
        netmask 255.255.255.224
        network XXX.XXX.XXX.96
        broadcast       XXX.XXX.XXX.127
        gateway XXX.XXX.XXX.97

```output from netstat -rn

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
XXX.XXX.XXX.96   0.0.0.0         255.255.255.224 U         0 0          0 eth0
0.0.0.0         XXX.XXX.XXX.97   0.0.0.0         UG        0 0          0 eth0

```Any ideas?

---

### Post by JeSTeR7 on 2009-02-12
Wow old thread, but I am having the EXACT same issue as the OP.  I wouldn't even know where to start looking.

---

### Post by JeSTeR7 on 2009-02-12
Just to add to the strangeness, I'm also running VMWare server on the box, with a Windows 2000 server VM using a bridged virtual network adapter.  When the Ubuntu server becomes unresponsive via ping, ssh, or anything else, the Windows 2000 server is still responsive, via RDP or file sharing.

---

### Post by JeSTeR7 on 2009-02-16
Bumping, I'm really stuck on this and have no idea where else to look.

---


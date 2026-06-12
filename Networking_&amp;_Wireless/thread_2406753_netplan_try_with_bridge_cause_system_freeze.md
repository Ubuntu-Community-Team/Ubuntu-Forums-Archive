---
title: "netplan try with bridge cause system freeze"
date: 2018-11-25
forum: Networking &amp; Wireless
---

### Post by mrfx2 on 2018-11-25
Hello there!

I have installed fresh Ubuntu Server 18.04.1 LTS on OVH bare-metal server. I need to run network bridge for LXD containers, but I failed. First of all, after installation there was no file under /etc/netplan/ so I have created one

This is my initial simple configuration without bridges and it works fine:

/etc/netplan/01-netcfg.yaml:

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
     dhcp4: false
     addresses:
       - aaa.bbb.ccc.ddd/24
       - fo1.fo1.fo1.fo1/32
       - fo2.fo2.fo2.fo2/32
       - fo2.fo2.fo2.fo2/32
     gateway4: gw1.gw2.gw3.gw4
     nameservers:
       addresses: [127.0.0.1,8.8.8.8,8.8.4.4]

```

aaa.bbb.ccc.ddd is my main IP and fo... are fail-over ips.


Then I tried to create a bridge and have tested different configurations and none of them works, even following simple example without failover IPs cause system freeze:

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
     dhcp4: false
  bridges:
    br0:
    interfaces: [eno1]
    dhcp4: false
     addresses:
       - aaa.bbb.ccc.ddd/24
     gateway4: gw1.gw2.gw3.gw4
     nameservers:
       addresses: [127.0.0.1,8.8.8.8,8.8.4.4]

```

With above configuration even this:

netplan --debug try

cause system freeze.

There is nothing helpful in the logs. This is my first Ubuntu Server, but as user of Debian since 5.0 I have not anticipated such troubles. What did I do wrong?

---

### Post by mrfx2 on 2018-11-25
I found the problem. There were wrong indents in the yaml file. Amazing, that "try" command can crash the server because of one wrong indent in the file. Fixed configuration with bridges does not crashes the server, but still it does not work and cause the server is unavailable from the network :(

---

### Post by mrfx2 on 2018-11-25
I found a solution and everything works just fine now!

1. Make empty directory: /etc/netplan/ 
2. Create your own configuration at: /etc/systemd/network/ like this: [https://serverfault.com/questions/912366/systemd-bridge-for-vm-multiple-static-ips](https://serverfault.com/questions/912366/systemd-bridge-for-vm-multiple-static-ips)
3. Forget this stupid, buggy "netplan"....

---


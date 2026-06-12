---
title: "Netplan and multiple nics problem"
date: 2019-10-11
forum: Networking &amp; Wireless
---

### Post by beduntu on 2019-10-11
Hi all

Ubuntu 18.04.2 LTS server, of four physical network interfaces present I have to use two, both with static ip. Well, I can't configure the second network card with netplan, needless to say I searched for a solution but I didn't get to the point: the first network card eno1 is always correctly configured, the second eno2 there is no way to assign them an ip; this is the current content of the file /etc/netplan/50-cloud-init.yaml :

```
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      addresses:
        - 10.1.103.100/24
      gateway4: 10.1.103.254
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [10.1.1.5, 10.1.1.6]
    eno2:
      addresses:
        - 10.10.0.100/24
     # gateway4: 10.10.0.254
     # nameservers:
     #     search: [mydomain, otherdomain]
     #     addresses: [10.1.1.5, 10.1.1.6]
```


As you can see, eno2 only needs an ip address because it is connected to a simple plain subnet; if I configure it temporarily with

> sudo ip addr add 10.10.0.100/24 dev eno2

it works perfectly.

for more information I add:

```
>  sudo netplan --debug apply

** (generate:2246): DEBUG: 09:08:05.908: Processing input file /etc/netplan/50-cloud-init.yaml..
** (generate:2246): DEBUG: 09:08:05.909: starting new processing pass
** (generate:2246): DEBUG: 09:08:05.909: eno1: setting default backend to 1
** (generate:2246): DEBUG: 09:08:05.909: eno2: setting default backend to 1
** (generate:2246): DEBUG: 09:08:05.909: Generating output files..
** (generate:2246): DEBUG: 09:08:05.909: NetworkManager: definition eno1 is not for us (backend 1)
** (generate:2246): DEBUG: 09:08:05.909: NetworkManager: definition eno2 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:eno1 not found in {}
DEBUG:eno2 not found in {'eno1': {'addresses': ['10.1.103.100/24'], 'gateway4': '10.1.103.254', 'nameservers': {'search': ['mydomain', 'otherdomain'], 'addresses': ['10.1.1.5', '10.1.1.6']}}}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    eno1:
      addresses:
      - 10.1.103.100/24
      gateway4: 10.1.103.254
      nameservers:
        addresses:
        - 10.1.1.5
        - 10.1.1.6
        search:
        - mydomain
        - otherdomain
    eno2:
      addresses:
      - 10.10.0.100/24
  vlans: {}
  wifis: {}
```

So eno2 seems to be "searched" in eno1 {....} which makes me suspect something wrong with the formatting of the yalm file: needless to say, I tried a few dozen different versions of indent but the best result is always the same: eno1 ok, eno2 ko.

Any suggestion?
Thank's
B.

---

### Post by TheFu on 2019-10-11
Please verify you are using .98 of netplan.  It was recently released. I have know idea if that will help at all or not.

You can remove netplan and go back to ifupdown, if you like.  There are multiple guides for accomplishing that.  Really wish Canonical would stop pushing alpha software onto LTS releases.

---

### Post by beduntu on 2019-10-14
Thanks for the reply.
I tried updating the system without results, so I reinstalled Ubuntu and set the interfaces at install time so that the .yalm file was created by the system: same results, only one interface is configured. But ... There seems to be a bug and currently the devices are configured only if they have a courier: now eno2 doesn't have it! Tomorrow I plug in a cable and I'll see ...

Thanks again.
B

---

### Post by beduntu on 2019-10-15
Finally the solution! Yes, it's a bug: once I have inserted a cable in eno2 this has been configured correctly! I have no words...

---

### Post by TheFu on 2019-10-15
> **beduntu said:**
> Finally the solution! Yes, it's a bug: once I have inserted a cable in eno2 this has been configured correctly! I have no words...

I doubt the netplan team thinks refusing to configure a port that isn't connected as a bug. Think of all the bad cable issues this can solve.

Regardless, happy you found  a solution.

---


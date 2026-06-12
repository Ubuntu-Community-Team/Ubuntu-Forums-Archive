---
title: "NetworkManager - Checking connectivity"
date: 2021-09-03
forum: Networking &amp; Wireless
---

### Post by linerman on 2021-09-03
Hi, I explore my knowledge regarding NetworkManager.
Lately, I've found out that there is an option which is default "on" (Checking connectivity) under:
/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf

I assume it is important thing when there is captive portal present over the network.
But what about a situation when I have only home network without captive portal? 
- Is that "checking connectivity" necessary? 
- Is this making my connection slower (regarding my network home usage)?
- What are the other needs of that option? - I would like to elaborate the subject, maybe someone could guide me?

---

### Post by TheFu on 2021-09-03
If you want the best network connection possible, don't use network-manager. Use netplan with a wires, ethernet, connection.

---

### Post by linerman on 2021-09-04
As far as I know, netplan is a default service in Ubuntu, since 18.04, isn't it? And it still uses NetworkManager.

---

### Post by TheFu on 2021-09-04
> **linerman said:**
> As far as I know, netplan is a default service in Ubuntu, since 18.04, isn't it? And it still uses NetworkManager.

There is a term - "renderer" ... inside netplan.  networkmanager is a valid renderer, but hardly the only one.  Servers don't use it - ever.
networkd is one of the other renderers. An example:

```
network:
  version: 2
  renderer: networkd
  ethernets:
     [COLOR="#FF0000"]ens3[/COLOR]:
       addresses:
          - [COLOR="#FF0000"]172.22.22.3[/COLOR]/24
       dhcp4: false
       dhcp6: false
       gateway4: [COLOR="#FF0000"]172.22.22.1
[/COLOR]       nameservers:
         addresses: [ 1.1.1.1, 1.0.0.1  ]
```
Then run:
```
sudo netplan generate
sudo netplan apply --debug
```
to have the new file used.  Indentation is critical. Copy/paste my example. Keep the same spacing.
I've put in [COLOR="#FF0000"]**red**[/COLOR] the things you need to change to match your network.

---


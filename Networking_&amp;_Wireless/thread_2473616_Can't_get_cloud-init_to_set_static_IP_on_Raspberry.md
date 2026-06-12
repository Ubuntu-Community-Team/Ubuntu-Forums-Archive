---
title: "Can't get cloud-init to set static IP on Raspberry Pi 4"
date: 2022-04-08
forum: Networking &amp; Wireless
---

### Post by mr-akerstrom on 2022-04-08
Hiya, I'm trying to deploy Ubuntu Server 2020.04 to my Raspberry Pi. 
Unfortunately it doesn't seem to apply the static IP address with cloud-init.

If I switch to dhcp, it works fine but not with a static IP. 
Also, the netplan config works if a create a netplan yaml file.
Anyone has any idea?

```

[FONT=Consolas]version: 2
ethernets:
    eth0:
      # Rename the built-in ethernet device to "eth0"   bcmgenet smsc95xx lan78xx
      match:
        driver: bcmgenet
      set-name: eth0
      dhcp4: true
      optional: true
wifis:
    renderer: networkd
    wlan0:
      dhcp4: false
      optional: true
      access-points:
        SunnySide:
          password: "TheNetworkIsTheComputer"
      addresses: [192.168.1.10/24]
      routes:
      - to: 0.0.0.0/0
        via: 192.168.1.1
      nameservers: 
        addresses: [192.168.1.1][/FONT][COLOR=#D4D4D4][FONT=Consolas]
[/FONT][/COLOR]

```

---

### Post by slickymaster on 2022-04-08
Thread moved to **Networking & Wireless** for a better fit

---

### Post by chili555 on 2022-04-08
>  routes:
      -[COLOR="#FF0000"] to: 0.0.0.0/0[/COLOR]
        via: 192.168.1.1The example file /usr/share/doc/netplan/examples/static.yaml suggests that this should be:

```
routes: 
  - to: default
    via: 192.168.1.1
```Please try.

---

### Post by mr-akerstrom on 2022-04-08
I'll try it, however the config does work when I manually run neplan apply. It is just in cloud-init where it fails.

---


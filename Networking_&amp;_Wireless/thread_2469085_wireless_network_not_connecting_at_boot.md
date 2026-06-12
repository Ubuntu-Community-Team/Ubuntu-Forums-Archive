---
title: "wireless network not connecting at boot"
date: 2021-11-18
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2021-11-18
After upgrading to 21.10, my network is not coming up any longer after booting

after running
```
sudo netplan apply
```

the network runs fine

There isn't anything in the logs that would indicate what is wrong

the netplan file looks like this

```

network:
  version: 2
  renderer: networkd
  ethernets:
          enp34s0:
                  dhcp4: yes
  wifis:
    wlo1:
      dhcp4: yes
      dhcp6: no
      access-points:
              "xxx":
                      password: "xxxxx"

```

---


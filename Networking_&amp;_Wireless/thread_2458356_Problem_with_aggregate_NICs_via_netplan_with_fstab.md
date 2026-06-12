---
title: "Problem with aggregate NICs via netplan with fstab."
date: 2021-02-22
forum: Networking &amp; Wireless
---

### Post by boyturtle2 on 2021-02-22
I've had server folders mounted on my desktop with /etc/fstab for some time now and all has been working well, without issue. Yesterday I decided to aggregate 2 the 2 NICs I have in my pc with netplan, my chosen mode was 802.3ad and my Unifi switch supports this. However, as I am new to netplan, this has been quite challenging, but I finally got it to work and the 2 cards were running; ethtool bond0 gave me a speed of 2000Mb/s. Unfortunately, I lost the drives that were previously mounted in /etc/fstab.

I'm sure mounted disks and aggregated NICs should happily live side by side, so I'm wondering if something in the code I'm using is causing this problem or if I've gone about this the wrong way. 

A typical line in the /etc/fstab is ```
//192.168.52.170/Admin /home/ServerAdmin cifs vers=1.0,uid=boyturtle,gid=boyturtle,credentials=/home/boyturtle/.smbcredentials,iocharset=utf8 0  0
```

The full netplan yaml file is as follows
```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp3s0:
      dhcp4: no
    enp0s31f6:
      dhcp4: no
  bonds:
    bond0:
      interfaces: [enp3s0, enp0s31f6]
      addresses: [192.168.52.128/24]
      gateway4: 192.168.52.101
      parameters:
        mode: 802.3ad
        transmit-hash-policy: layer3+4
        mii-monitor-interval: 1
      nameservers:
        addresses:
          - 192.168.52.101
          - 1.1.1.1
          - 9.9.9.9
```

I would appreciate any input to get this resolved

---

### Post by TheFu on 2021-02-22
Just a guess, but I don't think you can use NetworkManager

```
renderer: NetworkManager
```
should be
```
renderer: networkd
```

Examples; [https://netplan.io/examples/#configuring-interface-bonding](https://netplan.io/examples/#configuring-interface-bonding) The example with bond-lan: seems relevant.

---

### Post by boyturtle2 on 2021-03-01
> Just a guess, but I don't think you can use NetworkManager
NetoworkManager works fine. When I run it alone, the 2 NICs link without issue. /etc/fstab works fine too. When I put the two together, my network drives do not mount locally.

---


---
title: "Permanently Enable Jumbo Frames on 10 Gbe Port"
date: 2020-09-02
forum: Networking &amp; Wireless
---

### Post by laceiba2 on 2020-09-02
I have two computers that both contain Asus 10 Gbe network cards connected directly to one another via a Cat 8 cable. One is my Windows desktop, the other is my Ubuntu server running 20.04. I am using Ubuntu as a NAS with a ZFS drive array. Enabling jumbo frames on Windows and having it stick has been easy. I have not been able to figure out how to do this in Ubuntu. Issuing the command below on Ubuntu gets me significantly faster transfer speeds in testing. How do I make this change permanent?

```
sudo ifconfig enp3s0 mtu 9000
```

Thanks in advance for any help.

---

### Post by chili555 on 2020-09-03
Is networking set up with netplan? I suggest that you try:

```
network:
  version: 2
  renderer: networkd
  ethernets:
   enp3s0:
     addresses:
       - 10.10.10.2/24
     gateway4: 10.10.10.1
     nameservers:
         search: [mydomain,otherdomain]
         addresses: [10.10.10.1, 1.1.1.1]
     match:
       macaddress: 00:e0:8d:7e:1f:37
     mtu: 9000
```Of course, substitute your details here. Follow with:

```
sudo netplan generate
sudo netplan apply
```

Check:

```
ifconfig
```

Reference: [https://bugs.launchpad.net/netplan/+bug/1724895](https://bugs.launchpad.net/netplan/+bug/1724895)

---


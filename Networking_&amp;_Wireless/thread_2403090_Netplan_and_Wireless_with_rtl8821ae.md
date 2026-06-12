---
title: "Netplan and Wireless with rtl8821ae"
date: 2018-10-07
forum: Networking &amp; Wireless
---

### Post by shad0wlightus on 2018-10-07
Hello,

New user to Ubuntu 18.04 server and netplan setup.  Previously used Xenial with the same setup and wireless worked correctly after every reboot using /etc/network/interface command.  After every reboot I have to issue the command iwconfig wlp2s0 essid ssid and iwconfig wlp2s0 key password and everything works correctly.  I am not getting any error messages with netplan --debug generate or netplan --debug apply command.  I have wpasupplicant and wireless_tools installed.  Did I miss another package that was needed.  The server was installed using minimal installation.

```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: no
      addresses: [aa.bb.cc.45/24]
      gateway4: aa.bb.cc.1
      nameservers:
        addresses: [aa.bb.cc.9,aa.bb.cc.5]
  wifis:
    wlp2s0:
      dhcp4: no
      addresses: [aa.bb.cc.46/24]
      gateway4: aa.bb.cc.1
      nameservers:
        addresses: [aa.bb.cc.9,aa.bb.cc.5]
      access-points:
        "SSID":
           password: "PSKpassword"
```

---


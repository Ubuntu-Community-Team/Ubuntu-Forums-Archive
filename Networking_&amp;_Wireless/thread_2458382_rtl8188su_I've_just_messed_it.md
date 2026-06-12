---
title: "rtl8188su I've just messed it"
date: 2021-02-23
forum: Networking &amp; Wireless
---

### Post by angelo16 on 2021-02-23
Well.
Trying to fix rtl8188fu I removed a directory following some instructions found somewhere.

Now, even the rtl8188su which should work out of the box, because the kernel blah blah blah, it does not work anymore.

It seems that it does not scan the available networks.

What should I do now ?

```
dell@dell-inspiron1525:~$ lsusb
Bus 002 Device 003: ID 0b05:1786 ASUSTek Computer, Inc. USB-N10 802.11n Network Adapter [Realtek RTL8188SU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. MK260 Wireless Combo Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dell@dell-inspiron1525:~$ 

```

---

### Post by chili555 on 2021-02-23
Please run and post:

```
sudo modprobe r8712u && dmesg | grep r87
```

---


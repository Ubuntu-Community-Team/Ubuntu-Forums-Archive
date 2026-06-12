---
title: "Systemd NIC naming problem"
date: 2016-04-24
forum: Networking &amp; Wireless
---

### Post by csete on 2016-04-24
I'm in the process of building out a new dual NIC server machine with a scratch install of 16.04.  I am trying to follow the directions from [https://www.freedesktop.org/software/systemd/man/systemd.link.html](https://www.freedesktop.org/software/systemd/man/systemd.link.html) to give my network cards nice and easy names to keep track of ingress and egress. However, I can't seem to get one of the card names to "take" and even though this is not a requirement it is kind of driving me a bit crazy that it doesn't seem to work.  I have the following definition 

```

~$ cat /etc/systemd/network/85-inet.link 
[Match]
Path=pci-0000:01:00.0

[Link]
Name=inet0

```

However, no matter what I've tried, I keep getting the following device name:

```

~$ udevadm info /sys/class/net/enp1s0
P: /devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
E: DEVPATH=/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
E: ID_BUS=pci
E: ID_MM_CANDIDATE=1
E: ID_MODEL_FROM_DATABASE=RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
E: ID_MODEL_ID=0x8136
E: ID_NET_DRIVER=r8169
E: ID_NET_LINK_FILE=/etc/systemd/network/85-inet.link
E: ID_NET_NAME_MAC=enxxxxxxxxxxx
E: ID_NET_NAME_PATH=enp1s0
E: ID_OUI_FROM_DATABASE=Hewlett Packard
E: ID_PATH=pci-0000:01:00.0
E: ID_PATH_TAG=pci-0000_01_00_0
E: ID_PCI_CLASS_FROM_DATABASE=Network controller
E: ID_PCI_SUBCLASS_FROM_DATABASE=Ethernet controller
E: ID_VENDOR_FROM_DATABASE=Realtek Semiconductor Co., Ltd.
E: ID_VENDOR_ID=0x10ec
E: IFINDEX=2
E: INTERFACE=enp1s0
E: SUBSYSTEM=net
E: SYSTEMD_ALIAS=/sys/subsystem/net/devices/enp1s0
E: TAGS=:systemd:
E: USEC_INITIALIZED=2360332

```

I can see that it is using the link definition file, but that name isn't "taking".  The other network card is configured similarly and that name is working just fine.

Insights appreciated.
Thanks,
Craig

---


---
title: "Trouble connecting to Wi-Fi"
date: 2018-07-29
forum: Networking &amp; Wireless
---

### Post by felixxwu on 2018-07-29
I'm runnnig Lubuntu 18.04, which I have just installed today on my Asus x205ta from windows 10.

I  am able to plug in an ethernet cable and instantly get internet  connection without problem, however as it is a laptop I want to be able  to use Wi-Fi, which I cannot. There is no option for me to select any  wifi networks and adding my own connection with the SSID and passphrase  also does nothing.

I've tried countless "solutions" online so I will do my best to give some terminal output.
I have run sudo apt update and sudo apt dist-upgrade. I have also reinstalled bcmwl-kernel-source using purge and install.

Here are some of my terminal outputs:

iwconfig:
```

lo        no wireless extensions.

enx9cebe8385322  no wireless extensions.

```

lshw -class network:
```

*-network                 
       description: Ethernet interface
       physical id: 1
       logical name: enx9cebe8385322
       serial: 9c:eb:e8:38:53:22
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152  driverversion=v1.09.9 duplex=full ip=192.168.1.106 link=yes  multicast=yes port=MII speed=1Gbit/s

```

rfkill list:
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

lsusb:
```

Bus 001 Device 007: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 003: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lspci:
```

00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0f)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0f)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0f)
00:1d.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB EHCI (rev 0f)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0f)

```

Any help would be greatly appreciated!!

---

### Post by bjlockie on 2018-09-25
See [https://askubuntu.com/questions/768036/connection-to-wifi-network-with-my-asus-x205ta](https://askubuntu.com/questions/768036/connection-to-wifi-network-with-my-asus-x205ta)

---


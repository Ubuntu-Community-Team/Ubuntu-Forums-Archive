---
title: "Wifi connection gets cut off every few minutes - missing firmware"
date: 2018-06-24
forum: Networking &amp; Wireless
---

### Post by erigeron on 2018-06-24
Hello,

Few days ago I started experiencing the following issue:
my wifi connection works normally until it gets cut off randomly after few minutes.
I have to run a "sudo service network-manager restart" all the time and  the connection starts working again for some more minutes before it happens again.

This is the output of `sudo lshw -C network`:

```

  *-network                 
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: 40:e2:30:cb:ab:a3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.15.0-23-generic firmware=N/A ip=192.168.1.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: enp5s0f1
       version: 12
       serial: 78:24:af:ca:a5:34
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:33 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: docker0
       serial: 02:42:ad:11:8d:68
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes



```

Under configuration/firmware the value is N/A but I don't know if that's actually causing the issue.

Also this is the list of conf files I have under "/etc/modprobe.d"


```
alsa-base.conf                  blacklist-rare-network.conf
amd64-microcode-blacklist.conf  blacklist-watchdog.conf
blacklist-ath_pci.conf          dkms.conf
blacklist.conf                  hda-jack-retask.conf
blacklist-firewire.conf         intel-microcode-blacklist.conf
blacklist-framebuffer.conf      iwlwifi.conf
blacklist-modem.conf            nvidia-graphics-drivers.conf
blacklist-oss.conf
```


Can someone give some help on this one please?
I'm running *Ubuntu* 18.04 LTS.
Thanks.

---

### Post by jeremy31 on 2018-06-24
Firmware isn't needed for that wifi, see if disabling Network Managers ability to enable wifi power management helps
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by erigeron on 2018-06-24
> **jeremy31 said:**
> Firmware isn't needed for that wifi, see if disabling Network Managers ability to enable wifi power management helps
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

Thank you jeremy31, that seems to have solved the issue. :o

---


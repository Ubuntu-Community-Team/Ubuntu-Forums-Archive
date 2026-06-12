---
title: "Ubuntu 20.04 Ethernet R8168 driver is unstable"
date: 2023-03-06
forum: Networking &amp; Wireless
---

### Post by mdennyh91 on 2023-03-06
I've a stability problem with Realtek R8168 Ethernet driver for Ubuntu Server 20.04 LTS that I use. I already followed the instruction given here: [https://askubuntu.com/questions/1327697/ubuntu-20-04-ethernet-r8168](https://askubuntu.com/questions/1327697/ubuntu-20-04-ethernet-r8168). I use this command to install the latest driver:


```
    sudo apt-get update
    sudo apt-get install r8168-dkms
    (then reboot...)

```

The driver I use already the newest version


```
    ethtool -i enp4s0
    
    driver: r8168
    version: 8.048.00-NAPI
    firmware-version:
    expansion-rom-version:
    bus-info: 0000:04:00.0
    supports-statistics: yes
    supports-test: no
    supports-eeprom-access: no
    supports-register-dump: yes
    supports-priv-flags: no

```

My configuration: 

```

     sudo lshw -c network
    
     *-network
           description: Ethernet interface
           product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:04:00.0
           logical name: enp4s0
           version: 16
           serial: d8:5e:d3:d5:ff:24
           size: 1Gbit/s
           capacity: 1Gbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.048.00-NAPI duplex=full ip=192.168.1.242 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
           resources: irq:59 ioport:f000(size=256) memory:fcd04000-fcd04fff memory:fcd00000-fcd03fff



```

**The Problem**
The connection is still unstable, it drops randomly but it will start again after some time. Why is that ? 


**Netplan configuration from (/etc/netplan/00-installer-config.yaml)**


```
    # This is the network config written by 'subiquity'
    network:
      ethernets:
        enp4s0:
          dhcp4: no
          dhcp6: true
          optional: true
          addresses: [192.168.1.242/24]
          gateway4: 192.168.1.1
          nameservers:
            addresses: [192.168.1.1, 8.8.4.4]
      version: 2
      renderer: networkd

```

**System Log (/var/log/syslog)**


```
    Mar  6 11:52:28 rajawaliserver kernel: [   14.505065] r8168: enp4s0: link up
    Mar  6 11:52:28 rajawaliserver kernel: [   14.505097] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
    Mar  6 11:52:28 rajawaliserver systemd-networkd[798]: enp4s0: Gained carrier


    /// HERE THE SERVER GETS VALID ADDRESS IN 192.168.1.242


    Mar  6 11:52:28 rajawaliserver avahi-daemon[814]: Joining mDNS multicast group on interface enp4s0.IPv4 with address 192.168.1.242.
    Mar  6 11:52:28 rajawaliserver avahi-daemon[814]: New relevant interface enp4s0.IPv4 for mDNS.
    Mar  6 11:52:28 rajawaliserver avahi-daemon[814]: Registering new address record for 192.168.1.242 on enp4s0.IPv4.


    /// THEN SOMEHOW, IT DETECTS A CHANGE IN NETWORK CONFIGURATION AND LOSES ITS ADDRESS. 


    Mar  6 11:52:28 rajawaliserver systemd-timesyncd[760]: Network configuration changed, trying to establish connection.
    Mar  6 11:52:29 rajawaliserver avahi-daemon[814]: Joining mDNS multicast group on interface enp4s0.IPv6 with address fe80::da5e:d3ff:fed5:ff24.
    Mar  6 11:52:29 rajawaliserver avahi-daemon[814]: New relevant interface enp4s0.IPv6 for mDNS.
    Mar  6 11:52:29 rajawaliserver systemd-networkd[798]: enp4s0: Gained IPv6LL
    Mar  6 11:52:29 rajawaliserver avahi-daemon[814]: Registering new address record for fe80::da5e:d3ff:fed5:ff24 on enp4s0.*.
    Mar  6 11:52:30 rajawaliserver systemd-resolved[800]: Using degraded feature set (UDP) for DNS server 192.168.1.1.



```

Are there another driver for this ethernet I can use ? Do I need to upgrade the whole OS?

---


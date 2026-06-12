---
title: "How do you create a persistent tap interface in Ubuntu 17.10?"
date: 2018-03-02
forum: Networking &amp; Wireless
---

### Post by nbritton on 2018-03-02
How do you create a persistent tap interface in Ubuntu 18.04 and/or Ubuntu 17.10? I can create the device with "ip tuntap add tap0 mode tap", but I need it to come back up after reboot. I put "pre-up ip tuntap add tap0 mode tap" in /etc/network/interfaces", but that doesn't do anything (in Ubuntu 18.04) because the system is using netplan for the network configuration.

---

### Post by nbritton on 2018-04-19
Step 1: printf "[NetDev]\nName=tap1\nKind=tap\n" > /etc/systemd/network/tap1.netdev
Step 2: Add tap1 to netplan configuration.

Also I've learned if you're trying to setup a virtual bridge for use with KVM you probably want to use a dummy interface instead of tap, the reason for this is because a tap interface will be ignored by netplan because it has a NO-CARRIER status. The networkd team has not got around to properly supporting devices that have a NO-CARRIER status. Instead they recommend using a dummy interface, i.e....

Step 1: printf "[NetDev]\nName=dummy1\nKind=dummy\n" > /etc/systemd/network/dummy1.netdev
Step 2: Add dummy1 to netplan configuration.

[https://github.com/systemd/systemd/issues/6645](https://github.com/systemd/systemd/issues/6645)
[https://www.freedesktop.org/software/systemd/man/systemd.netdev.html](https://www.freedesktop.org/software/systemd/man/systemd.netdev.html)

Here is my netplan configuration:

```

network:
  version: 2
  renderer: networkd

  ethernets:
    eno3: {}
    eno4: {}
    dummy1: {}
    dummy2: {}

  vlans:
    vbridge2-vlan10:
      id: 10
      link: vbridge2
      addresses: [10.11.1.2/24]
    vbridge2-vlan20:
      id: 20
      link: vbridge2
      addresses: [10.11.2.2/24]

  bonds:
    bond1:
      interfaces: [eno3, eno4]

  bridges:
    internet:
      interfaces: [bond1]
      addresses: [10.10.2.2/16]
      gateway4: 10.10.0.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]
    vbridge1:
      interfaces: [dummy1]
      addresses: [10.11.0.2/24]
    vbridge2:
      interfaces: [dummy2]

```

Also to disable IPv6 (because they screwed it up in 18.04) add the following below to /etc/default/grub and then run update-grub and then reboot:
```

GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"

```

For completeness here is the full configuration script for my KVM hypervisor hosts, they run xrdp with xfce:
```

#!/bin/bash


### Install packages ###
apt update;
apt upgrade -y;
apt install -y qemu-kvm libvirt-bin virtinst bridge-utils cpu-checker virt-manager xrdp xfce4 firefox xfce4-terminal nmap iotop;


### Disable IPv6 due to bugs ###
sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT=""/GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"/' /etc/default/grub;


### Setup Network Dummy Interfaces ###
printf "[NetDev]\nName=dummy1\nKind=dummy\n" > /etc/systemd/network/dummy1.netdev;
printf "[NetDev]\nName=dummy2\nKind=dummy\n" > /etc/systemd/network/dummy2.netdev;
systemctl restart systemd-networkd.service;


### Netplan configuration ###
cat << 'EOF' > /etc/netplan/01-netcfg.yaml
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd


  ethernets:
    eno3: {}
    eno4: {}
    dummy1: {}
    dummy2: {}


  vlans:
    vbridge2-vlan10:
      id: 10
      link: vbridge2
      addresses: [10.11.1.2/24]
    vbridge2-vlan20:
      id: 20
      link: vbridge2
      addresses: [10.11.2.2/24]


  bonds:
    bond1:
      interfaces: [eno3, eno4]


  bridges:
    lab:
      interfaces: [bond1]
      addresses: [10.10.2.2/16]
      gateway4: 10.10.0.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]
    vbridge1:
      interfaces: [dummy1]
      addresses: [10.11.0.2/24]
    vbridge2:
      interfaces: [dummy2]
EOF
netplan apply;


### Enable nested virtualization ###
echo "options kvm-intel nested=y" >> /etc/modprobe.d/kvm.conf;


### Enable XRDP server ###
ufw allow 3389/tcp;
echo "xfce4-session" > /root/.xession;
echo "xfce4-session" > /home/nbritton/.xession;
echo "xfce4-session" >> /etc/xrdp/startwm.sh;
sed -i '/\/etc\/X11\/Xsession/ s/^/#/' /etc/xrdp/startwm.sh;
systemctl restart xrdp;

### Workaround Bug 1766695 ### 
sed -i '/ExecStart=/i ExecStartPre=/bin/sleep 20' /lib/systemd/system/xrdp-sesman.service;

```

---


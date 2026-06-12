---
title: "Static IP and netplan stop working a couple days after fresh install Ubuntu Server 18"
date: 2019-02-14
forum: Networking &amp; Wireless
---

### Post by cnorlander on 2019-02-14
[COLOR=#242729][FONT=Arial]Having some major issues with networking on Ubuntu 18.04 LTS. Fresh install. I set a static IP during install which worked for a couple days and remained set after multiple reboots. Now the interface shows no IP. It seems when I set that IP it did generate a netplan that appears correct however netplan apply does nothing.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This happened to me previously as well on the previous install. I had been messing with some DNS stuff so I figured I'd just reimage the machine and not touch any of the network utilities this time and I still am having the issue.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The issue occurs about a day and a half after install seemingly randomly. Was not using the machine when the issue began and the only thing I have done so far on this install is set up a couple docker containers with samba and SFTP.[/FONT][/COLOR]

---

### Post by cnorlander on 2019-02-14
[COLOR=#242729][FONT=Arial] I scrapped the default netplan and followed a tutorial to create this one still no cigar.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Contents of my 50-cloud-init.yaml[/FONT][/COLOR]
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        enp0s25:
            dhcp4: no
            addresses: [192.168.0.32/24]
            gateway4: 192.168.0.1
            nameservers:
                addresses: [1.1.1.1,8.8.8.8]
[COLOR=#242729][FONT=Arial]Terminal output from netplan --debug apply[/FONT][/COLOR]
** (generate:2227): DEBUG: 23:11:19.520: Processing input file /etc/netplan/50-cloud-init.yaml..
** (generate:2227): DEBUG: 23:11:19.520: starting new processing pass
** (generate:2227): DEBUG: 23:11:19.520: enp0s25: setting default backend to 1
** (generate:2227): DEBUG: 23:11:19.520: Generating output files..
** (generate:2227): DEBUG: 23:11:19.520: NetworkManager: definition enp0s25 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:enp0s25 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    enp0s25:
      addresses:
      - 192.168.0.32/24
      dhcp4: false
      gateway4: 192.168.0.1
      nameservers:
        addresses:
        - 1.1.1.1
        - 8.8.8.8
  vlans: {}
  wifis: {}

DEBUG:Skipping non-physical interface: lo
DEBUG:Skipping non-physical interface: docker0
DEBUG:Skipping non-physical interface: br-98e8ea9c70cb
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp0s25
DEBUG:netplan triggering .link rules for docker0
DEBUG:netplan triggering .link rules for br-98e8ea9c70cb

---


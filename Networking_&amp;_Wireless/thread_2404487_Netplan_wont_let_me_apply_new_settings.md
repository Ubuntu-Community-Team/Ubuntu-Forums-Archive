---
title: "Netplan wont let me apply new settings"
date: 2018-10-24
forum: Networking &amp; Wireless
---

### Post by rafise on 2018-10-24
I'm trying to add a vlan taging to my box in the network config /etc/netplan, but when trying netplan apply I get this errors someone know how to properly edit the netplan yaml files?? Thanks guys.

root@test2:~# netplan apply
Error in network definition //etc/netplan/50-cloud-init.yaml line 9 column 12: unknown key vlans
root@test2:~#

 root@test2:~# netplan --debug generateDEBUG:command generate: running ['/lib/netplan/generate']
** (generate:405): DEBUG: 18:26:16.467: Processing input file //etc/netplan/50-cloud-init.yaml..
** (generate:405): DEBUG: 18:26:16.468: starting new processing pass
Error in network definition //etc/netplan/50-cloud-init.yaml line 9 column 12: unknown key vlans
root@test2:~#

-----------------------
root@test2:~# cat /etc/netplan/50-cloud-init.yaml
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    ethernets:
        eth0:
            dhcp4: false
            dhcp6: false
            vlans:
                    eth0.10:
                            addresses:
                            - 10.10.2.10/24
                            dhcp4: false
                            dhcp6: false
                            gateway4: 10.10.2.1
                            id: 10
                            link: eth0
                            nameservers:
                                    addresses:
                                    - 1.1.1.1
                                    search:
root@test2:~#

---


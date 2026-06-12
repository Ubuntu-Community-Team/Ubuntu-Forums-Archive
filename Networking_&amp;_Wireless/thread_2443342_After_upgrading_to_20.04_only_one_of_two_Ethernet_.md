---
title: "After upgrading to 20.04 only one of two Ethernet ports are recognised"
date: 2020-05-14
forum: Networking &amp; Wireless
---

### Post by tranoire on 2020-05-14
Hi, I hope someone can help.

I upgraded from 19.10 -> 20.04 Desktop.  Everything was fine in 19.10.  I'm running a SuperMicro motherboard with two ethernet ports, an Aquantia 10Gb (eno1) and an Intel 1Gb (eth0).  eno1 works as expected but I cannot get eth0 to work.  On startup eth0 appears as DISABLED in ifconfig. If I run 'ifconfig eth0 up' then it appears to be ok but doesn't work.  Plugging in a cable doesn't work - ping 8.8.8.8 -> Network is unreachable.  Same for local network.   Note I unplug from eno1 and plug into eth0 so cable shouldn't be the issue.

Running 'ethtool eth0' shows Speed correctly, along with Link Detected: Yes

I've tried using the network settings gui to add another wired connection.  The MAC address for eth0 shows as (null)(eth0), and cannot be selected.

I've tried adding the following to /etc/netplan/x.conf

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
      dhcp4: yes
      macaddress: <eth0 mac>
    eno1:
      dhcp4: yes
      macaddress: <eno1 mac>

Note: with correct spacing

When I 'netplan try' and click the top right of the screen I see Ethernet Unmanaged and two two connections to choose between:
netplan-eth0
Wired Connection 2
I can't select either.  Opening up Wired Settings and there's only one network which says 'Cable unplugged'.

If I remove the netplan rows and apply again, click top right of screen, 'Ethernet Unmanaged', I lose the two wired options and just 'Connect' or Settings.  Connect does nothing.  Try to add a new connection and I can't select a device:
(null)(eth0)


Anyone got any ideas?  Anything I can try?  Any diagnosis I can run?


Thanks
Simon

---


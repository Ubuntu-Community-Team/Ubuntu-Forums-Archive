---
title: "NetworkManager does not spoof MAC address after making appropriate configuration"
date: 2019-09-20
forum: Networking &amp; Wireless
---

### Post by mbman88 on 2019-09-20
**not a duplicate, **I believe this problem is unique to my system, possibly a configuration issue or missed syntax or step, etc., or perhaps an unreported bug... but I'm uncertain.

I've followed this guide [https://wiki.archlinux.org/index.php/NetworkManager#Configuring_MAC_address_randomization](https://wiki.archlinux.org/index.php/NetworkManager#Configuring_MAC_address_randomization) **and **[&#8203;https://blogs.gnome.org/thaller/2016/08/26/mac-address-spoofing-in-networkmanager-1-4-0/]("http://&#8203;https://blogs.gnome.org/thaller/2016/08/26/mac-address-spoofing-in-networkmanager-1-4-0/") ...

I have a file located in /etc/NetworkManager/conf.d with the configuration of: 

```
[connection]
wifi.powersave = 3

# 'permanent' uses the hardware mac address, 'preserve' keeps the mac address the same, 'stable' generates a permanent mac address per network, 'random' generates mac per each connection/association
# I presume to assign a specific address you add it at the end of the '=' sign or have an empty space between; e.g., ethernet.cloned-mac-address=00:22:68:1c:59:b1
# OR ethernet.cloned-mac-address 00:22:68:1c:59:b1

# Ethernet setting
ethernet.cloned-mac-address=random
# Generate a random MAC for each WiFi and associate the two permanently.
wifi.cloned-mac-address=random
```


I attempted to restart NetworkManager in various ways, 
```

systemctl restart NetworkManager 
sudo killall -SIGHUP NetworkManager
sudo nmcli con reload

```

I have just did this before I did anything of this, today: ```
dpkg-reconfigure resolvconf
```
This is to fix the inability to log-in to a network that prompts for an "Agreement" via webpage.

I have Private Internet Access installed.


After I do all of this and connecting to a network that I have to accept and agreement on a webpage, no changes are found via ifconfig and ip link. The default MAC address still exists. Each time the network reconnects without prompting for an "Agreement page" telling me that I'm using the same MAC address as before.

I previously had a separate configuration file in the conf.d directory. I tried putting the configuration into the NetworkManager.conf file.


My version is 16.04 Ubuntu-MATE

NetworkManager version 1.2.6

---

### Post by mbman88 on 2019-09-20
Quick UPDATE reply:

After reading at least 1 post there's a possibility that no one will help me on this issue... however, after reading this post [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752)
It seems that this issue may be built-in due to an somewhat unrelated security issue. The post indicates that the macchanger method now works with NetworkManager, which never worked before. I tried it and it has worked.

I'm not gonna mark it as solved, however, because the original question pertains to getting NetworkManager on automated randomization for network connections, and that issue is unsolved and desirable.

---


---
title: "No wifi on remote vnc server"
date: 2019-11-08
forum: Networking &amp; Wireless
---

### Post by makem2 on 2019-11-08
I have just setup Ubuntu 19.10 on a Raspberry Pi4 and am using  tightvnc from a linux laptop to access it remotely, headless. I am able to connect via ssh, with remmina and use the internet.

The wifi icon (two arrows) is greyed out and the settings from there are also greyed out. I thought that wifi was automatically associated.

[URL="https://paste.ubuntu.com/p/K9Swrkydxk/"]https://paste.ubuntu.com/p/K9Swrkydxk/
[/URL]
Netplan settings are:

```

# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        eth0:
            dhcp4: true
            optional: true
    version: 2

network:
    version: 2
    renderer: networkd
    wifis:
        wlan0:
             optional: true
             dhcp4: true
             access-points:
                     "xxxxxxxxxxxxx":
                             password: "xxxxxxxxxxxxxxxxxxx"

```

---


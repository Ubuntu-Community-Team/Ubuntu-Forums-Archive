---
title: "Why is the network not working on boot and why am I getting a IP even if DHCP is off?"
date: 2019-04-06
forum: Networking &amp; Wireless
---

### Post by molaf on 2019-04-06
I am on 18.04.2 with the latest updates and I have the following netplan config file:


```
    network:
      version: 2
      renderer: networkd
      ethernets:
        eno1:
          dhcp4: no
          dhcp6: no
          optional: true
        enp2s0:
      bonds:
        bond0:
          interfaces: [eno1, enp2s0]
          addresses: [192.168.3.5/24]
          gateway4: 192.168.3.253
          nameservers:
            addresses: [208.67.222.222,208.67.220.220,8.8.8.8,8.8.4.4]
          dhcp4: no
          parameters:
            mode: active-backup
            primary: eno1

```

It was working fine until I updated the system at the beginning of this week, update which included the kernel and several more packages. I haven't kept track so I cannot give any further information about it.
I only know that the update disabled all the services and targets for ZFS I compiled from trunk. 

When I boot I cannot access the server and the server cannot access the local LAN or the WAN. If I log in physically I get this:

```
    IP address for enp2s0: 192.168.3.97
    IP address for bond0:  192.168.3.5

```

Then if I issue a **netplan apply** the server is back to normal!
 However, I still get an IP even if I specified **dhcpX: no**. The router (OpenWRT) has not even a preassigned IP for the MAC address of either network card!

I tried to check the services:

```

$ systemctl status networkd-dispatcher.service networking.service network-online.target network-pre.target network.target | cat

Unit networking.service could not be found.
&#9679; networkd-dispatcher.service - Dispatcher daemon for systemd-networkd
   Loaded: loaded (/lib/systemd/system/networkd-dispatcher.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-04-06 22:02:12 CEST; 22min ago
 Main PID: 2433 (networkd-dispat)
    Tasks: 2 (limit: 9830)
   CGroup: /system.slice/networkd-dispatcher.service
           &#9492;&#9472;2433 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers

Apr 06 22:02:11 systemd[1]: Starting Dispatcher daemon for systemd-networkd...
Apr 06 22:02:11 networkd-dispatcher[2433]: No valid path found for iwconfig
Apr 06 22:02:12 systemd[1]: Started Dispatcher daemon for systemd-networkd.

&#9679; network-online.target - Network is Online
   Loaded: loaded (/lib/systemd/system/network-online.target; static; vendor preset: enabled)
   Active: active since Sat 2019-04-06 22:02:10 CEST; 22min ago
     Docs: man:systemd.special(7)
           https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget

Apr 06 22:02:10 systemd[1]: Reached target Network is Online.

&#9679; network-pre.target - Network (Pre)
   Loaded: loaded (/lib/systemd/system/network-pre.target; static; vendor preset: enabled)
   Active: active since Sat 2019-04-06 22:02:07 CEST; 22min ago
     Docs: man:systemd.special(7)
           https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget

Apr 06 22:02:07 systemd[1]: Reached target Network (Pre).

&#9679; network.target - Network
   Loaded: loaded (/lib/systemd/system/network.target; static; vendor preset: enabled)
   Active: active since Sat 2019-04-06 22:02:07 CEST; 22min ago
     Docs: man:systemd.special(7)
           https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget

Apr 06 22:02:07 systemd[1]: Reached target Network.

```

Can anyone help me in the solving this problem?

---

### Post by molaf on 2019-04-09
Any suggestion to debug the issue?

---

### Post by molaf on 2019-04-21
[COLOR=#111111][FONT=&amp]I disabled the bonding and now it works.

Has anyone an explanation?

Thanks in advance


[/FONT][/COLOR]

---


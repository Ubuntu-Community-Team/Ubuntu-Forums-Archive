---
title: "Spoofing Mac Address Problems"
date: 2019-05-23
forum: Networking &amp; Wireless
---

### Post by rebellious.ben on 2019-05-23
Okay so I use my wireless connection on my laptop, however, when I type "sudo macchanger -r (wireless)" - It works but my wireless connection comes up in my top right and will not connect. Does anyone have any ideas for me to try? Thanks.

---

### Post by TheFu on 2019-05-23
Bring down any network connections first, change the MAC, bring up the specific network connection.  MAC is used for getting fresh DHCP information most places. In some networks, a new MAC isn't allowed to connect at all or might be put onto an outside network for internet access only, no LAN access.

Do you have the correct device, specified correctly?

When I try to use macchanger, it doesn't work.
```
[ERROR] Could not change MAC: interface up or insufficient permissions: Device or resource busy
```
It isn't "up" or in use and I'm using sudo. Also, it isn't locked via rfkill.
```
$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

On my system, I have only 1 guess.  The management tool I use has it exclusively locked. Nope. That wasn't it.

[https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses) is the only other thing that I've found.  I avoid using wifi as much as possible due to security considerations. Basically, I only use it with a VPN or with ssh-tunnel to my LAN when travelling.

---


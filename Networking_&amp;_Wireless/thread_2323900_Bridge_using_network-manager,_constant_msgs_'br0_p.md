---
title: "Bridge using network-manager, constant msgs 'br0: port 1(enp3s0f1) received tcn bpdu'"
date: 2016-05-09
forum: Networking &amp; Wireless
---

### Post by interzoneuk on 2016-05-09
Hi.

I am setting up a network bridge of my wired interface for use with KVM using 16.04

Previously I used to just edit the /etc/network/interfaces to create the bridge - i.e -> [https://wiki.ubuntu.com/KvmWithBridge](https://wiki.ubuntu.com/KvmWithBridge)

However I want to use network-manager in order to easily switch network-profiles (to connect to different network segments)

If I create the bridge using nmtui with STP enabled I see constant messages (dmsg) - e.g

```
[1271.540537] br0: port 1(enp3s0f1) received tcn bpdu
[1271.540548] br0: topology change detected, propagating
```

However if I disable STP the messages disappear.

Also if I use the old method for bridging ( [https://wiki.ubuntu.com/KvmWithBridge](https://wiki.ubuntu.com/KvmWithBridge)) and enable STP I do not see those messages.

Why am I only seeing the bpdu messages using netwiork-manager and is this an indication something is wrong?

---


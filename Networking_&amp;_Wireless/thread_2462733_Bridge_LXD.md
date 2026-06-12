---
title: "Bridge LXD"
date: 2021-05-26
forum: Networking &amp; Wireless
---

### Post by aavar on 2021-05-26
Hi
I have successfully set up lxd and I am loving it.
The issue I am having is that the containers are not visible to the network.
I have tried different approaches, but none of them gives me the result I am looking for (either the container is visible to everything but the host or the host (and the container) has no connection to the network at all.
Can you please point me to a guide to setting this up?
I am using ubuntu 20.04 server with netplan and NetworkManager.

Thank you in advance :)

---

### Post by TheFu on 2021-05-26
I don't use 20.04 nor network-manager. Actually, I don't think network-manager can accomplish a normal linux-bridge.

Step 1:  Setup a normal Linux bridge. This can be the same bridge used by the host, other VMs, whatever.
Step 2: Tell LXD to use the bridge. Let my check my notes for the command.

[https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/)
[https://bayton.org/docs/linux/lxd/lxd-zfs-and-bridged-networking-on-ubuntu-16-04-lts/](https://bayton.org/docs/linux/lxd/lxd-zfs-and-bridged-networking-on-ubuntu-16-04-lts/) (it has netplan example)

lxc profile list
lxc profile create bridged  # name of profile is "bridged"
lxc profile show bridged    # name of profile is "bridged"
# ###################### Profiles
# Build and start a container using a specific profile
lxc launch -p default -p bridged ubuntu:x mybridge

Sorry, I don't have more LXC/LXD stuff. Connecting the bridge to the lxd profile wasn't hard. I don't recall the exact command. It "just worked" on the first attempt.

One of the main reasons I didn't move my servers to 20.04 already is that netplan bridging was less-than-obvious for the first 9+ months and I didn't have a spare machine on which to play "what if".  I've gotten more comfortable with netplan in the last year and it seems to support bridges fine now, based on my reading and solutions for problems in these forums.

---


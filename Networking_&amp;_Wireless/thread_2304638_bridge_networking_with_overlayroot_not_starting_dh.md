---
title: "bridge networking with overlayroot not starting dhcpc"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by neil.the.blue on 2015-11-28
Hello,

I am running ubuntu server 15.10. I have installed openssh, lxc and overlayroot. When I set overlayroot="tmpfs", I find that the network bridge device is no longer allocated an address via dhcp so I can not log onto the machine. 
But all works fine if I disable overlayroot.
I have also stoped lxc-net and added a standard bridge:

```

auto lo
iface lo inet loopback

auto enp2s0
iface enp2s0 inet manual

auto br0
iface br0 inet dhcp
    bridge-ifaces enp2s0
    bridge-ports enp2s0
    up ifconfig enp2s0 up

```

I am guessing that the overlay root is preventing some network setup but I am not sure what.
Any help or suggestions please.

Thanks
Neil

---

### Post by zhangyang2 on 2015-12-21
Hi Neil

    I also met this question.Have you solve it?

Thanks
kevin

---


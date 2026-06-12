---
title: "Adding tap device to bridge causes DNS to fail (sometimes)"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by Bill Cosby on 2017-05-15
Hello everyone,

I am on Ubuntu xenial (16.04 LTS), since I use virtualization, I decided to make a bridged network.

I created the bridge in [FONT=Courier New]/etc/network/interfaces
[/FONT] like so:
```

iface enp0s31f6 inet manual

auto br0
iface br0 inet dhcp
  bridge_ports    enp0s31f6
  bridge_stp      off
  bridge_maxwait  0
  bridge_fd       0

```

and my internet works fine. When I add a tap device like this:

```

user=anyone
dev=tap0
ip tuntap add $dev mode tap user $usr
ip link set $dev up
ip link set $dev master br0

```

I can use the tap device to access the internet without problems from my virtualized guest. **Sometimes**, I still have normal internet access from my host (i.e. DNS is working).
However more often than not, the DNS fails on my host system (I tested by pinging remote hosts with their IP, with their name it would fail). Everything is fine again on my host system as soon as I remove the tap device.

I do not think these are external network issues, since I had very much the same setup on Fedora, and it worked flawlessly.

I can't find anything useful in [FONT=Courier New]dmesg[/FONT], [FONT=Courier New]syslog[/FONT] or [FONT=Courier New]ip route[/FONT] to help me out. So I am asking here, has anyone an idea what is wrong?

Kind regards,
Bill

---


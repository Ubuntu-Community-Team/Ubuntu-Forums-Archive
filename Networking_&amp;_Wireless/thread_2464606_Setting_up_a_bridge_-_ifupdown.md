---
title: "Setting up a bridge - ifupdown"
date: 2021-07-07
forum: Networking &amp; Wireless
---

### Post by markdavidoff on 2021-07-07
I've been stuck at this for 3 days, so I've come for help. I followed several guides online for setting up a bridge for my KVM servers. Seems simple, but I have had uncountable problems.
Initially, I tried using netplan, and that didn't work. I have gone back to ifupdown in an attempt to get things working. Same or worse results.

Note: The machine is headless - console only. I'm running Ubuntu 20.04

The result of my attempts rendered the VM talking to the network, but I could not talk to the host.
I.E. I could ping the VM, which got a DHCP IP, but no ports on the host contactable.
I am also unable to ping the gateway from the host.

In order to get access to the host, I need to plug in physically and remove the bridge, then reboot.

My interfaces now:

```
auto lo
iface lo inet loopback

iface enp2s0 inet manual

auto br0
iface br0 inet static
    hwaddress ether 3c:d9:2b:06:d3:6a
    address 192.168.0.222
    netmask 255.255.255.0
    gateway 192.168.0.1
    bridge_ports enp2s0
    bridge_stp on
    # If STP is off, set to 0. If STP is on, set to 2 (or greater).
    bridge_fd 2

```

**brctl show**
```

**bridge name     bridge id               STP enabled     interfaces**
br0             8000.3cd92b06d36a       yes             enp2s0
```

**ip route**
```

default via 192.168.0.1 dev enp2s0 src 192.168.0.222 metric 202
default via 192.168.0.1 dev br0 proto dhcp src 192.168.0.21 metric 204
169.254.0.0/16 dev vnet0 scope link src 169.254.116.104 metric 205
192.168.0.0/24 dev enp2s0 proto dhcp scope link src 192.168.0.222 metric 202
192.168.0.0/24 dev br0 proto dhcp scope link src 192.168.0.21 metric 204
```

I'm not the best at networking. I'm wondering if it's ip route related?
That stuff gets automatically configured though, so I'm not too sure what to change there if anything.

Thanks for your help!

---

### Post by markdavidoff on 2021-07-07
It was suggested on another forum to remove the "enp2s0" lines from the routes, [as that user didn't have their main NIC in their routing table with a similar setup]("https://community.home-assistant.io/t/install-home-assistant-os-with-kvm-on-ubuntu-headless-cli-only/254941/49")

I think this may have resolved the issues (I can at-least ping the router from the host now, and vice-versa. I haven't tested the VM yet).
**However, the system keeps adding these lines back in with the "enp2s0" device, which has a lower metric - (higher priority).**
Is there a way to find out what is doing that, or to force a lower metric for that interface?

Perhaps I'm thinking about this in the wrong way?
Help appreciated. Thanks!

---

### Post by markdavidoff on 2021-07-07
Alright, after doing some Google-fu, I found [this post for Raspberry Pi]("https://unix.stackexchange.com/questions/182967/can-i-prevent-a-default-route-being-added-when-bringing-up-an-interface/657438") where the user was complaining that their Ethernet was getting a default route instead of WiFi.

I noticed an entry in my **dhcpcd.conf** an entry for enp2s0, so I added **metric 1000** at the bottom of the entry.
Now, the routes get added, but it's not of high priority.

Wish I knew that was happening before getting rid of Netplan!

---


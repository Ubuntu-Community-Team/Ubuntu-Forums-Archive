---
title: "Problems with Netplan yaml configure file doesn't enable ethernet device"
date: 2020-04-23
forum: Networking &amp; Wireless
---

### Post by dhiaagr on 2020-04-23
Hi everybody,

I configured netplan yesterday, and the changes seemed to be persistent across reboots. Yet today, it doens't seem to work.

When running ```
sudo lshw -c network
```
Ethernet device appears disabled.

Here's my yaml configuration file;
```

network:

    ethernets:

      enp2sO:

        addresses: []
        dhcp4: true

    version: 2

```

I generated and applied the yaml configuration file multple times using :
```
sudo netplan generate
```
```
sudo netplan apply
```

I have to run after each reboot :
```
sudo dhclient enp2s0
```

Any ideas as to what should I do ?

---

### Post by chili555 on 2020-04-23
> 
network:

    ethernets:

      enp2sO:

        addresses: []
        dhcp4: true

    version: 2

You seem to have omitted the renderer and the spacing and indentation are a bit off. Is that a capital o in the interface name or a zero? It should be zero.

May I suggest:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: true

```Followed by the usual:

```
sudo netplan generate
sudo netlan apply
```

---------

Reference: /usr/share/doc/netplan/examples/dhcp.yaml

---

### Post by dhiaagr on 2020-04-23
Hi Chili,
I must've mistyped it out of frustration since I tried a lot of different things. 
Thank you for the heads up. That was indeed a letter O that should've been the digit 0.
Network is all set up now, but I still don't know what caused the problem in the first place.
I will mark the question resolved for now and cross my fingers that the issue doesn't get reproduced.
Thank you again ( :

---


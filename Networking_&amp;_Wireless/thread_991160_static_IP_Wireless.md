---
title: "static IP Wireless"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by Xanerrix on 2008-11-23
hi,

I have been trying to get a static IP connection working to do some sharing but I am not able to successfully modify the interfaces file.

What I find strange is that my interfaces file is the following before modifications:

```
auto lo
iface lo inet loopback
```

I have no primary wlan0 interface but my wireless works fine.
I have tried changing to:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
       address 192.168.0.197
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.0.255
       gateway 192.168.0.1
```

I have also tried:
```

auto wlan0
iface wlan0 inet static
       address 192.168.0.197
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.0.255
       gateway 192.168.0.1
```
Without the rest.
I am at a loss with this.

I have a D-Link DIR-625 Router

Thanks
Andre

---

### Post by Xanerrix on 2008-11-23
Update:

I used the network tools from System > Administration > Network Tools.
And tried to configure my connection from there.

It says:
The interface does not exist.
Check that it is correctly typed and that it is correctly supported by your system.

But my connection works...

---


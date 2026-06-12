---
title: "OpenVPN embedded device: you must define (TUN/TAP) device"
date: 2019-09-25
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2019-09-25
Hi,
I'm using an embedded device and I want to setup a VPN connection with openVPN. The problem is related to a specific device since with other devices and same OS and configuration, the problem is not present. The device has mips CPU with 4.10.12 linux kernel and openVPN 2.3.9.
I get the error: ```
you must define (TUN/TAP) device (--dev)
```
I added to ```
/etc/modules tun
``` and I tried with ```
modprobe tun
```
If I type ```
openvpn --mktun --dev tun0
``` I get TUN/TAP device
```

tun0 opened
persistent state set to: ON

```
Then if I type ```
openvpn --config my.ovpn
``` I get the same error message.
Any idea?
Thank you

P.S.
I trivially solved via ```
openvpn --dev tun0 --config my.ovpn
```

---


---
title: "Ubuntu 14.04 server, static IPv6 interface doesn't initialize if cable is unplugged"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by richard51 on 2014-04-25
This is my first post, and I am not sure if this is a bug, by design or an error on my part …

 I am using Ubuntu 14.04 lts server edition, and setting up an IPv6 only network for testing purposes. I have set the eth0 interface to have a static IPv6 ULA address, which points to my local network (switch). The problem I am having is this, if the cable is not connected to the interface (eth0) I will get the message "*waiting for network configuration*" at boot, the interface does not initialize, and the static IPv6 address is ignored by my DNS (bind9).

Syslog reports:
 ```
IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
creating IPv6 interface eth0 failed; interface ignored (bind9)
``` 

 This is my /etc/network/interfaces file:
```
# The loopback network interfaces
auto lo
iface lo inet loopback
iface lo inet6 loopback

# The wide area network interface
auto wlan0
iface wlan0 inet6 static
pre-up modprobe ipv6; wpa_supplicant -B -D wext -i wlan0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
address 2002:xxxx:xxxx:xxxx::xxxx/64
netmask 64
gateway 2002:xxxx:xxxx:xxxx:xx:xx:xx:xx
dns-nameservers ::1
dns-search foobar.com
dns-domain foobar.com

# The local area network interface
auto eth0
iface eth0 inet6 static
pre-up modprobe ipv6
address fd51:xxxx:xxxx:xxxx::x/64
netmask 64
```

Because these are static addresses, I don't understand why eth0 is not initialized at boot and ignored by bind9. I have tested it with IPv4 and that works as expected. This is a test server and is very rarely connected to the local network, and I cannot test packages like bind9, dnsmasq if it ignores the static IPv6 eth0 interface.

Any help would be appreciated!

---

### Post by richard51 on 2014-04-26
Sorry to *bump* up this thread, but can anyone help with this annoying problem?

I have tried numerous different configurations over the past week to get the static IPv6 to work (unplugged), but to no avail :confused:.

---

### Post by richard51 on 2014-04-30
I managed to fix this little annoyance, by adding the following line in **bold**.

```
# The loopback network interfaces
auto lo
iface lo inet loopback
iface lo inet6 loopback

# The wide area network interface
auto wlan0
iface wlan0 inet manual
iface wlan0 inet6 static
pre-up modprobe ipv6; wpa_supplicant -B -D wext -i wlan0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
address 2002:xxxx:xxxx:xxxx::xxxx/64
netmask 64 gateway 2002:xxxx:xxxx:xxxx:xx:xx:xx:xx
dns-nameservers ::1
dns-search foobar.com

# The local area network interface
auto eth0
**iface eth0 inet manual**
iface eth0 inet6 static
pre-up modprobe ipv6
address fd51:xxxx:xxxx:xxxx::x/64
netmask 64
```
Why setting the Ipv4 to manual works... is because, (*I haven't the foggiest idea!*) :confused:

---

### Post by brillat on 2014-06-17
I think it works because you just added a little delay while it thinks about the ipv4.  The ipv4 isn't related to the ipv6.

I just added a delay, and it fixed this same problem on mine:
iface eth0 inet6 static
**        pre-up sleep 10**
        address xxx:xxx:xx::10
        netmask 64

---


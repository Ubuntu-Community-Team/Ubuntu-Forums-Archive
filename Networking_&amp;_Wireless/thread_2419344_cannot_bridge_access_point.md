---
title: "cannot bridge access point"
date: 2019-05-20
forum: Networking &amp; Wireless
---

### Post by wongultraman on 2019-05-20
I have been trying to bridge ethernets with ap to make a wireless/wired router; but the ap is not ready with the following netplan codes.  Please help.

```
network:
  renderer: networkd
  version: 2
  ethernets:
    renderer: networkd
    eno1:
      dhcp4: yes
      dhcp6: no
    enp5s0f0:
      dhcp4: yes
      dhcp6: no
    enp5s0f1:
      dhcp4: yes
      dhcp6: no
    enp6s0f0:
      dhcp4: yes
      dhcp6: no
    enp6s0f1:
      dhcp4: yes
      dhcp6: no
  wifis:
    wlp2s0:
      dhcp4: yes
      dhcp6: no
      access-points:
        "MYAP":
#          mode: ap
#          channel: 6
          password: "12345678"

  bridges:
    br0:
      addresses: [192.168.8.4/24]
      gateway4: 192.168.8.4
      nameservers:
        addresses: [218.102.23.77, 218.102.62.71]
      interfaces: [enp5s0f0, enp5s0f1, enp6s0f0, enp6s0f1, wlp2s0]
      dhcp4: true
      parameters:
        stp: false
        forward-delay: 0


```

---

### Post by #&amp;thj^% on 2019-05-20
I have found bridging stuff sometimes requires magic. :)
And I'm not sure how everything is set up o your end but see if this helps:
For configuring a bridge from ethernet to wifi, it is as simple as doing it in your "/etc/network/interfaces":
```

auto eth0
allow-hotplug eth0
iface eth0 inet manual

auto wlan0
allow-hotplug wlan0
iface wlan0 inet manual

auto br0
iface br0 inet static
bridge_ports eth0 wlan0
    address 192.168.1.100
    netmask 255.255.255.0
```

Replace the IP address with something more appropriate** to your network**.

If you prefer the IP attribution done via DHCP, change it to:
```

auto br0
iface br0 inet dhcp
bridge_ports eth0 wlan0
```

After changing /etc/network/interfaces, either restarting Debian or doing
```

service networking restart
```

Will activate this configuration.

**You will have to make sure for this configuration to have "bridge-utils" installed. You can install it with:**
```

sudo apt install bridge-utils
```

For more information, see: [https://manpages.debian.org/jessie/bridge-utils/bridge-utils-interfaces.5.en.html](https://manpages.debian.org/jessie/bridge-utils/bridge-utils-interfaces.5.en.html)

The wlan0 interface also has to be configured to connect to your remote AP so this configuration is not to be used verbatim.(Exact word for word)

Additional note: bridging eth0 and wlan0 together means in poor layman´s terms that br0 will present itself as a single logical interface englobing the interfaces that makes part of the bridge. Usually such configuration is made when both extend or belong to the same network.
Clear as mud right? :)

---

### Post by wongultraman on 2019-05-20
Thanks for the help.  Actually, I have no problem to config the bridge with /etc/network/interfaces (it is already working in my 18.04 server); however, I would like to upgrade it to 19.04 server (for better support of bt keyboard)and therefore need to migrate to netplan.

---

### Post by #&amp;thj^% on 2019-05-20
> **wongultraman said:**
> and therefore need to migrate to netplan.

Good Luck with that one: :D I'm still tinkering with that one as we speak.
Wireless devices use the &#8216;wifis&#8217; key and share the same configuration options with wired ethernet devices. The wireless access point name and password should also be specified: (Yes I see that you do have that)
Example:
```

network:
  version: 2
  renderer: networkd
  wifis:
    wlp2s0b1:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.0.21/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [192.168.0.1, 8.8.8.8]
      access-points:
        "network_ssid_name":
          password: "**********"

```
Forgot to add if needed, **Important>>>Netplan supports both networkd and Network Manager as backends.** You can specify which network backend should be used to configure particular devices by using the renderer key. You can also delegate all configuration of the network to Network Manager itself by specifying only the renderer key:
```

network:
  version: 2
  renderer: NetworkManager

```
Configuring interface bonding

Bonding is configured by declaring a bond interface with a list of physical interfaces and a bonding mode. Below is an example of an active-backup bond that uses DHCP to obtain an address:
```

network:
  version: 2
  renderer: networkd
  bonds:
    bond0:
      dhcp4: yes
      interfaces:
        - enp3s0
        - enp4s0
      parameters:
        mode: active-backup
        primary: enp3s0
```

Below is an example of a system acting as a router with various bonded interfaces and different types. Note the &#8216;optional: true&#8217; key declarations that allow booting to occur without waiting for those interfaces to activate fully.
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: no
    enp2s0:
      dhcp4: no
    enp3s0:
      dhcp4: no
      optional: true
    enp4s0:
      dhcp4: no
      optional: true
    enp5s0:
      dhcp4: no
      optional: true
    enp6s0:
      dhcp4: no
      optional: true
  bonds:
    bond-lan:
      interfaces: [enp2s0, enp3s0]
      addresses: [192.168.93.2/24]
      parameters:
        mode: 802.3ad
        mii-monitor-interval: 1
    bond-wan:
      interfaces: [enp1s0, enp4s0]
      addresses: [192.168.1.252/24]
      gateway4: 192.168.1.1
      nameservers:
        search: [local]
        addresses: [8.8.8.8, 8.8.4.4]
      parameters:
        mode: active-backup
        mii-monitor-interval: 1
        gratuitious-arp: 5
    bond-conntrack:
      interfaces: [enp5s0, enp6s0]
      addresses: [192.168.254.2/24]
      parameters:
        mode: balance-rr
        mii-monitor-interval: 1

```
Configuring network bridges

To create a very simple bridge consisting of a single device that uses DHCP, write:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: no
  bridges:
    br0:
      dhcp4: yes
      interfaces:
        - enp3s0

```

---

### Post by wongultraman on 2019-05-21
I have tried networkd and Network Manager; but there seems to be the same for my case.

Should I add "optional: true" to wifis?

---


---
title: "bond MAC address not unique after cloning"
date: 2022-06-15
forum: Networking &amp; Wireless
---

### Post by clarknova on 2022-06-15
Ubuntu Server 20.04.4

I have configured a server with a bond network interface. Netplan looks like this:

```
network:
  version: 2
  renderer: networkd
  ethernets:

    enp129s0f0: {}
    enp129s0f1: {}

  bonds:
    bond0:
      interfaces: [ enp129s0f0, enp129s0f1 ]
      dhcp4: true
      critical: true
      parameters:
         lacp-rate: fast
         mii-monitor-interval: 100
```

I then cloned this host using FOG, and the new host uses the same MAC address on the bond interface as the source host. This is a problem, since it leads to an IP address conflict, even with DHCP enabled.

```
# ifconfig
bond0: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 9000
        inet 10.13.6.29  netmask 255.255.255.0  broadcast 10.13.6.255
        inet6 fe80::3ccd:e5ff:fe1a:d39c  prefixlen 64  scopeid 0x20<link>
        ether 3e:cd:e5:1a:d3:9c  txqueuelen 1000  (Ethernet)
        RX packets 4679  bytes 331717 (331.7 KB)
        RX errors 0  dropped 1320  overruns 0  frame 0
        TX packets 784  bytes 102325 (102.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp129s0f0: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 9000
        ether 3e:cd:e5:1a:d3:9c  txqueuelen 1000  (Ethernet)
        RX packets 705  bytes 47520 (47.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 390  bytes 54220 (54.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp129s0f1: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 9000
        ether 3e:cd:e5:1a:d3:9c  txqueuelen 1000  (Ethernet)
        RX packets 3974  bytes 284197 (284.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 394  bytes 48105 (48.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

I guess the MAC address of the bond interface is being controlled by udevd, but I haven't been able to figure that out, or how to ensure that cloned hosts get a unique MAC address on the bond interface. Would somebody be kind enough to point me in the right direction?

---

### Post by TheFu on 2022-06-16
netplan.io?  Put something like this at the same level in the bond0 stanza as the IPaddress setting:
```
      macaddress: 52:54:00:cc:bb:aa
```

ref: [https://netplan.io/reference/#common-properties-for-all-device-types](https://netplan.io/reference/#common-properties-for-all-device-types)

Using DHCP to manage server IPs has burned lots of people. Best not to do that.

ifconfig is deprecated. Use the **ip** commands, though they generally create uglier output ... still ... after plenty of complaints.

route -n  (human readable)
and
ip route (compressed junk)

---

### Post by clarknova on 2022-06-16
> **TheFu said:**
> netplan.io?  Put something like this at the same level in the bond0 stanza as the IPaddress setting:
```
      macaddress: 52:54:00:cc:bb:aa
```

Thanks, I can use this. It doesn't solve the problem of each cloned host being born with a cloned MAC address on the bond, but at least I can change it after imaging.

> Using DHCP to manage server IPs has burned lots of people. Best not to do that.

Right, but if I'm pushing an image to multiple hosts then static is going to result in IP conflict. With DHCP each host should come up with a unique address and I can change it after imaging. Except, not if the MAC address ends up identical on each host. Ideally the bond interface would get a unique MAC address after imaging, but I don't see a way to get that result other than changing it manually on each host.

> ifconfig is deprecated. Use the **ip** commands, though they generally create uglier output ... still ... after plenty of complaints.

route -n  (human readable)
and
ip route (compressed junk)

Yeah, I guess I'm old. I'll change when the new commands give me a better result than the old ones.

---

### Post by TheFu on 2022-06-16
Dynamic setting on configs shouldn't be hard for each system.  Put the MAC and IPs you want in those dynamic settings.
After all, cloning is "cloning".  That's sorta the point. An exact copy.

There are other issues with cloning, but you'll get to discover those later, I suppose.

OTOH, I don't clone, so this isn't an issue here.

---

### Post by clarknova on 2022-06-20
> **TheFu said:**
> Dynamic setting on configs shouldn't be hard for each system.

That's my hope, that somebody will see this thread and point me in the right direction.

---

### Post by clarknova on 2022-06-23
It turns out the fate of the bond interface's MAC address is bound to the (ostensibly unique) ID found in /etc/machine-id and the related file /var/lib/dbus/machine-id. I added the following to my post-deployment script:
```

# mount our root device
mkdir /mnt/temp
mount /dev/md0 /mnt/temp

# remove the cloned machine ID 
rm /mnt/temp/etc/machine-id
rm /mnt/temp/var/lib/dbus/machine-id

# generate a new machine ID
chroot /mnt/temp dbus-uuidgen --ensure=/etc/machine-id
chroot /mnt/temp dbus-uuidgen --ensure

```

and now all my deployed hosts get their very own machine ID and bond0 MAC address.

---


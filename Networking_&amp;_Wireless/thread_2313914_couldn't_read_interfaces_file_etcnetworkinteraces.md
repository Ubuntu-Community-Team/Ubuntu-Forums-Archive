---
title: "couldn't read interfaces file /etc/network/interaces"
date: 2016-02-16
forum: Networking &amp; Wireless
---

### Post by phluffy2 on 2016-02-16
I'm attempting to add some static IP address to a new ubuntu install. I should start by saying that the system identified my ethernet address as "enx[macaddresshere]" I made the following change :

```
root@phluf:~# cat /etc/udev/rules.d/70-my-network.rules
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="[macaddresshere]", NAME="net0"
```
And it now shows up in my ifconfig -a as 'net0':```
net0      Link encap:Ethernet  HWaddr [macaddresshere]          inet addr:10.24.10.32  Bcast:10.24.10.127  Mask:255.255.255.128
          inet6 addr: fe80::2e0:4cff:fe37:2fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:522845 (522.8 KB)  TX bytes:279346 (279.3 KB)
```The given address, 10.24.10.32 is given via DHCP at boot with no configuration from my side. I'm attempting to get both a public and private address on 'net0'. I've made changes to /etc/network/interfaces:```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


auto net0
iface net0 static
        address 10.24.10.100
        netmask 255.255.255.128
        gateway 10.24.10.1


auto net0:0
iface net0:0 static
        address [public]
        netmask 255.255.255.248
```I've tried this both with and without the subinterface :0, and with and without "auto net0" lines, and with and without netmask lines, adding CIDR notation to the address instead, all to no avail.
With the config file as above ^ when I attempt to run ifdown/ifup, I get:
```
root@phluf:~# ifdown net0 && ifup net0/etc/network/interfaces:6: unknown or no address type and no inherits keyword specified
ifdown: couldn't read interfaces file "/etc/network/interfaces"
```
Permissions look like this:```
root@phluf:~# ls -la /etc/network/interfaces
-rw-r--r-- 1 root root 260 Feb 16 19:59 /etc/network/interfaces
```I'm running commands as root. I googled around a bit and found a few errors with /etc/network/interfaces, but it mostly seemed to be people with typos... I don't SEE a typo in my config, but I'll forehead myself if one is found...
** Sorry for the multiple threads! I'm not sure why 2 were created, and were blank. Hoping this works... **

---

### Post by Dennis N on 2016-02-16
You can easily set up a static ip address starting at the panel networking icon, right-clicking and selecting "Edit Connections"

Here is a post in an past thread describing what to do from there:

[http://ubuntuforums.org/showthread.php?t=1905186&p=11593844#post11593844](http://ubuntuforums.org/showthread.php?t=1905186&p=11593844#post11593844)

---

### Post by phluffy2 on 2016-02-17
Thanks for your reply Dennis. Unfortunately, this is a 'headless system' and I'm reaching it remotely via ssh. I've also removed the gui from this install.

---

### Post by steeldriver on 2016-02-17
The "unknown or no address type" is inet I think

```

iface net0 [COLOR=#0000ff]**inet**[/COLOR] static

```

---

### Post by SeijiSensei on 2016-02-17
Usually when I've used virtual adapters like eth0:0 they have been in the same network subnet as eth0 itself.  I'm not sure you can assign two distinct addresses like you're trying to do.  You might be able to get around this problem by specifying a different gateway address for eth0:0, presumably the upstream router that serves that network subnet.  As it stands now, all the outbound traffic goes to the 10.x router which won't know what to do with the public traffic it receives.

It might also be possible to specify  routing manually, e.g,
```

/sbin/ip route add 10.24.10.0/25 via 10.24.10.1
/sbin/ip route add default via xx.xx.xx.xx

```
where xx.xx.xx.xx is the upstream public router.  If you want all the Internet-bound traffic to go out via 10.24.10.1, you could try reversing those routes making that gateway the default and specifying 
```
/sbin/ip route add xx.xx.xx.xx/29 via xx.xx.xx.xx
```

---

### Post by phluffy2 on 2016-02-20
> **steeldriver said:**
> The "unknown or no address type" is inet I think

```

iface net0 [COLOR=#0000ff]**inet**[/COLOR] static

```All the example sites I've checked have this format. What format are you suggesting? Could you post yours as an example?

> **SeijiSensei said:**
> Usually when I've used virtual adapters like eth0:0 they have been in the same network subnet as eth0 itself.  I'm not sure you can assign two distinct addresses like you're trying to do.  You might be able to get around this problem by specifying a different gateway address for eth0:0, presumably the upstream router that serves that network subnet.  As it stands now, all the outbound traffic goes to the 10.x router which won't know what to do with the public traffic it receives.

It might also be possible to specify  routing manually, e.g,
```

/sbin/ip route add 10.24.10.0/25 via 10.24.10.1
/sbin/ip route add default via xx.xx.xx.xx

```
where xx.xx.xx.xx is the upstream public router.  If you want all the Internet-bound traffic to go out via 10.24.10.1, you could try reversing those routes making that gateway the default and specifying 
```
/sbin/ip route add xx.xx.xx.xx/29 via xx.xx.xx.xx
```
The routing is such that I don't need another default gateway. The public IP is routed from the modem and router down to this box. The setup works if I do:
```
ip addr add [publicip]/32 dev net0
``` but I'm looking to make this persistent between boots.

---

### Post by steeldriver on 2016-02-20
> **phluffy2 said:**
> All the example sites I've checked have this format. What format are you suggesting?

I'm suggesting that yours are missing the inet keyword

```

auto net0
iface net0 static
        [COLOR=#0000ff] ^^^[/COLOR]
        address 10.24.10.100
        netmask 255.255.255.128
        gateway 10.24.10.1

```

---


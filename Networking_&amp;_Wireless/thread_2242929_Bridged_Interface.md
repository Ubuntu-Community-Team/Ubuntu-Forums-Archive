---
title: "Bridged Interface"
date: 2014-09-04
forum: Networking &amp; Wireless
---

### Post by elysian2 on 2014-09-04
Having trouble bridging VMs and containers.

```

auto br0
iface br0 inet static
address 192.168.2.20
gateway 192.168.2.254
netmask 255.255.255.0
dns-nameserver 192.168.2.254
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0

```

```

brctl showstp br0

br0
 bridge id        8000.0800276aca51
 designated root    8000.0800276aca51
 root port           0            path cost           0
 max age          20.00            bridge max age          20.00
 hello time           2.00            bridge hello time       2.00
 forward delay          15.00            bridge forward delay      15.00
 ageing time         300.00
 hello timer           1.58            tcn timer           0.00
 topology change timer       0.00            gc timer         229.02
 flags            

eth0 (1)
 port id        8001            state             forwarding
 designated root    8000.0800276aca51    path cost           4
 designated bridge    8000.0800276aca51    message age timer       0.00
 designated port    8001            forward delay timer       0.00
 designated cost       0            hold timer           0.58
 flags            

```

```

echo "allow br0" > /etc/qemu/bridge.conf
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Neither LXC or QEMU is able connect to the router.

```

lxc.network.type=veth
lxc.network.link=br0
lxc.network.flags=up
lxc.network.name=eth0
lxc.network.mtu=1500

```

```

qemu-system-x86_64 -m 1024 -hda snapshot.qcow2 -vga qxl -cpu host -machine type=pc,accel=kvm -net nic -net bridge,br=br0 -smp 4 -usbdevice tablet -soundhw ac97

```

Is there something I'm missing?

---

### Post by Doug S on 2014-09-05
> **elysian2 said:**
> Having trouble bridging VMs and containers.

```

auto br0
iface br0 inet dhcp
address 192.168.2.20
gateway 192.168.2.254
netmask 255.255.255.0
dns-nameserver 192.168.2.254
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0

```I assume that is only a portion of your /etc/networks/interfaces file. It is odd because br0 is declared as dhcp, yet it then goes on to declare addresses as if it was static. In my case I got my other settings from the [Ubuntu Serverguide]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html#bridging") and never questioned them. Yours are different. Here is my file (all of it):```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Local network interface
auto eth1
iface eth1 inet static
  address 192.168.222.1
  network 192.168.222.0
  netmask 255.255.255.0
  broadcast 192.168.222.255

# The primary network interface and bridge
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
```

---

### Post by elysian2 on 2014-09-05
> **Doug S said:**
> I assume that is only a portion of your /etc/networks/interfaces file. It is odd because br0 is declared as dhcp, yet it then goes on to declare addresses as if it was static. In my case I got my other settings from the [Ubuntu Serverguide]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html#bridging") and never questioned them. Yours are different. Here is my file (all of it):```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Local network interface
auto eth1
iface eth1 inet static
  address 192.168.222.1
  network 192.168.222.0
  netmask 255.255.255.0
  broadcast 192.168.222.255

# The primary network interface and bridge
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
```

Yes, it is set to static. Sorry for the typo while making this thread.

---

### Post by elysian2 on 2014-09-06
Any suggestions?

---

### Post by Doug S on 2014-09-06
What are the ip addresses of your VM's? And are they on the 192.168.2.0 sub-net?
I use dhcp and bridging and my VM's are allocated their IP address from my main router (another ubuntu server).

---

### Post by elysian2 on 2014-09-06
They are set to DHCP but they can't get an IP from the router.

---

### Post by Doug S on 2014-09-06
I have never used the "qemu-system-x86_64" so can not really comment on that. It has been a couple of years, but I did try lxc this afternoon. I made a VM (or whatever one calls it under lxc) BEFORE I edtied /etc/lxc/default.conf, and it always got it IP address from the local pool, even after I edited /etc/lxc/default.conf and then started the VM. However, if I made a new VM then it got its IP address from my main router.

So, the second machine:```
doug@trusty2:~$ [COLOR=#ff0000]ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:16:3e:c1:45:04
          inet addr:[COLOR=#ff0000]192.168.111.9[/COLOR]  Bcast:192.168.111.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1924 (1.9 KB)  TX bytes:1624 (1.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```And the first machine:```
doug@trusty:~$ [COLOR=#ff0000]ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:16:3e:c5:af:5b
          inet addr:[COLOR=#ff0000]10.0.3.44[/COLOR]  Bcast:10.0.3.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1706 (1.7 KB)  TX bytes:1562 (1.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```And the config file (after editing):```
doug@s15:~$ [COLOR=#ff0000]cat /etc/lxc/default.conf[/COLOR]
[COLOR=#ff0000]lxc.network.type = veth
lxc.network.link = br0[/COLOR]
lxc.network.flags = up
lxc.network.hwaddr = 00:16:3e:xx:xx:xx
```

---


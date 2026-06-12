---
title: "No network on VM after migrating to new xen server"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by gabrielqs on 2015-07-22
Hi,

I understand this is question is not completely related to ubuntu, but I hope my experienced ubuntu fellows would help me find a way through this.

I have two XCP servers, running several ubuntu VMs. A couple of days ago, I have migrated one VM from one Xen Server to another. After doing this, this VM is not able to connect to the networks as before. I have kept IP and MAC Addresses intact.
 
After running ifconfig, i can see the interface as follows:
 
```
eth0      Link encap:Ethernet  HWaddr YYY  
          inet addr:XXXX  Bcast:XXXX  Mask:255.255.255.192
          inet6 addr: XXXXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:13614 (13.6 KB)
          Interrupt:68 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3985002 (3.9 MB)  TX bytes:3985002 (3.9 MB)
```
 
 
Bringing down and up the eth0 interface works, as follows:
 
```
root@xx:~# ifdown -v eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/resolvconf
run-parts: executing /etc/network/if-down.d/sendmail
run-parts: executing /etc/network/if-down.d/upstart
run-parts: executing /etc/network/if-down.d/wpasupplicant
ip route del default via XXX metric 100 dev eth0 2>&1 1>/dev/null || true 
ip -4 addr flush dev eth0 label eth0
ip link set dev eth0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/sendmail
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
 
root@xx:~# ifup -v eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
ip addr add XXXX/255.255.255.192 broadcast +   dev eth0 label eth0
ip link set dev eth0   up
 ip route add default via XXXX metric 100 dev eth0 
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
```
 
Routes seem to be in order:
 
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         XXX 0.0.0.0         UG    100    0        0 eth0
XXX 0.0.0.0         255.255.255.192 U     0      0        0 eth
```
 
 
But i still can't start the networking service...
 
```
root@xxx:~# service networking start
networking stop/waiting
```
 
Any hints on how to start solving this? The networking service doesn't give me any kind of hint of what's wrong.
 
Thanks,
Gabriel

---


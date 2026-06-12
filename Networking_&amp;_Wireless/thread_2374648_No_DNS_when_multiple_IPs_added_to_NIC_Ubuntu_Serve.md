---
title: "No DNS when multiple IPs added to NIC Ubuntu Server 16.04"
date: 2017-10-17
forum: Networking &amp; Wireless
---

### Post by patdundee on 2017-10-17
Hi Guys
I have the following config with multiple IPs. However with multiple IPs  my DNS is not working correctly. I can ping IP address's but I cannot  resolve domain names with ping unless i only have a single IP assigned.  Has anyone found a way around this please?

I have tried it with both dns-nameserves added in the interfaces file and with them remmed out.
```

                 auto lo enp17s0
                 iface lo inet loopback

             iface enp17s0 inet static
                 address 109.xxx.xxx.xxx/27
                 gateway 109.xxx.xxx.xxx
                 broadcast 109.xxx.xxx.xxx
                 network 109.xxx.xxx.xxx
                 #dns-nameservers 8.8.8.8 109.xxx.xxx.xxx 109.xxx.xxx.xxx

         iface enp17s0 inet static
                 address 109.xxx.xxx.xxx/27

         iface enp17s0 inet static
                 address 109.xxx.xxx.xxx/27

         iface enp17s0 inet static
                 address 109.xxx.xxx.xxx/27
```

---

### Post by SeijiSensei on 2017-10-18
Are you saying that using "ping hostname" will not return replies but "ping 109.xxx.xxx.xx" does?

Unless you are running your own DNS server, I don't see why you would expect the other names to resolve.  If you are running your own server, you'll obviously need to add "A" records for the other addresses and, if you want to conform to standards, "PTR" records in the reverse zone file for xxx.xxx.109.in-addr.arpa.

Alternatively add entries to /etc/hosts on the clients for the additional IPs.

Now if you mean that assigning other IPs to the same interface breaks outbound DNS, I've not had that problem myself, but I use the traditional method of creating multiple virtual interfaces using ifconfig:

```

/sbin/ifconfig eth0:0 10.10.10.10
/sbin/ifconfig eth0:1 10.10.10.11
[etc.]

```

I don't know how this maps to systemd-based distributions like 16.04

If you use the interfaces file you posted, what do you see from running just "ifconfig" at the terminal prompt?  Do all the virtual interfaces appear with separate addresses?  Please post the output of ifconfig in code tags.

---

### Post by patdundee on 2017-10-18
Hi
I used to be able to use eth0:1 etho:2 ect etc in ubuntu 14.04 but that is not accepted in 16.04

The only way i can add IPS that respond to both internal pings and from pings externally from systems in other locations is as shown above. But as you have seen it does break external DNS as it does not accept the nameserver address's when you have more than one ip. With that it cannot even do an apt update as it cannot resolve any host by domain name. If you put the DNS in the resolvconf it is automatically overwritten and the resolvconf is blank again. 

It is a very strange one. 

Here is the output of ifconfig with the other ips (Which are live) but do not show with ifconfig

```

enp17s0   Link encap:Ethernet  HWaddr 18:a9:05:69:01:38
          inet addr:109.xxx.xxx.xxx  Bcast:109.xxx.xxx.xxx  Mask:255.255.255.224
          inet6 addr: fe80::1aa9:5ff:fe69:138/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:345 errors:0 dropped:10 overruns:0 frame:0
          TX packets:602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28693 (28.6 KB)  TX bytes:95467 (95.4 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:44446 (44.4 KB)  TX bytes:44446 (44.4 KB)


```

---

### Post by patdundee on 2017-10-18
Ok got it to work this way around. If i set the config as follows

```

# The loopback network interface
auto lo enp17s0
iface lo inet loopback

# The primary network interface
iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27
        netmask 255.255.255.224
        network 109.xxx.xxx.xxx
        gateway 109.xxx.xxx.xxx
        dns-nameservers 8.8.8.8 109.xxx.xxx.xxx 109.xxx.xxx.xxx

iface enp17s0 inet static
address 109.xxx.xxx.xxx/27
dns-nameservers 8.8.8.8 109.xxx.xxx.xxx 109.xxx.xxx.xxx

iface enp17s0 inet static
address 109.xxx.xxx.xxx/27
dns-nameservers 8.8.8.8 109.xxx.xxx.xxx 109.xxx.xxx.xxx

iface enp17s0 inet static
address 109.xxx.xxx.xxx/27
dns-nameservers 8.8.8.8 109.xxx.xxx.xxx 109.xxx.xxx.xxx

```
everything works fine even after a reboot. All IPs respond internal and external and I can resolve both host names and ip address's.

However if i run 
```
ifdown enp17s0 && ifup enp17s0
```

I get the following result, even though everything works correctly
```

RTNETLINK answers: Cannot assign requested address
RTNETLINK answers: Cannot assign requested address
RTNETLINK answers: Cannot assign requested address

```

I suppose i can live with that until i found out why :)

---


---
title: "LAN works, Internet doesn't"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by famousdrew on 2007-01-30
Ok, here my situation. It's a Dell 1450SC server with dual gigabit cards. The server is online via dhcp right now and it works fine inside the local area network. It will not ping outside nor will it connect to any Internet servers. I have tried setting static IP addresses with both our internal DNS servers and using our ISPs DNS servers, neither have worked. 

Inside network == good
Outside network == bad

I checked the firewall - it's a Watchguard Edge 55e (10,000 concurrent connections, we're using about 40) and I don't see a reason it would block this activity. I'm using SSH to connect to the server and from this Windows station I can browse the web with similar settings I'm assigning to the server in static IP mode. Again, neither DHCP nor static IPs let me get outside, both work inside.

I just went to copy this info and it is in static mode right now.

Some info:

```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:20:AD:EE
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe20:adee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:3819173 (3.6 MiB)  TX bytes:3748843 (3.5 MiB)
          Base address:0xecc0 Memory:dfde0000-dfe00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1254 (1.2 KiB)  TX bytes:1254 (1.2 KiB)
```



```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

---

### Post by famousdrew on 2007-01-30
A couple additional questions - could there be any kind of software firewall that Ubuntu installs automagically? This is a new server install today of 6.10.  Am I missing something obvious? I've read through these forums and haven't seen anything about additional steps to get online...

Thanks guys.

---

### Post by famousdrew on 2007-01-31
I've found that if I assign a DNS server from outside the network such as that of our ISP I get less results than using our internal DNS. The Internal DNS server at least lets me resolve domain names to IPs but won't let me ping or browse outside the LAN.

---

### Post by dartakaum on 2007-02-05
i'm in the same situation has you...

This happen after i upgrade some gnome apps...

---


---
title: "Dapper Laptop as wired to wireless bridge, works but unable to browse SMB shares"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by Jaidee on 2006-08-27
Hello all,

I've followed the instructions found [here]("https://help.ubuntu.com/community/WifiDocs/WirelessLaptopInternetAccessPoint") regarding using Firestarter to bridge a wired connnection into my wireless network. I've got my linux running XBox wired to my laptop, which then bridges eth0 (wired) to eth1 (wireless), and both can access the internet correctly.

I would ideally like to browse the various XP machines on my home network by Samba, but, as per the guide, the XBox  and thus eth0 are on a different subnet to the rest of the network, and I don't think Samba likes this.

Here's my ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:00:F0:87:09:E4
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:f0ff:fe87:9e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22119 (21.6 KiB)  TX bytes:54643 (53.3 KiB)
          Interrupt:10 Base address:0x6800

eth1      Link encap:Ethernet  HWaddr 00:04:23:61:6D:D6
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe61:6dd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13359333 (12.7 MiB)  TX bytes:83394705 (79.5 MiB)
          Interrupt:5 Base address:0xa000 Memory:c0000000-c0000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39965 (39.0 KiB)  TX bytes:39965 (39.0 KiB)

```

As you can see, eth0 is on the 192.168.1.x subnet, and eth1 is on 192.168.0.x 

My XBox has IP 192.168.1.2, and uses 192.168.1.1 as the gateway. As I say, internet works great, but no SMB!

Any ideas if there's a way to bridge the connections without having to make seperate subnets?

Cheers, JD.

---


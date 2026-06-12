---
title: "unable to find wireless network (however can with livecd)"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by spudtheimpaler on 2007-05-07
Hi.

I have Kubuntu 7.04. I had tried the live cd and was very happy with it so went ahead with the install... 

For my router I have an Orange Livebox. I have disarmed any wap/wep security and the need to 'pair' with the device. When using the live cd the network was found straight away and I could connect with ease. Since installing, however, I can no longer find the network (This is all using KNetworkManager which comes with KDE).

I am dual booting with xp, and that also finds the network well enough.

I have searched the forums (though with pretty vague search terms) and found nothing, though apparently the results of sudo lshw -class network might help troubleshoot:

```
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:d0:5f:38
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-f                                                  d autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 d                                                  uplex=full ip=192.168.1.12 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MI                                                  I speed=100MB/s
       resources: ioport:3000-30ff iomemory:e0200800-e02008ff irq:22
  *-network
       description: HFA384x/IEEE
       product: Version 01.02
       vendor: INTERSIL
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:72:00:20:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=0.8.3                                                   ip=192.168.1.14 multicast=yes wireless=IEEE 802.11b

```

I can connect to the router via ethernet well enough, but that isn't really a long term option so I'd be glad for any help you could give. Obviously if you need any more info, outputs etc please let me know.

Like I said, this worked fine using the kubuntu live cd, so that might help.

Kind Regards,
Mitch.

(Whilst not a total beginner, please feel free to treat me as such, I'd rather it was clear :))

---

### Post by spudtheimpaler on 2007-05-07
the results of ifconfig in case they are of any use:

```

eth0      Link encap:Ethernet  HWaddr 00:02:3F:D0:5F:38
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fed0:5f38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4203 (4.1 KiB)  TX bytes:13966 (13.6 KiB)
          Interrupt:22 Base address:0x800

eth1      Link encap:Ethernet  HWaddr 00:02:72:00:20:CE
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:72ff:fe00:20ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2750993 (2.6 MiB)  TX bytes:672161 (656.4 KiB)
          Interrupt:3 Base address:0x3100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-02-72-00-20-CE-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2833541 (2.7 MiB)  TX bytes:672161 (656.4 KiB)
          Interrupt:3 Base address:0x3100

```

eth1 is the wireless by the way, eth0 being the ethernet

---

### Post by spudtheimpaler on 2007-05-07
*cough* bump *cough*

---

### Post by spudtheimpaler on 2007-05-07
Grrr.

Now it appears that the livecd will no longer load. Neither in start/install mode or in check for faults mode...

---

### Post by spudtheimpaler on 2007-05-07
OK - well...

I have downloaded and burnt the Ubuntu (not Kubuntu) disc.

Guess what?! The wireless works fine using the Ubuntu livecd, but having just installed the ubuntu in place of Kubuntu and guess what?! The wireless isn't found!

I would really appreciate some assistance with this. Any ideas?!

Regards,
Mitch.

---


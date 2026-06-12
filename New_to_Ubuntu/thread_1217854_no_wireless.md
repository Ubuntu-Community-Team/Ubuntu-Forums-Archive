---
title: "no wireless"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-07-20
hi, i own a lenovo x200 tablet pc. i've done a fresh install of ubuntu 9.04 3 or 4 times on this computer. each time, it recognized my wireless automatically. 

however, this time, there ubuntu did not recognize my wireless card. it's not that it isn't working, it's as if it doesn't exist at all. the card doesn't appear under ifconfig. iwconfig returns no wireless devices. 

the only reason for this i can think of is that i had my physical wireless switch turned off during the last install (which was 2 days ago). i just turned on my wireless for the first time, and i noticed this problem.

what should i do? thanks

edit:

ifconfig ==>

```

eth0      Link encap:Ethernet  HWaddr 00:1f:16:10:5a:ca  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe10:5aca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1985717 (1.9 MB)  TX bytes:167187 (167.1 KB)
          Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:324 (324.0 B)  TX bytes:324 (324.0 B)

```

sudo lshw -C network ==>

```

  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:10:5a:ca
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.8-3 ip=192.168.0.4 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:a0:4c:e1:dd:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by diablo75 on 2009-07-20
Do you happen to know what kind of wireless adapter you have?  The model number, that is.  You might check the bottom of the laptop; often there is a label that shows the adapters MAC address as well as what kind of adapter it actually is.

You also might try shooting in the dark and hooking the laptop up to an ethernet connection to the Internet to download all available updates, restart the PC, and see if it helps.  Also check the System>Administration>Hardware Drivers applet to see if any need to be enabled for the adapter (do that after updates).

---


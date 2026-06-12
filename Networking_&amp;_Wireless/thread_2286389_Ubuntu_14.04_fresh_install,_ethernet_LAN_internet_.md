---
title: "Ubuntu 14.04 fresh install, ethernet LAN internet not working"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by arbondz on 2015-07-11
I just built my first PC and installed the latest version of Ubuntu as its primary operating system.  I have the computer connected directly to the router using an ethernet cable that I have verified can does connect to the internet using another computer.  The PC is not connecting to the internet. The PC does not have the ability to connect with wifi.

[COLOR=#111111][FONT=Ubuntu]I am running an AMD 8320 and a gigabyte-990fxa-ud3. Also no sound coming out of the HDMI, though I am not sure if that is related.
[/FONT][/COLOR]
here is the output to sudo lshw -C network

```

robert@robspc:~$ sudo lshw -C network
[sudo] password for robert: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: fc:aa:14:e1:40:76
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:73 ioport:b000(size=256) memory:fe100000-fe100fff memory:d2100000-d2103fff
```

here is the output to sudo ifconfig -a

```

robert@robspc:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr fc:aa:14:e1:40:76  
          inet6 addr: fe80::feaa:14ff:fee1:4076/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:188 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:90 (90.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18705 (18.7 KB)  TX bytes:18705 (18.7 KB)
```

Thanks for any help you can give

---

### Post by PaulW2U on 2015-07-11
Hi arbondz, I took the liberty or removing some formatting and added some code tags for your terminal output for better readability.

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by arbondz on 2015-07-11
Thanks Paul :)

---


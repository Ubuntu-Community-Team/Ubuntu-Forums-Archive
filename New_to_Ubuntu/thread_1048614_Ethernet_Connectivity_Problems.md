---
title: "Ethernet Connectivity Problems"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by thehonorableflamingo on 2009-01-23
I just installed Ubuntu, and it has worked great so far.  However, I can't seem to get connected to the internet.  The same ethernet connection is working fine on a different computer.

It is configured to connect automatically, and when I plug in the cable, it acts as though it is trying to connect, and gives the message 'Requesting a network address from the wired network', but it is never able to finish connecting.

I have tried some of the suggestions from other places on this site, but I have had no luck so far.

Any suggestions are appreciated.

---

### Post by yeats on 2009-01-23
Okay - I'm assuming you've ruled out a bad cable . . . .

Open a terminal and do:

```
ifconfig
```

and post the results here.  That will help others get started helping you.

---

### Post by thehonorableflamingo on 2009-01-23
Thanks for the reply.

When I type 'ipconfig' into the terminal, I get the following message:

bash: ipconfig: command not found

I'm not sure if this helps at all.  Thanks again.

---

### Post by cjv8888 on 2009-01-23
It is

ifconfig not ipconfig

---

### Post by thehonorableflamingo on 2009-01-23
Oops, my mistake.  I am still thinking in terms of Windows I suppose, and didn't read the post that clearly.

I typed 'ifconfig', and here is the entry.

ath0      Link encap:Ethernet  HWaddr 00:19:7e:34:a4:9e  
          inet6 addr: fe80::219:7eff:fe34:a49e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:15:58:83:a6:30  
          inet6 addr: fe80::215:58ff:fe83:a630/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:542840 (542.8 KB)  TX bytes:2178 (2.1 KB)
          Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7E-34-A4-9E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72874 errors:0 dropped:0 overruns:0 frame:18945
          TX packets:517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:6564221 (6.5 MB)  TX bytes:23782 (23.7 KB)
          Interrupt:17 


Thanks in advance for any advice.

---

### Post by cjv8888 on 2009-01-23
please also post

```
lspci
```

```
sudo lshw -C network
```

---

### Post by thehonorableflamingo on 2009-01-24
Thanks for the reply.

Here is the 'lspci' entry.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

And the 'sudo lshw -C network'.

  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:83:a6:30
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.5-1 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:34:a4:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:f2:f7:49:73:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---


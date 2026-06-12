---
title: "[SOLVED] Intel 82562 and 8.04"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by ComputingFroggy on 2008-07-28
Hello,

I have installed a Ubuntu Hardy Heron (v 8.04) on a small computer with supposedly an Ethernet chipset Intel 82562.

However when running lspci -nn I get the line 
Ethernet controler [0200]: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet COntroler [8086:103a] (rev 82)

Anyway, I don't know what to do ?
Should I follow the intructions at 
[http://ubuntuforums.org/showthread.php?p=3370406](http://ubuntuforums.org/showthread.php?p=3370406)

I would have thought Hardy Heron would correct this problem using the latest driver ! ? !

I intended to post on the above named thread... but i's read-only now.


cheers,
L@u
The Computing Froggy

---

### Post by ComputingFroggy on 2008-07-29
Hi,

I was told (by noob12) that the thread quoted above does not apply.

Also I found strange that in the lspci command, the chipset 82801DB is listed as the ethernet network device when this is apparently a sound device, and on my machine the ethernet chipset is 82562ET.

Anybody could help ?

Here are the commands I have tried and their result !

```
# modinfo e100 | grep 103A
alias:          pci:v00008086d0000103Asv*sd*bc02sc00i*


# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (CNR) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 82
       serial: 00:07:32:0a:1c:7c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

# lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 82)


# lspci -n
00:00.0 0600: 8086:3580 (rev 02)
00:00.1 0880: 8086:3584 (rev 02)
00:00.3 0880: 8086:3585 (rev 02)
00:02.0 0300: 8086:3582 (rev 02)
00:02.1 0380: 8086:3582 (rev 02)
00:1d.0 0c03: 8086:24c2 (rev 02)
00:1d.1 0c03: 8086:24c4 (rev 02)
00:1d.7 0c03: 8086:24cd (rev 02)
00:1e.0 0604: 8086:244e (rev 82)
00:1f.0 0601: 8086:24c0 (rev 02)
00:1f.1 0101: 8086:24cb (rev 02)
00:1f.3 0c05: 8086:24c3 (rev 02)
00:1f.5 0401: 8086:24c5 (rev 02)
01:08.0 0200: 8086:103a (rev 82)

```


Thanks,
L@u

---

### Post by ComputingFroggy on 2008-07-29
Me again ! ;-)

I have tried to download the driver from Intel (e1000) and followed the instructions ... to no effect.

Find here more commands giving info on the system:
One will see, in the dmesg output there's definitely a problem with e100 ... and that the new driver downloaded from Intel (e1000) is not used ! !

As usual, any ideas are welcome !


Cheers,
L@u


```
# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:07:32:0a:1c:7c  
          adr inet6: fe80::207:32ff:fe0a:1c7c/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:1104 (1.0 KB)

# ethtool -i eth0
driver: e100
version: 3.5.23-k4-NAPI
firmware-version: N/A
bus-info: 0000:01:08.0

# dmesg |grep e100
[   16.002863] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   18.805258] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   18.805263] e100: Copyright(c) 1999-2006 Intel Corporation
[   18.807845] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e100
[   19.059171] e100: eth0: e100_probe: addr 0xe8000000, irq 19, MAC addr 00:07:32:0a:1c:7c
[   41.024319] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   43.022753] e100: eth0: e100_watchdog: link down
[   51.015578] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   53.014047] e100: eth0: e100_watchdog: link down
[  112.961409] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  114.959852] e100: eth0: e100_watchdog: link down
[  164.915982] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  166.914419] e100: eth0: e100_watchdog: link down
[  216.870546] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  218.868986] e100: eth0: e100_watchdog: link down
[  268.825113] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  270.823555] e100: eth0: e100_watchdog: link down
[  310.788419] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  312.786857] e100: eth0: e100_watchdog: link down
[  340.946046] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  342.944498] e100: eth0: e100_watchdog: link down
[  350.937312] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  352.935748] e100: eth0: e100_watchdog: link down
[  392.900615] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  394.899058] e100: eth0: e100_watchdog: link down
[  402.891891] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  404.890325] e100: eth0: e100_watchdog: link down
[  454.846448] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  456.844935] e100: eth0: e100_watchdog: link down
[  464.837711] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  466.836150] e100: eth0: e100_watchdog: link down
[  506.801015] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  508.799452] e100: eth0: e100_watchdog: link down
[  516.792276] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  518.790719] e100: eth0: e100_watchdog: link down
[  558.755587] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  560.754020] e100: eth0: e100_watchdog: link down
[  568.746845] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  570.745285] e100: eth0: e100_watchdog: link down
[  610.710151] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  612.708587] e100: eth0: e100_watchdog: link down
[  682.647245] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  684.645681] e100: eth0: e100_watchdog: link down
[  702.629773] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  704.628212] e100: eth0: e100_watchdog: link down
[  744.593074] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  746.591514] e100: eth0: e100_watchdog: link down
[  796.547642] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  798.546083] e100: eth0: e100_watchdog: link down
[  848.502209] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  850.500652] e100: eth0: e100_watchdog: link down
[  868.484737] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  870.483180] e100: eth0: e100_watchdog: link down
[  930.430577] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  932.429009] e100: eth0: e100_watchdog: link down
[  982.385159] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  984.383577] e100: eth0: e100_watchdog: link down
[ 1024.348440] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1026.346881] e100: eth0: e100_watchdog: link down
[ 1034.339731] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1036.338141] e100: eth0: e100_watchdog: link down
[ 1076.303007] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1078.301450] e100: eth0: e100_watchdog: link down
[ 1086.294274] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1088.292710] e100: eth0: e100_watchdog: link down
[ 1128.257576] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1130.256016] e100: eth0: e100_watchdog: link down

```

---

### Post by noob12 on 2008-07-29
Due to time constraints I can't commit to sticking with this thread, but here's what I can see.  The device is identified properly as an ethernet controller.  Your lshw output shows that the e100 driver has claimed the device just fine.  The configuration line of the lshw output indicates there is no link detected on the ethernet.

Check the condition of the cable and the physical connection (is the ethernet cable properly plugged in on both sides).  Try swapping a known good cable with the one that you have.  

Check the output of the commands > dmesg and > tail /var/log/kern.log for any errors related to the e100 driver or eth0 device.  If you see anything interesting, post it.

---

### Post by ComputingFroggy on 2008-07-29
Hi,

Well done noob12 !

Indeed the problem was with the cable ! !
Strangely, this cable works with a computer 30cm away but not with the new one (which is 30cm upper).
As the cable is brand new, it never occurred to me it could be faulty !! !!

Thanks for your help.

I am still puzzled why the Ethernet device is listed as 82801DB PRO/100 VE (CNR) Ethernet Controller instead of 82562 ... but now it works, that's the main point.


Thanks again,
L@u

---


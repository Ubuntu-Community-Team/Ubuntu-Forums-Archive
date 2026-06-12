---
title: "wlan0 not showing on ifconfig - BCM4311/Ubuntu 10.04/Acer TravelMate5520"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by desatonao on 2013-12-08
Hi!

I've trying for days, following many instructions for the web, to get my wireless working. I've tried repeatedly with some drivers: with b43 with no success; with wl I could see the networks through WICD, but impossible to connect, and still not showing wlan0, to try at least through terminal.

The last try with ndiswrapper, the controller is bcmwl5. I've followed all the steps from here: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) stoping in the 4th one, after deactivating all others drivers and with ndiswreapper module loaded, the hardware and the driver are still not meeting.

After wasting a lot of hours, googling a lot and trying all what is possible (I really did my best), I pray for help.

Here I paste the recomended data for those issues. Thanks in advance!

lspci -nn | grep BCM:
```
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

ifconfig:
```
eth0      Link encap:Ethernet  direcciónHW 00:16:d3:e1:37:7a  
          Direc. inet:192.168.1.39  Difus.:192.168.1.255  Másc:2
          Dirección inet6: fe80::216:d3ff:fee1:377a/64 Alcance:E
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métri
          Paquetes RX:4316 errores:0 perdidos:0 overruns:0 frame
          Paquetes TX:4257 errores:0 perdidos:0 overruns:0 carri
          colisiones:0 long.colaTX:1000 
          Bytes RX:3911920 (3.9 MB)  TX bytes:610629 (610.6 KB)
          Interrupción:16 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)
```

iwconfig wlan0:
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```


lsmod | grep "wlan_module_name":
```
ndiswrapper           184709  0 
```

dmesg | grep ndiswrapper:
```
[   18.177370] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   19.215578] usbcore: registered new interface driver ndiswrapper
```

sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:16:d3:e1:37:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.39 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:f0200000-f0203fff ioport:a000(size=256) memory:84000000-8401ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0300000-f0303fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:26:02:fe:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```


sudo iwlist wlan0 scan:
```
wlan0     Interface doesn't support scanning : Network is down
```

lsb_release -d:
```
Description:    Ubuntu 10.04.4 LTS
```

uname -mr:
```
2.6.32-52-generic i686
```

sudo service networking restart:
```
restart: Unknown instance: 
```

---


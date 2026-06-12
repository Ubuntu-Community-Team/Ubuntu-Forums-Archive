---
title: "Broadcasting on 0.0.0.1"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by einnar on 2008-07-14
I've been told by my ISP that I am broadcasting on 0.0.0.1, but I'm not seeing it. Any help would be appreciated.

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ChapWireless 9517-18"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:20:A6:5B:9A:D0   
          Bit Rate=54 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=85/100  Signal level=-49 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:d6:9c:cf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:9b:69:99
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=65.124.17.75 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
```

```
lscpi
bash: lscpi: command not found
einnar@Meili:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
```


And for good measure, a bit of : 

```
dmesg | grep wlan0
[ 7487.120281] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7487.319997] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7491.724253] wlan0: Initial auth_alg=0
[ 7491.724260] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7491.724285] wlan0: Initial auth_alg=0
[ 7491.724288] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7491.920956] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7492.120671] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7492.320382] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7496.724636] wlan0: Initial auth_alg=0
[ 7496.724643] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7496.724760] wlan0: Initial auth_alg=0
[ 7496.724763] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7496.921365] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7497.121051] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7497.320760] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7501.725252] wlan0: Initial auth_alg=0
[ 7501.725263] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7501.725541] wlan0: Initial auth_alg=0
[ 7501.725549] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7501.921773] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7502.121411] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7502.321114] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7506.725851] wlan0: Initial auth_alg=0
[ 7506.725862] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7506.726007] wlan0: Initial auth_alg=0
[ 7506.726013] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7506.922112] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7507.121853] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7507.321506] wlan0: authentication with AP 00:20:a6:5b:9a:d0 timed out
[ 7511.726524] wlan0: Initial auth_alg=0
[ 7511.726532] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7511.726554] wlan0: Initial auth_alg=0
[ 7511.726557] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7511.731958] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 7511.731963] wlan0: authenticated
[ 7511.731967] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 7511.732756] wlan0: authentication frame received from 00:20:a6:5b:9a:d0, but not in authenticate state - ignored
[ 7511.735401] wlan0: RX deauthentication from 00:20:a6:5b:9a:d0 (reason=6)
[ 7511.735405] wlan0: deauthenticated
[ 7512.733266] wlan0: authenticate with AP 00:20:a6:5b:9a:d0
[ 7512.736922] wlan0: RX authentication from 00:20:a6:5b:9a:d0 (alg=0 transaction=2 status=0)
[ 7512.736928] wlan0: authenticated
[ 7512.736932] wlan0: associate with AP 00:20:a6:5b:9a:d0
[ 7512.744667] wlan0: RX ReassocResp from 00:20:a6:5b:9a:d0 (capab=0x421 status=0 aid=3)
[ 7512.744676] wlan0: associated
```


Thanks in advance.
If there is anything else you see, please let me know.

Einnar

---

### Post by pytheas22 on 2008-07-15
What is the output of:
```

ifconfig
```

---

### Post by einnar on 2008-07-15
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1B:38:D6:9C:CF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1D:E0:9B:69:99  
          inet addr:65.124.17.75  Bcast:65.124.19.255  Mask:255.255.252.0
          inet6 addr: fec0::e:21d:e0ff:fe9b:6999/64 Scope:Site
          inet6 addr: 2002:417c:1314:e:21d:e0ff:fe9b:6999/64 Scope:Global
          inet6 addr: fe80::21d:e0ff:fe9b:6999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:369958 (361.2 KB)  TX bytes:26610 (25.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-9B-69-99-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by pytheas22 on 2008-07-17
> wlan0     Link encap:Ethernet  HWaddr 00:1D:E0:9B:69:99  
          inet addr:65.124.17.75  **Bcast:65.124.19.255**  Mask:255.255.252.0
          inet6 addr: fec0::e:21d:e0ff:fe9b:6999/64 Scope:Site
          inet6 addr: 2002:417c:1314:e:21d:e0ff:fe9b:6999/64 Scope:Global
          inet6 addr: fe80::21d:e0ff:fe9b:6999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:369958 (361.2 KB)  TX bytes:26610 (25.9 KB)

Your broadcast address looks alright to me.  Why does your ISP think there's something wrong with it?

---


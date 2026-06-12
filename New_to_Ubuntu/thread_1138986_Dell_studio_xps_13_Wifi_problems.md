---
title: "Dell studio xps 13 Wifi problems"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by nynoah on 2009-04-26
Ok I am typing on my old laptop.  I have a strange problem with my new Dell xps studio 13.  The Wifi driver on it is not working correctly.  I can get my wifi to work but for some reason the signal is EXTREMELY weak.  I can get a great signal when I boot into windows.  So I know it is not a card issue but rather a driver issue.  Even then the signal on my old lap top is really strong.  On my old laptop.  I have 4 out of 5 bars.  On my Dell xps I have next to NONE.  It takes like 10 mins to even get it to get a lock.  Does anyone know what I can do to fix this.  Should I try to use Ndiswrapper to install the windows driver.  This problem is also present in Kubuntu too.

This is for Ubuntu 9.04

Any suggestions?
Thanks

---

### Post by nynoah on 2009-04-26
This the card I have that is listed on the Dell site.

Wireless Networking Cards
Dell Wireless 1510 802.11n Half Mini-Card

---

### Post by nynoah on 2009-04-27
help?

---

### Post by nynoah on 2009-04-27
help

---

### Post by nynoah on 2009-04-27
Could I possible have static in the antenna?  Could I have more than one driver conflicting?  Any ideas?  Help me brain storm to solve this.... please

---

### Post by nynoah on 2009-04-27
rachele@rachele-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:dd:a6:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63312 (63.3 KB)  TX bytes:63312 (63.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:62:47:13  
          inet addr:192.168.1.137  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe62:4713/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:624335 (624.3 KB)  TX bytes:154097 (154.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-62-47-13-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rachele@rachele-laptop:~$ 




and the iwconfig says

rachele@rachele-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"miranda"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by nynoah on 2009-04-27
Ok I noticed I am getting TONS of error messages for this

***ath9k_config: Unable to set channel***

This mean anything to anyone?

---

### Post by coffeeaddict22 on 2009-04-28
Can you also post the output of ```
lshw -C network
```

---

### Post by nynoah on 2009-04-28
rachele@rachele-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:dd:a6:34
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:62:47:13
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.137 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f6:0b:ad:43:88:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
rachele@rachele-laptop:~$

---

### Post by nynoah on 2009-04-28
rachele@rachele-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:dd:a6:34
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:62:47:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.137 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:0b:ad:43:88:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
rachele@rachele-laptop:~$

---

### Post by coffeeaddict22 on 2009-04-28
2 options; one quick, one not so quick.
You can try 
```
sudo ifconfig down
``` followed by
```
sudo ifconfig up
```; if that doesn't work you're going to have to change the driver.
Have a look at [http://ubuntuforums.org/showpost.php?p=5711824&postcount=6]("http://ubuntuforums.org/showpost.php?p=5711824&postcount=6")
It looks like the atheros cards don't play well with a 64-bit kernel, so you'll have to upgrade to the madwifi driver to get it working properly.
wmaster0 is a "dummy" interface the kernel creates for your wifi; it's grabbing your network interface, which is a good indication the driver isn't playing.

---


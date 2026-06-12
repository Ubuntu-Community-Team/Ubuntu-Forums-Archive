---
title: "tp link wn321g-ubuntu 10.10 problem"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by imamsibli on 2011-03-18
hi .....
my name is imam. i from indonesia. sorry my english is not good.

i use tohiba l510 include realtek wifi adapter. realtek adapter can connect hotspot but tp link usb adapter  cant.

the problem with my ubuntu 10.10 and usb wifi tp link wn321g, like this :

[COLOR=Red]imim2011@imim:~$ dmesg | grep rt2
[   16.122285] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.130967] usbcore: registered new interface driver rt2870

imim2011@imim:~$ iwconfig[/COLOR] [COLOR=Red]
lo        no wireless extensions.

eth0      no wireless extensions.[/COLOR] [COLOR=Red]

wlan0     802.11bg  ESSID:"DINAS PERTANIAN"  Nickname:"rtl8191SEVA2"[/COLOR] [COLOR=Red]
          Mode:Managed  Frequency=2.462 GHz  Access Point: 68:7F:74:35:10:80   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/100  Signal level=-71 dBm  Noise level=-101 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     Ralink STA  ESSID:""  [/COLOR] [COLOR=Red]
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

imim2011@imim:~$ sudo lshw -C network[/COLOR] [COLOR=Red]
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:69:c7:e4
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10MB/s
       resources: irq:19 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: b4:82:fe:8f:8f:94
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE  driverversion=0019.1207.2010 firmware=63 ip=192.168.1.108 latency=0  link=yes multicast=yes wireless=802.11bg
       resources: irq:10 ioport:2000(size=256) memory:94400000-94403fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=Ralink STA[/COLOR]

thanks for your help.

---


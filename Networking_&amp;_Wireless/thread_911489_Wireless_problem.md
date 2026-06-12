---
title: "Wireless problem"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by gera9 on 2008-09-05
first of all, hi to everyone im new on ubuntu and i had network manager and it worked fine with my home wireless network but then i tried to install wicd but at the end of the installation a window appeared saying that the program wont run properly because something was missing, so i uninstalled it and then i installed again network manager and now i cant connect to my wireless network, wicd screwed the interface, how can i restore all again? and how can i restore network manager applet?

---

### Post by imdano on 2008-09-05
It's not exactly clear what your problem is, but if it's just that the network manager applet is missing, ```
sudo apt-get install nm-applet
``` should do the trick...

---

### Post by gera9 on 2008-09-05
sorry, my problem is that network manager detects my wireless network but i cant connect to it. 

when i type sudo iwconfig that's what appears:


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"INFINITUM7541"  Nickname:"INFINITUM7541"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1E:C7:62:30:91   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Encryption key: on
          Power Management: off
          Link Quality=100/100  Signal level=-17 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and when i try to configure wlan0 a window appears saying "interface doesn't exists"

---

### Post by gera9 on 2008-09-05
and when i type lshw -C network

*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:66:94:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.71 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:8b:d7:f4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by imdano on 2008-09-05
That all looks normal.  Have you rebooted since you reinstalled NM?  Wicd doesn't alter any existing device configuration files, so I don't think that's the cause of the problem you're seeing.  All it does is make ifconfig/iwconfig/wpa_supplicant calls to make and monitor connections.

After you reboot, if you're still having trouble, post the output of ifconfig as well.  Also, you mentioned that when you try to configure wlan0, you get a message saying the interface doesn't exist.  What program are you trying to configure it with?

And finally (somewhat unrelated) do you remember what the window said was missing after you installed wicd?  Did it appear when you tried to run wicd or just when installation finished?  Did you install wicd from a .deb or through the apt repo?

---


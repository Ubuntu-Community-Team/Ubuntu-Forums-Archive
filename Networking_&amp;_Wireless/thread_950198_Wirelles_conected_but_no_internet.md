---
title: "Wirelles conected but no internet"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by nick937 on 2008-10-16
I had hardy heron for awhile and it didnt work for the past month on this particular wireless network. Once I upgraded to Intrepid, the problem was fixed. I recently updated intrepid, and now the problem is back again. Every other wireless network works besides this one.
here is my info when I am connected to the network:


[IMG]http://d.imagehost.org/0820/info.jpg[/IMG]


```

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:1b:7_:5_:5_:00  
          inet addr:163.118.158.111  Bcast:163.118.204.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9638 (9.6 KB)  TX bytes:4680 (4.6 KB)


/////////////////
nick@t00r:~$ sudo lshw -C network
[sudo] password for nick: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:7_:5_:5_:7_
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=163.118.158.111 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:_4:_9:6c:_4
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vnet0
       serial: fe:78:07:64:4a:14
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=yes multicast=yes
nick@t00r:~$ 

////////////////////

iwconfig:

wlan0     IEEE 802.11abg  ESSID:"fit"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:E6:47:44:01   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=95/100  Signal level:-33 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
/////////////////

```

---

### Post by nick937 on 2008-10-16
yes I know I wrote "Wirelles" instead of "Wireless". I did not realize this until after I submitted it. I also wrote "conected". I should probably read what I type from now on..

---

### Post by mikewolf on 2008-10-17
I have the same problem jsut like yours. I have not use the networkmanager, but the "networking".

I can even ping the website of the internet, but I cant use the synaptic package manager or any other internet software.

---

### Post by nick937 on 2008-10-17
I also got rid of network manager and tried WICD, I have the same problem.

---

### Post by superprash2003 on 2008-10-17
are you able to ping your router?? or ping google?

---

### Post by nick937 on 2008-10-17
> **superprash2003 said:**
> are you able to ping your router?? or ping google?

No, the only thing I can ping is my ip (163.118.158.111).
Also, I tried booting up on a Live Cd (to maybe see if it was some of my settings), and it does the same thing. Everyone else who connects to this AP, who does not have linux, can connect to it perfectly fine.

I tried talking to my schools tech support and they said it was because my 
"default route IP" was from 163.118.159.xxx when it should be from 163.118.158.xxx...... 

What I dont understand is how it was working fine, and then I updated ibex, and its broken now

---

### Post by nick937 on 2008-10-17
any ideas??

---

### Post by Squish on 2008-10-17
I had this problem under a wep network

It was configured really strangely, and now has been fixed. I was going through multiple access points, and multiple routers. Once they just rebooted setting, reset up the network to a simpler interface, I was able to gain access.

---

### Post by nick937 on 2008-10-19
> **Squish said:**
> I had this problem under a wep network

It was configured really strangely, and now has been fixed. I was going through multiple access points, and multiple routers. Once they just rebooted setting, reset up the network to a simpler interface, I was able to gain access.

Was everyone else without linux able to connect to it?? Because the AP is from my school, and most everyone uses windows to connect to it (and it works with windows)...

---

### Post by nick937 on 2008-10-21
it has to be an ubuntu problem, im not sure what though.

---


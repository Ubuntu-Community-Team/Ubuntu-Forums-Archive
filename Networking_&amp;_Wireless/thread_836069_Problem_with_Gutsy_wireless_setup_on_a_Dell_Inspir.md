---
title: "Problem with Gutsy wireless setup on a Dell Inspiron 6400 laptop"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by wwastro on 2008-06-21
I recently installed Ubuntu 7.10 on the above laptop (I'm a newbie to Ubuntu!), which normally requires a wireless connection to the internet. I have attempted to set this up with online guidance - using a static IP address etc, but so far have failed to make a connection. Details:

1) The laptop can see the router OK - IP address, SSID, DNS addresses etc. It successfully pings the router, and the WiFi light is on continuously (but not in the present session, in which I am relying on a temporary ethernet connection).

2) Ubuntu is using a "restricted" Windows driver for the wireless card (I am not sure what this means, however).

3) My current results from sudo lshw -C network:

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:94:65:62
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.3 latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:bd:3e:2f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.4 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s

4) My ifconfig results from yesterday:

eth0      Link encap:Ethernet  HWaddr 00:15:C5:BD:3E:2F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:94:65:62  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:16 dropped:17 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3969 (3.8 KB)  TX bytes:535 (535.0 b)
          Interrupt:16 Base address:0x2000 Memory:efdff000-efdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6587124 (6.2 MB)  TX bytes:6587124 (6.2 MB)

5) My iwconfig results from previous session:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:D3:B3:6E   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/100  Signal level=-71 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:11  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

6) IPv6 support was disabled prior to the above checks.

7) I could not find any note of a wireless setup problem with Ubuntu on this type of laptop on the page:

[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron6400](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron6400)

Any help in resolving this issue will be much appreciated. Thanks.

---

### Post by Harpoon on 2008-06-21
I am at a disadvantage because I had skipped Gutsy.  I do, however, have the same network card, and in Feisty it used the same iwl3945 driver.  I experienced no card/driver related problems.

It could be that this is a networkmanager problem.  You can try this:

sudo ifdown eth1
sudo iwlist eth1 essid <id here>
sudo iwlist mode managed
sudo dhclient

That should bring the card back up, and show you what it is doing in the terminal.  If it works, great--you can continue to manually connect like this, or install wicd from the repository. You can start the program from the applications menu.

If that doesn't work, you may neet to kill network manager first.  If that doesn't work, I would think that the problem lies other than with the card/driver.

Hope this helps.

---

### Post by wwastro on 2008-06-21
Thanks, Harpoon, for your suggestions.

Unfortunately the command

sudo iwlist mode managed

is not accepted by the system because my install does not recognize _mode_ or _managed_ as keywords for iwlist.

Is there another way of achieving the intended result, or have I misunderstood something?

Thanks.

---


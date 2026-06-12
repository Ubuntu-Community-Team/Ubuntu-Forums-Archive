---
title: "[SOLVED] Can't get wireless to start at boot..."
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by which_chick on 2008-03-25
I have a working wireless config on Dell Inspiron laptop, Gutsy AMD64, Broadcom BCM94311MCG wlan mini-PCI.  I'm using the "restricted drivers" for the Broadcom, just put a check in the restricted drivers manager to make them go and that seemed to work.

The problem is that if I try to tell the wireless to start up at boot (either by using System->Administration->Network and putting a check in the box next to it OR by going to /etc/network/interfaces and putting auto eth1 in right under the wireless stuff), it doesn't do DHCP but instead gives me the eth1-avahi stuff that you get when there is no dhcp and there is no internet.

If I *don't* try to start the wireless automatically, I can start it every time after I log in by going to a terminal window and typing 

```
sudo ifup eth1
```

and it works perfectly, does its little wpa authentication, stays up like a champ, has good throughput.  I am using the wireless right now.

I'm confused.  I thought that if the wireless worked okay on a manual start that I could just tell it to start at boot and everything would be fine -- but this doesn't seem to be the case.

Eth0 is hard-wired ethernet.  It's currently unplugged and nonfunctional.
Eth1 is wireless.  It's currently functional.

lshw
```

jessica@RedLaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:4c:29:eb:af
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.254.2 latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a2:d3:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes

```

ifconfig
```
jessica@RedLaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:A2:D3:2E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1E:4C:29:EB:AF  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe29:ebaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5802 errors:0 dropped:731 overruns:0 frame:0
          TX packets:3919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8310165 (7.9 MB)  TX bytes:256307385 (244.4 MB)
          Interrupt:10 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:1C:23:A2:D3:2E  
          inet addr:169.254.6.123  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1164 (1.1 KB)  TX bytes:1164 (1.1 KB)
 
```

iwconfig:

```
jessica@RedLaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"home"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:A3:16:15:6B   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=88/100  Signal level=-41 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

CURRENT /etc/network/interfaces:

```
jessica@RedLaptop:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp
auto eth0 

#This is the wireless.
iface eth1 inet dhcp
wpa-psk 7854c75359c546685c68b302edd6973a608a65210b5ccf23b7256d4d84ce2c0c
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid home

#Turning off "auto" because it doesn't work right yet.
#auto eth1

```

I know that it's auto-starting eth0.  I'm not worried about that.  The thing is that if I take the # out from in front of "auto eth1", the wireless doesn't come up.  It fails DHCP and I get the avahi thing like the current ifconfig shows for eth0 and then there's no internet.

It does not make any difference if I have eth0 enabled or not.  I've experimented as follows:

case 1:  try only wired interface at boot.  
Result:  Wired works fine.  Wireless doesn't start but can be started as per sudo ifup eth1.

case 2:  try wired and wireless interfaces at boot
Result:  Wired works fine.  Wireless fails DHCP, gets the avahi thing

Case 3:  Try only wireless at boot
Result:  Wireless fails DHCP, gets avahi thing.  Wired can be started as per sudo ifup eth0

Whether or not I ask for the wired interface to come up appears to be irrelevant to whether or not I have wireless.

Am I doing something wrong?  Missing something really obvious?  All I'm doing to start the wireless after I log in is going to a terminal window and typing 

```
sudo ifup eth1
```

so it's using the configuration information that's in the /etc/network/interfaces file, right?  

I'm out of ideas for how to find where the problem is.  Suggestions?  (I've got to go to work, but I'll check back on this when I get home tonight.)

---

### Post by Eiríkr on 2008-03-25
Network Manager is known to have very limited functionality, and apparently causes all kinds of trouble if you have both wired and wireless on the same machine.  I rather suspect that NM is the culprit here.  Many threads I've read here on the forum strongly recommend replacing Network Manager with WICD, which unfortunately is not included in the Ubuntu repositories, and must therefore be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").

Hope this helps,

Eiríkr

---


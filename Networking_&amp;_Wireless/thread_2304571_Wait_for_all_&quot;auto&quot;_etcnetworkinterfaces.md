---
title: "Wait for all &quot;auto&quot; /etc/network/interfaces to be up for network-online.target failed"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by Manoj_Arun_Kumar on 2015-11-28
Hi, 

--------------------------------------------------------------------------------
1) I am troubled with following problem :
--------------------------------------------------------------------------------
Wait for all "auto" /etc/network/interfaces to be up for network-online.target failed .

[Failed] Wait for all "auto" /etc/network/interfaces to be up for network-online.target.

--------------------------------------------------------------------------------
2) O/P of systemctl list-dependencies network-online.target
--------------------------------------------------------------------------------

```
# systemctl list-dependencies network-online.target
network-online.target
&#9679; &#9500;&#9472;ifup-wait-all-auto.service
&#9679; &#9492;&#9472;NetworkManager-wait-online.service
```

--------------------------------------------------------------------------------
3) O/P of systemctl --all |grep ifup
--------------------------------------------------------------------------------

```
# systemctl --all |grep ifup
&#9679; ifup-wait-all-auto.service                                                                                            loaded    failed   failed    Wait for all "auto" /etc/network/interfaces to be up for network-online.target
  [EMAIL="ifup@eth0.servic"]ifup@eth0.servic[/EMAIL]e                                                                                                     loaded    active   exited    ifup for eth0
  system-ifup.slice                                                                                                     loaded    active   active    system-ifup.slice

```
--------------------------------------------------------------------------------
4) cat /etc/network/interfaces
--------------------------------------------------------------------------------
```
# cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
            address 192.168.1.21
            netmask 255.255.255.0

auto dsl-provider
iface dsl-provider inet ppp
pre-up /bin/ip link set enp7s0 up # line maintained by pppoeconf
provider dsl-provider

auto enp7s0
iface enp7s0 inet manual

```
--------------------------------------------------------------------------------
5) ifconfig
--------------------------------------------------------------------------------

```
# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:21:cc:72:7e:03  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66571 (66.5 KB)  TX bytes:66571 (66.5 KB)
```

--------------------------------------------------------------------------------
6) Question :
--------------------------------------------------------------------------------

1) Why auto /etc/network/interfaces to be up for network-online.target failed ?
2) whether pppoeconf is causing problem ?

Thanks
MAK

---

### Post by Bucky Ball on 2015-11-28
Please use code tags for terminal output. See the last link in my signature ...

Run the wirelessinfo script in my signature and post a link or post the output *_between code tags_*, please.

Are you using the default 'Network Manager'? Have you manually tweaked the /interfaces file?

---

### Post by Manoj_Arun_Kumar on 2015-11-28
Hi,

I have edited my post using code tags .

Answer 1: Yes, I am using default network manager  .

Answer 2: Yes, for assigning new IP for system, I have tweaked. and also I made pppoeconf.


Kindly find the O/P for the wireless script :

[ATTACH]265803[/ATTACH]


Thanks
MAK

---

### Post by praseodym on 2015-11-28
If the "interfaces" is filled, e.g. with pppoeconf, then the NWM cannot handle these settings automatically. Open this file:

```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```
Change "false" to "true", save, close the editor and reboot

---


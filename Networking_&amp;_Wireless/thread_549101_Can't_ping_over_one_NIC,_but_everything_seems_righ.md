---
title: "Can't ping over one NIC, but everything seems right"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by hugmenot on 2007-09-12
I'm at a loss. I used to use a bridge, br0, to use my serverbox as a kind of wireless repeater. Since recently I cannot get my wireless madiwifi NIC to transmit packages. Even though everything that I can think of seems properly set up. I must be missing something. Is there another place I can look at?

I would reinstall this machine, but the screen is cracked and installing would be very cumbersome.

Here's some info. I established an unencrypted link, and set the proper ip adress. The route is up, 10.0.0.255 is the network I use to ssh in, 10.1.0.255 is the network with the AP. Iptables seems to be open.

I tested the pccard wifi card on my other PC, it works flawlessly.

Now what means "invalid nwid"? Is this the cause? My other machnie has 0 in this field.

```
root@serverbox:/root# iwconfig ath0
ath0      IEEE 802.11g  ESSID:"Bruecke"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:30:F1:E5:B6:65   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=41/70  Signal level=-55 dBm  Noise level=-96 dBm
          Rx invalid nwid:653727  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@serverbox:/root# ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:24:DD:AC  
          inet addr:10.1.0.100  Bcast:10.1.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe24:ddac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74377 (72.6 KB)  TX bytes:552 (552.0 b)

root@serverbox:/home/towolf# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 br0
10.1.0.0        *               255.255.255.0   U     0      0        0 ath0
default         susa.lan        0.0.0.0         UG    0      0        0 br0
root@serverbox:/root# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@serverbox:/root# 


```

---


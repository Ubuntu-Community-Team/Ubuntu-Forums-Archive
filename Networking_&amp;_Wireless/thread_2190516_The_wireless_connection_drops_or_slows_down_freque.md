---
title: "The wireless connection drops or slows down frequently"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by namnamir on 2013-11-27
Hey folks,

I have a weird problem with my internet connection. My connection drops or slows down **frequently**. I've [updated]("http://ubuntuforums.org/showthread.php?t=1476007") the driver from rt2800 to rt2860, it has just reduced the number of drop connection. It is too slow (sometimes less than 100 Kbps) :confused:

```

Ethernet Adapter:     **Linksys WMP600N**
Type:                 Wireless 802.11
Connection State:     Connected
IP Address:           192.168.***.***
Connection Speed:     130 MBit/s
System Name:          ra0
MAC Address:          ************
Driver:               rt2860
Access Point (SSID):  *************
Access Point (MAC):   *************
Band:                 b/g
Channel:              11 (2462 MHz)

```

**iwconfig**
```

lo        no wireless extensions.

eth1      no wireless extensions.


ra0       Ralink STA  ESSID:"**************"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: *************   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:*****************************************
          Link Quality=82/100  Signal level:-66 dBm  Noise level:-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

[B]lsmod | grep rt
[/B]```

ip6t_rt                12558  3 xt_addrtype            12713  4 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
x_tables               29891  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
parport_pc             32866  1 
rt2860sta             864789  1 
parport                46562  3 parport_pc,ppdev,lp

```

P.S:
[LIST]
[*]I had the same problem on Win 8 and after deleting the network connection of VirtualBox, I had no more problem. Here, in Kubuntu, I've installed the Virtualbox too but I am almost sure that it doesn't depend on VirtualBox because before installing that, I had the same problem on Kubuntu and Ubuntu.
[*]I am a newbie in Linux.
[/LIST]

---


---
title: "Ad-Hoc (WinXP - Kubuntu6.06)"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by janco on 2007-01-25
Im trying to make AdHoc network between pc with XP and Kubuntu. But i just cannot connect. These are my info :

iwconfig : 

```
IEEE 802.11b/g  ESSID:"doma"  Nickname:"Broadcom 4318"
          Mode:Ad-Hoc  Frequency=2.462 GHz  Cell: 02:E0:0F:4C:26:EE
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist eth1 scan :

```
Cell 01 - Address: 02:E0:0F:4C:26:EE
                    ESSID:"doma"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=100/100  Signal level=-233 dBm
                    Extra: Last beacon: 48ms ago
```

ifconfig :

```
Link encap:Ethernet  HWaddr 00:18:F3:8F:BF:72
          inet addr:192.168.0.26  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:225 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8010 (7.8 KiB)  TX bytes:1532 (1.4 KiB)
          Interrupt:11
```

route :

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```

file resolv.conf

```

nameserver 195.146.132.58
nameserver 195.146.128.60

```

DNS of my ISP.

ping 192.168.0.1 :

```
From 192.168.0.26 icmp_seq=209 Destination Host Unreachable
```


I also try to switch off the firewall on XP comp, but didnt help.

---

### Post by spd106 on 2007-01-25
Are you using ICS? and have the ip addresses been assigned manually or through DHCP?

---

### Post by janco on 2007-01-25
Sorry, but i dont know whats ICS? 
And IPs are assigned manualy.

---

### Post by janco on 2007-01-25
ICS - internet connection sharing ?

Yes, XP is sharing its internet connection. This adhoc network works fine with XP-XP adhoc network.

---

### Post by spd106 on 2007-01-25
Your Kubuntu machine looks to be configured correctly, as long as the key is right.

On the XP machine, in order to forward the internet connection you must enable Internet Connection Sharing (ICS). This will set up a DHCP server on the 192.168.0.x subnet and have NAT.

But that doesn't solve the problem of no connection. I suggest that you check that windows machine is in ad-hoc mode, then double-check the encryption keys match.

---

### Post by spd106 on 2007-01-25
I had a quick search and according to the bcm43xx forum [http://bcm43xx.spugna.org/index.php?topic=187.0](http://bcm43xx.spugna.org/index.php?topic=187.0)
ad-hoc mode isn't supported by the bcm43xx driver yet (or at least with softmac).

You could try ndiswrapper instead, there are guides for this around. 

Sorry for the bad news.

---

### Post by janco on 2007-01-25
Oh ......... (i dont want to swear :P)

thank you wery much, it helsp me a lot....

---


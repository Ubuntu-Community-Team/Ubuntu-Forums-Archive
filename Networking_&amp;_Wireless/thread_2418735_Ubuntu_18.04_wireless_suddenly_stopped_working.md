---
title: "Ubuntu 18.04 wireless suddenly stopped working"
date: 2019-05-10
forum: Networking &amp; Wireless
---

### Post by pabra708 on 2019-05-10
At the end of last year I put Ubuntu Studio on my HP laptop. I struggled for a while to get wireless to work. I finally got it to work. A couple of weeks ago my wireless suddenly stopped working again in the middle of surfing the internet. I'm using Larry W finger's drivers and NetworkManager.conf file reads [ifupdown]
managed=true. I checked rfkill list and the connection is neither soft blocked or hard blocked. 
Any help would be appreciated

---

### Post by praseodym on 2019-05-10
Please run the wireless script from the sticky thread and show the output

---

### Post by pabra708 on 2019-05-10
[ATTACH]283240[/ATTACH]

Here is the result of running the wireless script

---

### Post by praseodym on 2019-05-11
```
wlo1      IEEE 802.11  ESSID:"2wire324"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm [/COLOR]  
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
```
Wireless seems to be turned off. Any button, switch, key or key combo?

---

### Post by pabra708 on 2019-05-11
I've done some looking and I can't find any such thing. Is there a way to turn it on from the terminal. I've tried ifconfig wlo1 and got the following output 
lo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:e0:4c:81:92:e7  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---


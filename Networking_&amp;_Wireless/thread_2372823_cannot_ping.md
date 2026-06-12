---
title: "cannot ping"
date: 2017-09-29
forum: Networking &amp; Wireless
---

### Post by nur3 on 2017-09-29
hi 

[SIZE=2][FONT=arial]
i have two Pc with device USRP N210.T[/FONT][/SIZE]he  computer connected to the device of USRP N210 using Communication  System Toolbox Support Packages. the device  connected using the  ethernet Cable. The first and second  USRP will communicate within  omnidirectional. 


[I]>[B]> findsdru
Checking radio connections...

ans = 

     Platform: 'N200/N210/USRP2'
    IPAddress: '192.168.10.2'
    SerialNum: 'F5E4FF'[/B][/I][B]
       Status: 'Success'[/B]

 
Both USRP N210 are successfully connected to the PC but unable to communicate to each other.
I also try ip route get


[B][I]root@nur-Precision-T1700:~# ip route get 192.168.20.2
192.168.20.2 via 20.20.20.20 dev wlan1  src 20.20.20.103 
    cache 
root@nur-Precision-T1700:~# ip route add 192.168.20.2 via 20.20.20.20[/I][/B]


[B]
[/B]
[B][I]root@nur-Precision-T1700:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         20.20.20.20     0.0.0.0         UG    0      0        0 wlan1
20.20.20.0      0.0.0.0         255.255.255.0   U     9      0        0 wlan1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.20.2    20.20.20.20     255.255.255.255 UGH   0      0        0 wlan1
[/I][/B]

[B]
[/B]
[B][I]root@nur-Precision-T1700:~# ping 192.168.20.2
PING 192.168.20.2 (192.168.20.2) 56(84) bytes of data.
^C
--- 192.168.20.2 ping statistics ---
17 packets transmitted, 0 received, 100% packet loss, time 16128ms

root@nur-Precision-T1700:~# ping 20.20.20.20
PING 20.20.20.20 (20.20.20.20) 56(84) bytes of data.
64 bytes from [/I][/B][***20.20.20.20***]("http://20.20.20.20/")[B][I]: icmp_seq=1 ttl=64 time=149 ms
64 bytes from [/I][/B][***20.20.20.20***]("http://20.20.20.20/")[B][I]: icmp_seq=3 ttl=64 time=160 ms
64 bytes from [/I][/B][***20.20.20.20***]("http://20.20.20.20/")[B][I]: icmp_seq=4 ttl=64 time=0.899 ms
^C
--- 20.20.20.20 ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3002ms
rtt min/avg/max/mdev = 0.899/103.625/160.323/72.769 ms[/I][/B]

i also try with the same network but destination host unreachable.

[I][B]root@nur-Precision-T1700:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         20.20.20.20     0.0.0.0         UG    0      0        0 wlan1
20.20.20.0      0.0.0.0         255.255.255.0   U     9      0        0 wlan1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
[/B][/I]
[I][B]root@nur-Precision-T1700:~# ping 192.168.10.2
PING 192.168.10.2 (192.168.10.2) 56(84) bytes of data.
From 192.168.10.5 icmp_seq=1 Destination Host Unreachable
From 192.168.10.5 icmp_seq=2 Destination Host Unreachable
From 192.168.10.5 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.10.2 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4024ms[/B][/I]


[FONT=arial,helvetica,sans-serif][SIZE=2][FONT=arial,helvetica,sans-serif] I attach figure  how the computer connected. I hope someone can enlighten me and can give me the solutions.[/FONT][/SIZE]
[/FONT]
**[FONT=arial,helvetica,sans-serif][SIZE=2][/SIZE][/FONT]**

---

### Post by cariboo on 2017-10-01
Is there a reason why the two systems are on different sub-nets?

---

### Post by nur3 on 2017-10-03
i just tried to communicate both the USRP with the different network.it show as below:

root@nur-Precision-T1700:~# ping 192.168.20.2
PING 192.168.20.2 (192.168.20.2) 56(84) bytes of data.
^C
--- 192.168.20.2 ping statistics ---
17 packets transmitted, 0 received, 100% packet loss, time 16128ms

is there any other way, please advice.
thanks

---


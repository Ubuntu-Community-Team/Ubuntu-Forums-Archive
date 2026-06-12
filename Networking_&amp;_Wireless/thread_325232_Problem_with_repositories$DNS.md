---
title: "Problem with repositories$DNS"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by h0r0n on 2006-12-25
Hi! I just installed ptpp-config (i have local net and get inet via VPN) and decided to upgrade my dapper: sudo apt-get update and it answer that can't to find servers... Firefox is working...
I can ping some sites but can't ping ubuntu.com for example. Friend said that it's a DNS problem. What I have to do? In Windows wrote 
[I][C:\Documents and Settings\uswer>ipconfig /all

        Comp name  . . . . . . . . . : microsof-ad3843
        Main DNS-suffix  . . . . . . :
        IP-route . . . . : no
        WINS-proxy . . . . . . . : no
        DNS suffix order. : campus.gubkin.ru

Local area - Ethernet adapter:

        DNS-suffix . . : campus.gubkin.ru
        Card  . . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Adress. . . . . . . . . : 00-40-F4-B5-BA-7D
        Dhcp on. . . . . . . . . . . : &#1076;&#1072;
        AUTo customizing  . . . . . : &#1076;&#1072;
        IP-adress  . . . . . . . . . . . . : 10.32.74.10
        Mask . . . . . . . . . . : 255.255.255.192
        Gateway . . . . . . . . . . : 10.32.74.1
        DHCP-serv . . . . . . . . . . . : 10.32.74.1
        DNS-serv . . . . . . . . . . . : 10.32.0.1
                                            10.32.250.9
        Main WINS-serv  . . . . . . : 10.32.0.1[/I]

Thank you!

---

### Post by dbott67 on 2006-12-25
You may want to try 2 things:

1. Blacklist ipv6
2. Change default DNS servers to OpenDNS servers.

Both steps are outlined in this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747](http://www.ubuntuforums.org/showthread.php?t=323747)

-Dave

---

### Post by h0r0n on 2006-12-25
Thank you! I'll try!:D

---

### Post by h0r0n on 2006-12-27
You are the best Guru, it's working!

---

### Post by dbott67 on 2006-12-27
Great news!

-Dave

---


---
title: "accessing internet by lan cable through another computer with internet connection?"
date: 2021-12-02
forum: Networking &amp; Wireless
---

### Post by ubto66 on 2021-12-02
Computer A and Computer B. Computer A has a vpn wifi internet connection. Can computer B get internet access through computer A by a lan cable connection between computer A and computerB? If so how?  If computer A has internet connection through the build in wifi card and also has an usb wifi card connected can computer B then get internet connection through computer A's usb wifi card? If so how? Thank you.

---

### Post by damian7820 on 2021-12-02
First, you must have an EI/TIA 568A Ethernet crossover cable at one end and EIA/TIA 568 B at the other end.
Then computer A must be configurated as router through the iptables packes:
$sudo apt install iptables
Both computer A an B must share the same network segment. For example 192.168.1.1/24 (computer A) and 192.168.1.2 (computer B).
Then on the computer A configure at as a router:
$sudo [FONT=var(--ff-mono)]echo 1 > /proc/sys/net/ipv4/ip_forward[/FONT]
$sudo [FONT=var(--ff-mono)]iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

[/FONT]eth1 represents the name of network interface on the computer A.

---

### Post by ubto66 on 2021-12-04
When I have finished using computer A as a router, then how do I reverse back the settings to when computer A was not a router?

---

### Post by rsteinmetz70112 on 2021-12-06
Assuming Computer A is Ubuntu you don't actually need to do anything. It will work as a workstation and as a router at the same time. 
You can also do it though wifi if you wish, simply use the name of the wifi interface above. if you're using two wifi cards some additional com figuration may be required. But beware that any other wifi computer can access your internet connections as well.

---

### Post by damian7820 on 2021-12-08
[COLOR=#000000]$sudo [/COLOR][COLOR=#000000][FONT=var(--ff-mono)]echo 0 > /proc/sys/net/ipv4/ip_forward
[/FONT][/COLOR][COLOR=#000000]$sudo [/COLOR][COLOR=#000000][FONT=var(--ff-mono)]iptables -F[/FONT][/COLOR]

---

### Post by kurt18947 on 2021-12-10
Why not get a router with VPN capability? Or add the capability via 3rd party firmware?

---

### Post by ubto66 on 2021-12-11
Can you explain the difference between

 > $sudo [FONT=var(--ff-mono)]echo 1 > /proc/sys/net/ipv4/ip_forward[/FONT]
$sudo [FONT=var(--ff-mono)]iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
[/FONT]

and

> [COLOR=#000000]
$sudo [/COLOR][COLOR=#000000][FONT=var(--ff-mono)]echo 0 > /proc/sys/net/ipv4/ip_forward[/FONT][/COLOR]
[COLOR=#000000][FONT=var(--ff-mono)][/FONT][/COLOR][COLOR=#000000][FONT=var(--ff-mono)][/FONT][/COLOR][COLOR=#000000]$sudo [/COLOR][COLOR=#000000][FONT=var(--ff-mono)]iptables -F[/FONT][/COLOR] 				
 			
  			   		


---

### Post by ubto66 on 2022-01-03
sudo echo 1 > /proc/sys/net/ipv4/ip_forward returns permission denied. It does not ask for a psswrd.

---


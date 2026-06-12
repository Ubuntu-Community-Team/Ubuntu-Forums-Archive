---
title: "2 wifi devices, same laptop &amp; subnet, round trip through AP"
date: 2021-10-16
forum: Networking &amp; Wireless
---

### Post by faboisier on 2021-10-16
Hello everybody,

For training purpose, I try to connect 2 Wifi interfaces from my laptop to the same AP :
 
[COLOR=#D4D4D4][FONT=&amp][COLOR=#6a9955]# Connect Bart the AP "yoda" (security: NONE)[/COLOR]
[/FONT][/COLOR][COLOR=#0000ff]sudo iwconfig bartWlan essid yoda  
sudo ifconfig bartWlan 192.168.50.101 netmask 255.255.255.0[/COLOR][COLOR=#D4D4D4][FONT=&amp]

[COLOR=#6a9955]# Connect Homere the AP "yoda" (security: NONE)[/COLOR]
[/FONT][/COLOR][COLOR=#0000ff]sudo iwconfig homereWlan essid yoda  
sudo ifconfig homereWlan 192.168.50.102 netmask 255.255.255.0[/COLOR][COLOR=#D4D4D4][FONT=&amp]
[/FONT][/COLOR]

I would like to perform an iperf between these two interfaces : 192.168.50.101 (iperf client) -----> AP -----> 192.168.50.102 (iperf server)
So I setup the following routes :

[COLOR=#0000ff]sudo route del -net 0.0.0.0 gw 192.168.50.1  netmask 0.0.0.0 dev homereWlan
sudo route del -net 0.0.0.0 gw 192.168.50.1  netmask 0.0.0.0 dev bartWlan
sudo route del -net 192.168.50.0 netmask 255.255.255.0 dev homereWlan
sudo route del -net 192.168.50.0 netmask 255.255.255.0 dev bartWlan
sudo ip route add 192.168.50.102/32 dev bartWlan
sudo ip route add 192.168.50.101/32 dev homereWlan[/COLOR][COLOR=#D4D4D4][FONT=&amp]
[/FONT][/COLOR]

This is the result (route -n) :

[COLOR=#8b4513]0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp7s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp7s0
192.168.50.101  0.0.0.0         255.255.255.255 UH    0      0        0 homereWlan
192.168.50.102  0.0.0.0         255.255.255.255 UH    0      0        0 bartWlan[/COLOR][COLOR=#D4D4D4][FONT=&amp]
[/FONT][/COLOR]

Then I run iperf in two terminals :

[COLOR=#0000ff]iperf -s -B 192.168.50.101 -i 1 -u

iperf -c 192.168.50.101 -B 192.168.50.102 -n 1000000M -i 1 -u[/COLOR][COLOR=#D4D4D4][FONT=&amp]
[/FONT][/COLOR]

It work ! 

**[COLOR=#ff0000]BUT, I am not sure the data goes through the AP.[/COLOR]**[COLOR=#000000] I am afraid that the traffic goes through the local interfaces and not the AP.[/COLOR]

[COLOR=#0000ff]ip -c route get 192.168.50.101[/COLOR][COLOR=#D4D4D4][FONT=&amp]
[/FONT][/COLOR][COLOR=#8b4513]local 192.168.50.101 dev lo src 192.168.50.101 uid 1000 
    cache <local> [/COLOR][COLOR=#D4D4D4][FONT=&amp]

[/FONT][/COLOR][COLOR=#0000ff]ip -c route get 192.168.50.102[/COLOR][COLOR=#D4D4D4][FONT=&amp]
[/FONT][/COLOR][COLOR=#8b4513]local 192.168.50.102 dev lo src 192.168.50.102 uid 1000 
    cache <local> [/COLOR][COLOR=#D4D4D4][FONT=&amp]
[/FONT][/COLOR]

**How can I be sure that the traffic go through the AP and if not, what is wrong with my setup ?**

Thanks for your help

Fabrice

---


---
title: "Please help me with my router VPN"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by cheops20062 on 2014-02-15
[COLOR=#000000][FONT=Verdana]Hi, [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have setup a PPTP to work on my router but I'm not happy with it because I have to have redirect internet traffic and create NAT checked for it to work. I found a script that I modified slightly for my own purposes but don't fully understand how it works. 

[/FONT][/COLOR]```
[COLOR=#006600][FONT=Courier]for i in /proc/sys/net/ipv4/conf/*/rp_filter ; do [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]  echo 0 > $i [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]done [/FONT][/COLOR]

[COLOR=#006600][FONT=Courier]ip route flush table 100 [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]ip route del default table 100 [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]ip rule del fwmark 1 table 100 [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]ip route flush cache [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]iptables -t mangle -F PREROUTING [/FONT][/COLOR]

[COLOR=#006600][FONT=Courier]ip route show table main | grep -Ev ^default | grep -Ev ppp0 \ [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]  | while read ROUTE ; do [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]      ip route add table 100 $ROUTE [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]done [/FONT][/COLOR]

[COLOR=#006600][FONT=Courier]ip route add default table 100 via $(nvram get wan_gateway) [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]ip rule add fwmark 1 table 100 [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]ip route flush cache [/FONT][/COLOR]

[COLOR=#006600][FONT=Courier]iptables -t mangle -A PREROUTING -i br0 -j MARK --set-mark 1 [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]iptables -t mangle -A PREROUTING -i br1 -j MARK --set-mark 0 [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]iptables -t mangle -A PREROUTING -i br2 -j MARK --set-mark 0 [/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]iptables -t mangle -A PREROUTING -i br3 -j MARK --set-mark 1 
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]What I want to do is setup table 100 br1 to be my vpn and not the default table. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Many thanks for your help.[/FONT][/COLOR]

---


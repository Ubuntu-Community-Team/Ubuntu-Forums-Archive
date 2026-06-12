---
title: "$300 for the solution - fwmark, iptables"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by vincentdipiazza on 2008-03-19
Please take the time to figure this out, I will pay you $300 if you could get this working.
 
I am using linux kernel 2.4.35

I need to ask you for some expertise regarding iptables, fwmark, and ip rule.
 
I am currently redirecting all traffic through the VPN.  This works great.  However, I don't want http traffic to go through the VPN I want all other traffic to go through but not http.
 
So i did alot of research and I found that I would be able to create another routing table besides main.  And then route any specific traffic through that route.
 
First I create another table like this:
#ip route show table main | grep -Ev tun | grep -Ev ^default | while read ROUTE ; do
ip route add table 7 $ROUTE
done
#ip route add table 7 default via 192.168.66.1 
*** 192.168.66.1 is my IP recieved from my ISP's modem ***
 
I know table 7 works perfect because if I change the default ip rule to direct all traffic to table 7 I am no longer using the VPN for all traffic.  This is how I did the test:
DEFAULT IP RULE (ALL TRAFFIC GOES THROUGH VPN AT FIRST):
# ip rule
0:         from all lookup local
32766:  from all lookup main
32767:  from all lookup default
 
CHANGED IP RULE (ALL TRAFFIC GOES THROUGH ISP AFTER THESE COMMANDS):
# ip rule add from 0/0 table 7 pref 100
# ip rule
0:         from all lookup local
100:      from all lookup 7
32766:  from all lookup main
32767:  from all lookup default
 
But this is not what I want I only want to web traffic to go through the ISP and everything else to go through the VPN.  Therefore http should go through table 7 and all other traffic should go through table main.  So I did some research and found I need to mark the packets using IP tables.  And then i have to use fwmark to inside ip rule to move these packets to table 7.  So this is what I did:
FIRST I WANT TO REMOVE THE IP RULE TABLE 7 (ALL TRAFFIC NOW IS GOING BACK THROUGH THE VPN AFTER THESE COMMANDS):
# ip rule del from 0/0 table 7 pref 100
# ip rule
0:         from all lookup local
32766:  from all lookup main
32767:  from all lookup default
 
THEN I WANT TO ADD A FWMARK TO THE IP RULE (ALL TRAFFIC STILL GOES THROUGH VPN AFTER THESE COMMANDS):
# ip rule add fwmark 7 table 7 pref 100
# ip rule
0:         from all lookup local
100:     from all fwmark 0x7 lookup 7
32766:  from all lookup main
32767:  from all lookup default
 
The reason why traffic is still going through the VPN is because there are no marked packets with 7.
 
THEN I MARK ALL HTTP PACKETS WITH 7:
#iptables -t mangle -I PREROUTING -m layer7 --l7proto http -j MARK --set-mark 7
 
Now as soon as I issue this command http traffic doesn't work at all.  All other traffic works perfect, if I try to access a server using ssh it works, but if i try to access the web nothing happens.  This means that the command to mark http packets is working.  But for some reason fwmark doesn't effectively use table 7.  We know that table 7 is working perfect because we tested it by sending all traffic to it.  So the error or limitation is fwmark.  Why can't fwmark correctly use table 7?  I have read that I may need to add an SNAT or DNAT rule.  I also read that maybe the kernel has to include this fwmark in order for it to work.  I am stuck.  This is very important.  I will pay you $300 if you can figure this out for me.
 
P.S. AS SOON AS I REMOVE THE IPTABLES MARK 7 EVERYTHING IS GOING THROUGH THE VPN AGAIN AFTER THIS COMMAND.
#iptables -t mangle -D PREROUTING -m layer7 --l7proto http -j MARK --set-mark 7
 
1.) Table 7 works - this is not the issue.
2.) marking http packets works - this is not the issue
3.) ip rule add fwmark is not working for some reason.
a.) it could be that the kernel cannot handle this.  Please check it. But this does not seem likely since it allowed the command.
b.) it could be that when packets are going out they are going out with the wrong source IP, which is why I may need to use SNAT and DNAT iptables rules.
c.) I could be missing another step that is required when using fwmark inside the ip rule.
 
P.P.S Yes I have also tried marked all tcp port 80 without using the layer7 filter and I still get the exact same result.  PLEASE HELP!!!
 
Thanks,
Vince

---

### Post by TheWizzard on 2008-03-19
the dollar is worth nothing. how much in euros?

---


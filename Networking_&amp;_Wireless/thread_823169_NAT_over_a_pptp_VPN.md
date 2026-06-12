---
title: "NAT over a pptp VPN"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by cypr3ss on 2008-06-08
Hello All,

Apologies for the large post, but hoping someone can help with me with this, as I'm stuck.  I have a box running 8.04 with 2 nics (eth0 and eth1) which will be a firewall/router for a remote site.  When connected via ADSL I can get a PPTP VPN connection (ppp0) to the main site, and can reach all the hosts on this network (from the server/firewall).  I'd like all the machines connected to the server/firewall on eth1 (via a switch) to be able to access all the network hosts on the remote network.  

eth0      Link encap:Ethernet  HWaddr 00:0d:60:4a:c1:02  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr 00:05:1c:16:e5:12  
          inet addr:10.70.5.62  Bcast:10.70.5.63  Mask:255.255.255.192
          inet6 addr: fe80::205:1cff:fe16:e512/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.58.207  P-t-P:192.168.58.206 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1

From a host on the internal network (10.70.5.x) I can ping 192.168.58.207 but nothing else.  

To make sure I've got no issues with the firewall blocking things, my iptables setup is: 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0     

I have also set: net.ipv4.ip_forward=1 in /etc/sysctl.conf

As far as I can tell I need to NAT anything that goes out the ppp0 interface (so all traffic appears to the remote network as originating from 192.168.58.207) and will make it's way back... does this sound right? 
 
Any and all help greatly appreciated.

Regards,

Cypr3ss.

---

### Post by SpaceTeddy on 2008-06-09
i am confused as what is supposed to connect where. I've re-read the post three times and cannot make head or tails. Here are the facts i think i have gathered:

 - eth0 is your external interface which is connected to the internet
 - eth1 is your internal network card attached to a switch
 - ppp0 is a vpn tunnel device (windows vpn ?) being connected from the internet
 - any client on the internal network can ping any other client, as well as the client which is connected via ppp0

Now, what i *think* your problem could be:
 - your internal clients cannot access the internet (that would mean that NAT is missing on the firewall/router)
 - the client behind the ppp0 device is a router itself which holds another network that your clients cannot find. In that case, you are missing routed on the end points of the vpn connections as well as the standard gateways of both networks

As i am confused what the question is, i'll just wait for clarification and then try to help you with a solution.

also... a picture always helps *hint* :)

hope we can figure this out.

---

### Post by cypr3ss on 2008-06-09
:) Ok, sorry for the confusion, hope this helps to clarify:

eth0 is the external interface which is connected to the internet
eth1 is the internal network (running DHCP) connected to a switch
ppp0 is a vpn tunnel being connected from the eth0 interface (internet)

The VPN tunnel has a LAN on the end of it, the tunnel is terminating at/on a Nortel device and a (windows) PPTP vpn is my only option (long story).

Internal_lan -->ubuntu fw --->adsl -->Internet -->Main_Site_lan

The ubuntu box can ping any machine on the site lan, and all connections work (ie after authentication can browse network shares etc).  But only the ubuntu box, internal clients can't ping "down" the tunnel, they time out. 

Internal clients can access the Internet (depending on how DNS is configured) alright.

> 
 - the client behind the ppp0 device is a router itself which holds another network that your clients cannot find. In that case, you are missing routed on the end points of the vpn connections as well as the standard gateways of both networks


I think you may be onto something here... which is why I was thinking I could NAT traffic entering the VPN tunnel to appear to come from the one end-point and (hoped) the ubuntu box would then b able to do the "reverse routing"... does that make sense?  

I should also mention that the tunnel end-point IPs are addresses in the main site.

Thanks!!

Cypr3ss.

---

### Post by cypr3ss on 2008-06-09
> **SpaceTeddy said:**
> 
also... a picture always helps *hint* :)

hope we can figure this out.


And now I've attached a pic, which i'm sure will be more useful than my ramblings :)

I'm hoping we can figure this out too, and really appreciate your help, thanks again!

---

### Post by SpaceTeddy on 2008-06-09
right-o, now i understand the Problem.

Yes,you are prefectly right about the NAT being needed. The Problem is, that the router on the main network does not know where to find your subnet - it only knows where to find ubuntu machine (as that is directly conected to the network via vpn).

There are two things you need to do. 

1.) add a route on the ubuntu machine to the main network and send this one over the ppp0 link (if the ppp0 connection does not redirect you entirely anyway). If the standard gateway is NOT your vpn server, then you will need to add the route with
```
sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev ppp0
```

2.) enable NAT on all outgoing traffic to that network.
This can be done with this command
```
sudo iptables -A POSTROUTING --table nat -d 192.168.1.0/24 -o ppp0 -j MASQUERADE
```
which will rewrite all pakets going into the main network to orginiate from the ubuntu machine.
**Alternative:** Ask the person managing the nortel machine to set a route on their site to your network. This will eliminate the requirement for the NAT and will enable clients on the main Network to also access machines on your subnet. I would prefer that setting as it is clear routing without any rewriting - and therefore easier to understand.

hope it helps :)

---

### Post by cypr3ss on 2008-06-09
That's it, you've nailed it!!  I had the route command figured out, but could not get the NAT side of things figured.

It seems my FW rules still aren't quite right though... everything was working perfectly (including full name resolution from internal clients accross the tunnel) and then i rebooted the box.  When it came back up things weren't (and still aren't) working so well (even though I thought i'd backed up my iptables config :/).  Currently it looks like something is blocking the dns traffic across the tunnel, as I can ping hosts on the "main site" lan fine, but get "unknown host" errors when trying to ping the fqdn...

So I may post back later chasing some iptables help :) but atm it's time for bed.

Thanks heaps for all your help.

Kind regards,

Cypr3ss.

---


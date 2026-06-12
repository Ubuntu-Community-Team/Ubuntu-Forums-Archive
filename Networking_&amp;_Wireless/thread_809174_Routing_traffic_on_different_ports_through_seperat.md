---
title: "Routing traffic on different ports through seperate ppp connections."
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Liet_Kynes on 2008-05-27
Hi guys I'm wondering if someone could help me out here.

I'm running 2 pppoe connections and I need to route traffic on a specific port through a specific ppp conection. This is what I've done so far.

I've enable ip_forwarding by doing 
```
 echo 1 > /proc/sys/net/ipv4/ip_forwarding
``` I'm not sure if that is correct and how to enable it at boot time automatically. Or even if it's all that is required.

I've then added the following ipfilter rules.
```
iptables -A INPUT -p tcp --dport 118 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i ppp0 --dport 118 -j DNAT --to 196.43.x.x:119
```I'd also like to know how to load these rules automatically at startup. I'm not even sure ipfilter is loading at startup.

I think this should route any incoming traffic on port 118 eth0 (my network card) through the 2nd ppp connection (ppp1) to a specific server on port 119.


Any suggestions or advice. Thanks in advance.

---

### Post by SpaceTeddy on 2008-05-28
routing does not care about ports !

that said, i think what you need to do is add routes for the servers that are supposed to use a specific port. But this can get very ugly vey quickly.

So, besides that i am a little confused about why anyone would want to use a specific line for specific purposes, this is how i would (start) of doing it:

Try 1.) 
Use the SNAT target in the POSTROUTING. This lets you overwrite the source IP with any given IP in the rule. For example, if you want any traffic to any webserver to be rewritten so that the source is the ip 1.2.3.4, you would use this rule:
> sudo iptables -A POSTROUTING --table nat -j SNAT --to-source 1.2.3.4
BUT - regardless of what the source address is, the paket will still be sent out via your default gateway, i.e. always via the same ppp connection (assuming you have no special routes set). If the reply comes back on a different network card, i don't know how the machine handles this task.

Try 2.)
Alter the routing table. So, if you want ppp0 to be used for anything, and ppp1 for only a webserver at which is located at the ip 1.2.3.4, you would use the follow routes
```
sudo route add default gw %gw-ip0
sudo route add -net 1.2.3.4 netmask 255.255.255.255 dev ppp1 gw %gw-ip1

```
where %gw-ip0 is replaces by the default gateway of the ppp0 device, and %gw-ip1 is replaced by gateway of ppp1.

Try 3.)
if you only want to do this for webpages, maybe you want to have a look at a (transparent ?) proxy. I've used them before on machines with multiple ips to force some clients to appear under a different IP than others. A good starting point here would be squid.


Now, for loading the commands on boot. The easiest way is to write the commands into the /etc/rc.local file (make sure you use the full path to the exectuables, not just their names - e.g. use /sbin/iptables instead of iptables). Anytime time the machine loads, these commands will be exectued. Also, don't use the sudo before the commands, as these will already be executed by root - so there is no need to force a sudo upon them. 

The same goes for the ip_forward, also i'd suggest you use this command instead of your to accomplish the task (your commands i depricated as far as i know)
```
sysctl -w net.ipv4.ip_forward=1
```

hope it helps :)

---


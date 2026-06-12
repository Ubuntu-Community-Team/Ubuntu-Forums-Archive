---
title: "Ubuntu as router and DC++ active connection"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by -=MindHunteR=- on 2008-03-05
Hello friends!
First - sorry for my bad English.

I have Ubuntu workstation which performs like router and shares internet conection with NAT (it has 2 network adapters). I set the sharing using iptables and IP masquerading.
 To second adapter connected wireless router, which shares internet to 2 windows stations. On one of them I'm trying to use DC++ client, but I can't use active mode, even if I enter port numbers which I wanna use in DC++ client and do port forwardin in router and trying to do port forward on Ubuntu too... But I still can't use direct connect mode, only passive.
I guess that I do something wrong. For example, there is WAN/EXTERNAL IP address in DC settings.. I dunno which IP should I put there.
Therefore, please, ppl who knows DC and port forwarding in Linux (i think best to do it with iptables) - guide me what to do.

Here is the scheme of my connections: 

[IMG]http://img337.imageshack.us/img337/8751/20080305113013ci0.png[/IMG]


Many thanks! :KS


_

---

### Post by SpaceTeddy on 2008-03-05
two things i can see that would be possible to go wrong..

1.) your ubuntu desktop does not know where to find the windows stattion - since the wireless router has two different subnets connected. Can you access the internet at all from the windows station ? if so, does the wireless router do NAT aswell ? or has your ubuntu PC a route for the 192.168.1.0/24 network ?

2.) do you have port forwarding setup in your ubuntu box ? for most programms active connection means that other can connect to you - this is generally not working if you have NAT enabled anywhere. 

in general, what you will most likely need is the DNAT target in the PREROUTING chain of the nat table. this sounds scary, but it really is not. It basicially means that you will need to rewrite incomming pakets to be forwarded through any nat router.

---

### Post by -=MindHunteR=- on 2008-03-05
> **SpaceTeddy said:**
> 

1.) your ubuntu desktop does not know where to find the windows stattion - since the wireless router has two different subnets connected. Can you access the internet at all from the windows station ? if so, does the wireless router do NAT aswell ? or has your ubuntu PC a route for the 192.168.1.0/24 network ?

yes i can access to all inet servises from windows station. 
how can i check if my ubuntu has route for the 192.168.1.0/24 network ?


> **SpaceTeddy said:**
> 
2.) do you have port forwarding setup in your ubuntu box ? for most programms active connection means that other can connect to you - this is generally not working if you have NAT enabled anywhere. 

in general, what you will most likely need is the DNAT target in the PREROUTING chain of the nat table. this sounds scary, but it really is not. It basicially means that you will need to rewrite incomming pakets to be forwarded through any nat router.

i tried to do Port Forward in ubuntu box. i did
# export LAN=eth0
# export WAN=eth1
# iptables -t nat -A PREROUTING -p tcp --dport 3628 -i ${WAN} -j DNAT --to 192.168.0.1:3628
# iptables -t nat -A PREROUTING -p udp --dport 3628 -i ${WAN} -j DNAT --to 192.168.0.1:3628

i did port forward for these ports in router also. and entered them to DC client under manual port configurations. in EXTERNAL IP/WAN field i tried enter  IP of  WAN (132.blah.blah.balh) and of router (192.168.2.1)... nothing helps...
in addition, DC cliens has TLS port... what is this? how can i do port forward for it?
in internet i found a couple  of guides how to make port forward for DC.(all of them for 1 router, hardware router, not 2 routers as i have) they did port forward for TCP and UDP, but not for TLS. in the same time i can't leave this field empty.

---

### Post by SpaceTeddy on 2008-03-05
you can check of the route exists by either looking at the output of route -n (there should be a route there looking like this one)
> 192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

or you can simpy try to ping the xp machine - if you get replies, it should be working
> 
iptables -t nat -A PREROUTING -p tcp --dport 3628 -i ${WAN} -j DNAT --to 192.168.0.1:3628
iptables -t nat -A PREROUTING -p udp --dport 3628 -i ${WAN} -j DNAT --to 192.168.0.1:3628

the IP address of the destination seems to be wrong here - it should either be 192.168.0.100 (if the router inbetween uses NAT aswell and needs to do port forwarding) or the end host, so 192.168.2.101 (the windows machine)

otherwise, your commands look just fine.

---

### Post by -=MindHunteR=- on 2008-03-05
> **SpaceTeddy said:**
> you can check of the route exists by either looking at the output of route -n (there should be a route there looking like this one)

or you can simpy try to ping the xp machine - if you get replies, it should be working


Here is output:

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
132.69.192.0    0.0.0.0         255.255.192.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         132.69.255.254  0.0.0.0         UG    100    0        0 eth1

I don't see any port forwards here. Is it OK?

When i do ping 192.168.2.101 from Uuntu bo x i don't get reply.

> **SpaceTeddy said:**
> 
the IP address of the destination seems to be wrong here - it should either be 192.168.0.100 (if the router inbetween uses NAT aswell and needs to do port forwarding) or the end host, so 192.168.2.101 (the windows machine)

otherwise, your commands look just fine.

OK i'll do. Do i have to restart any servse in Ubuntu after i enter these commands?

Tnx.

---

### Post by SpaceTeddy on 2008-03-05
ok, that means that your router also does nat - this will complicate things a little.

what i think you need is to rewrite your nat rules on the ubuntu machine to have the destination address 192.168.0.100 - and then setup port forwarding on the wireless router with the destination 192.168.1.101 (i just saw that, in the picture, your windows pc has the ip 192.168.2.101 - i guess that is a typo)

if you change the rules in a file, then you will need to reboot. if you punch them right into the command line, they will take effect immeditaly...

here is what you could try in the commandline for a quick test
> sudo iptables -F PREROUTING --table nat #empty port forwarding
sudo iptables -t nat -A PREROUTING -p tcp --dport 3628 -i eth1 -j DNAT --to 192.168.0.100
sudo iptables -t nat -A PREROUTING -p udp --dport 3628 -i eth1 -j DNAT --to 192.168.0.100

you don't really need the ports on the --to part if they are the same as the --dport :) but that is just details, it would work with them aswell :)

---

### Post by -=MindHunteR=- on 2008-03-05
nope, win really has 192.168.2.101 IP address.

i did what you said. it sorks now!!!!

but, connection is unstable :( when ppl DL from me stuff, they gonna be disconnected after 30 secs of downloading. when i connects directly to net with my Win PC, without router and Linux box, connection is rock stable....


do you know may be what shoild I do with TLS port?

Thank you!!! :popcorn:


PS: i runned TCPView on Win machine, and saw that my DC uses 4087 port.... notwithstanding i put other tcp-udp port in connection settings .... :crazy:......... What is going on....

---

### Post by SpaceTeddy on 2008-03-06
connections loss has usually nothing to do with the firewall rules (unless you specificially design them to do it), and points more to a hardware fault. 

As for the ports you need, i have no idea about DC++ - i've never used it. I just figured that  the basic setup should work before you can go into debugging the program.
TLS is (like SSL) a layer in the transport protocol and does not have any specific requirements for the firewall or port. (as far as i know)

so... no, i don't know why you get the connection loss at all :(

---

### Post by -=MindHunteR=- on 2008-03-08
> **SpaceTeddy said:**
> connections loss has usually nothing to do with the firewall rules (unless you specificially design them to do it), and points more to a hardware fault. 

As for the ports you need, i have no idea about DC++ - i've never used it. I just figured that  the basic setup should work before you can go into debugging the program.
TLS is (like SSL) a layer in the transport protocol and does not have any specific requirements for the firewall or port. (as far as i know)

so... no, i don't know why you get the connection loss at all :(

okay!
Thank a lot, mate!!!:):):)

---


---
title: "VPN routing issues maybe"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Cowloon on 2007-04-20
I know almost nothing about VPN. On windows I have a cisco client to connect to my work, which works, but I can't access my network when I'm using it. Now I want to try setting up my linux machine to connect. I've imported the profile into kvpnc and it says it has connected, but I can't access work's network via smbclient or rdesktop. ifconfig shows some tun interfaces.

smbclient says Packet send failed to 999.999.999.255(137) ERRNO=Operation not permitted

where 999.999.999.999 matches eth0

I think that means it's not trying to send packets through the tunnel.

Do you have any thoughts about what I should check to diagnose the problem?

Also, if I get it working, I can't use it if it's going to prevent me from accessing the internet directly from my linux machine, since the linux machine is also my imap server and web server. Do you know what I need to do to make that work?

---

### Post by bnuytten on 2007-04-21
Concerning your windows box: when opening a VPN or PPTP connections it sets the default route to your VPN connection. Hence you cannot access your network anymore. You can change that behaviour but you will have to set up manual routes for your VPN than.

999.999.whatever is not a valid IP address! A valid on uses 4 octects between 0-255. You probably have to check /etc/openvpn/tun0.conf (or alike).

---

### Post by Cowloon on 2007-04-21
Yes, I didn't really mean 999. It's my representation of the address that is my actual address. The point being when I try to connect to a machine at my work with smbclient it complains about sending sockets to my ethernet interface, rather than the tun0 interface.

---

### Post by bnuytten on 2007-04-21
> **Cowloon said:**
> Yes, I didn't really mean 999. It's my representation of the address that is my actual address. The point being when I try to connect to a machine at my work with smbclient it complains about sending sockets to my ethernet interface, rather than the tun0 interface.

Do you have basic network access to the machine@work: i.e. can you ping the IP address of that machine? Just trying to pinpoint the cause here, could be routing, firewall, user rights, ...

---

### Post by Cowloon on 2007-04-21
No, if I ping the machine, ping hangs until timeout. I can ping the VPN server.

---

### Post by bnuytten on 2007-04-21
> **Cowloon said:**
> No, if I ping the machine, ping hangs until timeout. I can ping the VPN server.

Hmmm. Can you post the output of route -n? Since you can ping the VPN server there is at least a route to that VPN server but you may need to add a route to that machine@work or the network@work manually. Could off course be that a firewall is blocking ping for other hosts than the VPN server. But let's asume the absence of a firewall for now :-)

---

### Post by Cowloon on 2007-04-21
Hmm. Once I run kvpnc and then disconnect and quit, the interface tun0 is still there. If I run it again I get tun0 and tun1. Then if I run it again I get tun0, tun1 and tun2...

Anyway, after running kvpnc once, route -n prints:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
199.x.x.x   0.0.0.0         255.255.255.255 UH    0      0        0 tun0
198.4.x.x      y.y.y.254 255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
y.y.y.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         y.y.y.254 0.0.0.0         UG    0      0        0 eth0

where 199.x.x.x is a DNS server at work
198.4.x.x is the VPN server
y.y.y.254 is my ISP (y.y.y.252 is eth0)

ifconfig shows

eth0 (with inet y.y.y.252)
eth1 (with inet 192.168.0.1)
tun0 (with inet 10.100.200.11)

On windows, with the vpn client running ipconfig shows 2 interfaces with:

ip 192.168.0.100
gateway 192.168.0.1
dns 206.13.28.12 (my isp's dns server)

and the other

ip 10.100.200.11
gateway 10.0.0.1
dns 199.x.x.x (work's dns server presumably)

my windows machine uses my linux machine as it's gateway.

without the vpn client running, I only have the first interface. 

"route print" on the windows machine shows

Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0         10.0.0.1   10.100.200.11       1
          0.0.0.0          0.0.0.0      192.168.0.1   192.168.0.100       20
         10.0.0.0        255.0.0.0    10.100.200.11   10.100.200.11       20
    10.100.200.11  255.255.255.255        127.0.0.1       127.0.0.1       20
   10.255.255.255  255.255.255.255    10.100.200.11   10.100.200.11       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.0.0    255.255.255.0    192.168.0.100   192.168.0.100       20
      192.168.0.0    255.255.255.0         10.0.0.1   10.100.200.11       20
    192.168.0.100  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255    192.168.0.100   192.168.0.100       20
       198.4.x.x  255.255.255.255      192.168.0.1   192.168.0.100       1
        224.0.0.0        240.0.0.0    10.100.200.11   10.100.200.11       20
        224.0.0.0        240.0.0.0    192.168.0.100   192.168.0.100       20
  255.255.255.255  255.255.255.255    10.100.200.11   10.100.200.11       1
  255.255.255.255  255.255.255.255    192.168.0.100   192.168.0.100       1
Default Gateway:          10.0.0.1

where 198.4.x.x is the VPN server. I have no idea what 224.0.0.0 and 240.0.0.0 are.

Before requiring me to use VPN I used to connect to machines using rdesktop to addresses like 198.4.x.x.

---

### Post by bnuytten on 2007-04-22
> **Cowloon said:**
> 
"route print" on the windows machine shows

Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0         10.0.0.1   10.100.200.11       1
          0.0.0.0          0.0.0.0      192.168.0.1   192.168.0.100       20
<snip>
Default Gateway:          10.0.0.1



Remember the post about the default gateway in Windows? When the tunnel is down on your windows you will see the default gateway is your linux box (192.168.0.1). On your linux box, there is no such behaviour, you have to set the routes in the config files or add them manually. The simplest option is to bring the tunnel up (say tun0) and than manually change the default route
```
ip r d default via y.y.y.254 dev eth0 #delete the ISP route
ip r a default via 10.0.0.1 dev tun0 #add the VPN route
```

When the tunnel is down you need to do the reverse. The order doesn't really matter.
```
ip r a default via y.y.y.254 dev eth0 #add the ISP route
ip r d default via 10.0.0.1 dev tun0 #delete the VPN route
```

Using this technique should work but is not convenient because 1) you have to it manually and 2) you loose internet connectivity. So in stead of changing the default route, add a route for the network@work 10.0.0.0/8 when the tunnel is up. That way you keep Internet access and you can access work.
```
ip r a 10.0.0.0/8 via 10.0.0.1 dev tun0
```

Once you have that working, you can configure your tunnel in /etc/openvpn to automatically bring up/down the route when the tunnel is created/destroyed. Check the files in /etc/openvp/ for that.

---

### Post by Cowloon on 2007-04-22
Thanks. If I use:

```
ip r a 10.0.0.0/8 via 10.0.0.1 dev tun0
```

I get a network is unreachable error. (Shouldn't it be /24, since my interface has address 10.100.200.11? I get network is unreachable with that too).

I don't really understand what the routing is supposed to be doing though. How does adding a route to 10.0.0.0 allow me to go through the tunnel to some address in the range 198.4.0.0/16? Also, if it worked, would I still be able to go everywhere outside of work, through eth0 or eth1 instead of through the tunnel?

---

### Post by bnuytten on 2007-04-22
> **Cowloon said:**
> Thanks. If I use:

```
ip r a 10.0.0.0/8 via 10.0.0.1 dev tun0
```

I get a network is unreachable error. (Shouldn't it be /24, since my interface has address 10.100.200.11? I get network is unreachable with that too).

I don't really understand what the routing is supposed to be doing though. How does adding a route to 10.0.0.0 allow me to go through the tunnel to some address in the range 198.4.0.0/16? Also, if it worked, would I still be able to go everywhere outside of work, through eth0 or eth1 instead of through the tunnel?

The subnet mask or /24 or in dotted decimal notation 255.255.255.0 depends on how the network is configured at work. Routes are basic network knowledge. I'll try to give you a crash course with an analogy. You are a traffic cop and there are two kinds of cars. The blue cars need to go north where it's cold (eth0) and the red cars need to go south where it's warm (tun0). So the traffic cop is the routing table, it tells the blue cars to go north (eth0) and the red ones to go south (tun0). Okay, what windows does is: all the cars go north, but if the road to the south is open all cars must go south... You get the idea I think, the blue cars (eth0, Internet) all get lost off course.

You can distinguish the cars by color. You can distinguish IP packets by their destination address (amongst others). So that is what the routing table does, it looks at the destination address and decides in which direction the car should go... or trough which interface the packet should go.

> How does adding a route to 10.0.0.0 allow me to go through the tunnel to some address in the range 198.4.0.0/16? It doesn't :-) If you want that traffic to go trough the tunnel also, say these are the yellow cars, you must tell the traffic cop to send the red and yellow cars south. So:
```

ip r a 198.4.0.0/16 via 10.0.0.1 dev tun0
ip r a 10.0.0.0/8 via 10.0.0.1 dev tun0
```

Now on the other end of the tunnel, there is another traffic cop that will redirect the red and yellow cars to the correct destination. You do not need to worry about that. All you need to know is: send the red and yellow to that other traffic cop (10.0.0.1).

> Also, if it worked, would I still be able to go everywhere outside of work, through eth0 or eth1 instead of through the tunnel
In short: if you configure it well, yes :) Believe me, I have multiple tunnels up and running and I can still surf the internet :cool: You need at least basic and in some cases rather advanced network knowledge however.

---

### Post by Cowloon on 2007-04-22
So, any thoughts on why ip would be saying that the network is unreachable? ifconfig says tun0 has address 10.100.200.11. I can ping the VPN server and 10.100.200.11.

---

### Post by Cowloon on 2007-04-22
I'll add a part two to the question, because I think part of what I said might not have been understood.

Work IP addresses have a range 198.4.0.0/16, I think. In any case, from windows if I ping the machine by DNS name, I get back an address like that with the VPN client connected.

So, If I use an analogy for the blue, yellow and red cars, that are being directed by the traffic cop, let's say the red car is a datagram with an IP address in the range 198.4.0.0/16 and the traffic cop is the kernel inspecting the routing table, and a fire hydrant is my tun0 interface with ip address 10.100.200.11. Where does adding a route to 10.0.0.0/8 fit into allowing the datagrams to be routed to the router that is adjacent to the machines that I address as 198.4.0.0/16? I think you say it doesn't fit in. So, instead should it be:

ip r a 198.4.0.0/16 via 10.100.200.11 tun0

I tried it but the traffic cop still didn't like my red cars, though I didn't get a "network is unreachable" error, and I think the man page for the ip command is saying that I can use the device ip address (10.100.200.11) there.

---

### Post by bnuytten on 2007-04-23
> **Cowloon said:**
> So, any thoughts on why ip would be saying that the network is unreachable? ifconfig says tun0 has address 10.100.200.11. I can ping the VPN server and 10.100.200.11.

Probably because the gateway is not "adjacent" i.e. not directly reachable from your pc.

---

### Post by bnuytten on 2007-04-23
> **Cowloon said:**
> I'll add a part two to the question, because I think part of what I said might not have been understood.

Work IP addresses have a range 198.4.0.0/16, I think. In any case, from windows if I ping the machine by DNS name, I get back an address like that with the VPN client connected.

So, If I use an analogy for the blue, yellow and red cars, that are being directed by the traffic cop, let's say the red car is a datagram with an IP address in the range 198.4.0.0/16 and the traffic cop is the kernel inspecting the routing table, and a fire hydrant is my tun0 interface with ip address 10.100.200.11. Where does adding a route to 10.0.0.0/8 fit into allowing the datagrams to be routed to the router that is adjacent to the machines that I address as 198.4.0.0/16? I think you say it doesn't fit in. So, instead should it be:

ip r a 198.4.0.0/16 via 10.100.200.11 tun0

I tried it but the traffic cop still didn't like my red cars, though I didn't get a "network is unreachable" error, and I think the man page for the ip command is saying that I can use the device ip address (10.100.200.11) there.

I wanted to picure the traffic cop on a crossroad. Cars come from doesn't matter where, let's say from the East and must go either north (blue, eth0) or south (red, tun0). It is the traffic cop's job to send the cars in the right direction. So your command is correct from a semantic point of view. Syntactically correct is:
```
ip r a 198.4.0.0/16 via 10.100.200.11 dev tun0
```

I beginning to see how your net admin organised things. He is using 10.100.200.11/24 (subnet guess) as an "access network" for the real network at work, being 198.4.0.0./16. So you need a route to the network adjacent to the tun0 device (if it isn't already there):
```
ip r a 10.100.200.0/24 dev eth0
```

---


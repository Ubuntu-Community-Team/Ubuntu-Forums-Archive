---
title: "Static route failing to connect."
date: 2021-04-19
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2021-04-19
[https://www.linuxquestions.org/questions/linux-networking-3/static-route-failing-to-connect-4175693965/](https://www.linuxquestions.org/questions/linux-networking-3/static-route-failing-to-connect-4175693965/)[COLOR=#000000][FONT=Verdana]

Almost have my Debian based router working flawlessly. Found an issue and sorted it so I'm back at it. Everything seems to be perfect save one. The static route at the bottom for 192.168.1.250 is to my wifes workplace gateway at home. I have the ip static via dnsmasq. When the route is as below it refuses to connect. If I remove the route it connects after a few seconds. I don't know why this is? I need it to go to a specific gateway at my home. Have dual wan due to one being not so reliable, the other being amazing. Low bandwidth but best we can do out here is fixed wireless.[/FONT][/COLOR]

```

# ip route show
default via 10.254.197.1 dev enxd03745c561a2
10.88.88.0/24 dev enxd03745d06539 proto kernel scope link src 10.88.88.252
10.254.197.0/24 dev enxd03745c561a2 proto kernel scope link src 10.254.197.254
192.168.1.0/24 dev enp2s0 proto kernel scope link src 192.168.1.1
192.168.1.250 via 10.88.88.1 dev enxd03745d06539
```
I also seem to be able to ping that ip from anywhere on my lan except from the router.

```

# ip route get 192.168.1.250
192.168.1.250 via 10.88.88.1 dev enxd03745d06539 src 10.88.88.252 uid 0
    cache

```

[COLOR=#000000][FONT=Verdana]*EDIT* Script for reference - [/FONT][/COLOR][https://gitlab.com/jmgibson1981/scri.../homerouter.sh]("https://gitlab.com/jmgibson1981/scripts/-/blob/master/server/router/homerouter.sh")

---

### Post by The Cog on 2021-04-20
Your static route seems to be sending the connection the wrong way. It is sending the connection out of interface enxd03745d06539, to 10.88.88.1. My guess is that 10.88.88.1 doesn't know what to do with packets addressed to 192.168.1.250, and drops them. 

Or maybe it thinks that the way to forward packets to 192.168.1.250 is via 10.88.88.252 - send them back where they came from. It won't do that, it will just drop them.

When you remove the static route, the route chosen will be directly to 192.168.1.250 via interface enp2s0, which is the interface that is connected to the 192.168.1.0/24 network. 

Without more info I cannot tell why you want to send the packets in a different direction. I am assuming that 192.168.1.250 is the address of your "specific gateway".

---

### Post by Tadaen_Sylvermane on 2021-04-20
I'd be lying if I said I fully understood most of what I've come up with. I've pieced my script together from googling for the last couple days and a metric crapton of trial and error in virtualbox. I had hoped I could static route a single ip on my lan > that gateway. At the end I realized I could just mangle everything with that ip the same way I was mangling the specific ports to go through the specific gateway in my script.

```
iptables -A PREROUTING -t mangle -s 192.168.1.250 -j MARK --set-mark 100
```

This seems to be working. I've tested it via giving a bridged virtual box vm the ip and running tcptraceroute. Everything seems to be going through the proper gateway that way. Only time will tell today with how stable my wifes connection is.

Networking and routing is a whole new level for me.

---

### Post by The Cog on 2021-04-20
Yes, routing is a world all of its own. 
I'm happy to see it's working, though I don't understand. 

If you have more problems, I think we will probably want a lot more info about your network. For instance, I was very surprised to see mention of doing firewall marking.

---

### Post by Tadaen_Sylvermane on 2021-04-20
I need to comment it better. The idea is that it automatically configures a linux gateway on boot. It's custom to me as I need 2 wan connections at home. The internet here is mediocre at best. This way I can have a transparent http proxy on the local network, I get the most important things (zoom, my wifes work, and my games) on the good low latency connection (5mbit fixed wireless) whilst everything else goes through the higher bandwidth but also higher latency wan (10mbit fixed wireless). I live in a bit of a dead zone. Other than reference I imagine very few people would have an actual need for this script.

I'm pretty much hoping this holds over till Starlink is here. Is sad. Their "Better than nothing beta" supplies internet exponentially better than anything else around here. Assuming it's as good as they say it is. We live close to the indian res so i don't expect any kind of growth out here. Better internet access even less likely for that reason as well.

*edit* Anecdotally of course my wife's work was flawless as usual on that gateway, not a single problem on my games, and zoom is perfect tonight for both our connections. On the flipside the other gw was barely stable enough to stream for anyone today without buffering.

---


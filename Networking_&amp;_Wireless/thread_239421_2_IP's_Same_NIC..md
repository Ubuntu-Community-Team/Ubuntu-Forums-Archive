---
title: "2 IP's Same NIC."
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by listerthrawn on 2006-08-19
Hi,

I know this has been asked in at least one other post but it didn't quite answer all my questions.

What I want is to set up another ip address on my server on the same NIC and have bandwidth intensive things run over that IP address (like bittorrent etc.)  I can then shape traffic from this address at my linux router to keep my web browsing and general net usage quick.  I'm already using a traffic shaper but i think this would make it easier.  Any tips?

Thanks

Chris

---

### Post by foolsh on 2006-08-19
I dont know if there is an emulated interface but it seems if there were you could direct the traffic to be throttled to that one and use iptables to redirect it to the "real" interface. its just a thought

I dont know if would be a good idea to throttle the lo 127.0.0.0 interface then redirect that to eth0 but it might work

---

### Post by steve.horsley on 2006-08-20
It's easy. Like this:
> sudo ifconfig eth0:1 1.2.3.4 netmask 255.0.0.0
It is possible to add lots of addresses if you want.

---

### Post by foolsh on 2006-08-20
oh cool so ifconfig eth*x*:*n* xxx.xxx.xxx.xxx 
and bam you can have as many pipes not tubes as you need to direct traffic as you wish

---

### Post by steve.horsley on 2006-08-21
Kinda cool. If's fine for running different listening services such as HTTP, SSH where you can tell the server which address to listen on. 

It's ticky for outgoing connections because you can't tell an outgoing connection which if many addresses to call **from** very easily. An outgoing connection will likely use the first interface it finds that shares a subnet with the default gateway router. Changing this behaviour may be possible but if it is, it's probably some hairy ip configuration. **man ip** for the gory details.

---

### Post by netztier on 2006-08-21
> **listerthrawn said:**
> I'm already using a traffic shaper but i think this would make it easier.  Any tips?


Then why bother and crack your head over routing problems when you already have traffic shaping in place and configured? 
Just configure your shaper to throttle the "high bandwith traffic" and have it pass the rest of the traffic swiftly - and you're set to go. 

You say that you have a Linux router in place; this makes me assume that you have a single external IP address and the router is performing PAT in any case. 
Since you have to configure port-forwarding ("pinholes") for most P2P-Applications anyway, you'll have to know and identify all ports and port ranges anyway - configuring the shaper accordingly should come easy, then.

Can you point out where the advantage of using another IP address would be - is it less complexity on the router/shaper? Traded-off for more complexity on the inner system? I for one wouldn't got down that road...

kind regards

Marc

---


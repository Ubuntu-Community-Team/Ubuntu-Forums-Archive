---
title: "Bonding - 2 ISP and failover"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by limrick on 2008-08-10
I've got bonding to work with active-backup.

Now I need to go the next step:

Nic1 --> adsl ISP
Nic2 --> cable ISP

Now if the active/default nic / isp fails then the other one takes over, when the "active/default (preferred)" isp comes back up then it switches back. With the default route set properly.

Any ideas on how to do this?

TIA

---

### Post by solitaire on 2008-08-10
Some adsl modem routers have this capacity, check our 'draytek' they do a range of routers that have fallover options.

---

### Post by limrick on 2008-08-11
Thanks for the reply Solitare.

What I'm really after is an ISP / modem / transport device independent solution that is built on linux that will switch and restore failed ethernet 10/100/1000 connections.

---

### Post by mips on 2008-08-11
> **limrick said:**
> I've got bonding to work with active-backup.

Now I need to go the next step:

Nic1 --> adsl ISP
Nic2 --> cable ISP

Now if the active/default nic / isp fails then the other one takes over, when the "active/default (preferred)" isp comes back up then it switches back. With the default route set properly.

Any ideas on how to do this?

TIA

So you have dual routes to the internet? I do not see how this has anything to do with NIC bonding. You need to look at your routing.

---

### Post by limrick on 2008-08-11
the linux box would be acting as a nat to hosts behind it.
so all the natted host would only see one route to the internet

both the adsl and cable ISPs bonded in a active-backup configuration where, say the adsl is primary and the cable is backup.
if the adsl isp goes down the cable isp would be the internet.
when the adsl comes back up then the cable would go back to backup status and the adsl would be the active internet connection.

nat host 1 -----\---------------------/--- adsl isp
nat host 2 -----=|linux_nat_box| 
nat host 3 -----/---------------------\--- cable isp

---

### Post by mips on 2008-08-11
Does the adsl & cable networks reside in the same network? I mean do they both fall in the 192.168.0.0 (or whatever) network for example.

You are not provinding enough info here to get a clear idea of what is going on.

---

### Post by limrick on 2008-08-11
both isp would be totally different carriers / different networks.
Ie adsl - 24.x.x.x cable 52.x.x.x

---

### Post by mips on 2008-08-11
> **limrick said:**
> both isp would be totally different carriers / different networks.
Ie adsl - 24.x.x.x cable 52.x.x.x

In that case bonding is definately not the way to go and was never designed for that purpose.

---

### Post by fwre01 on 2008-08-11
So you have both internet connections going into one linux box which is natting the addresses on the inside network? what if one ISP has routing issues but niether link goes down?

**EDIT**
....sorry, i forgot you wanted to bond the connections, that cant be done IP's on different subnets

Bonding would imply some kind of load balancing which cant be done with different subnets. With one connection as Active and one as Passive you could acheive redundancy. but you still have the problem as mentioned in the begining of my post.

---

### Post by limrick on 2008-08-11
Hmmm, starting to sound like this can be solved by routing.

Not knowing much about routing,,,,, is that the solution to hardware or ISP failures and if so then how would the routing detect hardware failure and restore back to the 'default' ISP after restoration?

---

### Post by fwre01 on 2008-08-11
Redundancy could be achieved with weighted routes, combined with some kinda of track IP function. could you explain a bit more about how this it set up, whats connected to what, what other equipments involved, ect...

---

### Post by limrick on 2008-08-11
Basicly its as the ascii art shows, local 10/100 nated lan, the linux box acting as a nat/firewall/failover switch for the local lan for internet access to 2 different ISPs.
This gives the clients on the local lan nearly 99.9% access to the internet.

---

### Post by solitaire on 2008-08-11
After seeing other peoples responses. I Still think you should go for the DrayTek route!! (or something like it!!!!)

You are making TOO much work for yourself. If you do not know how to set one up then how can you keep it running when the fallover fails?? 

By all means keep trying this but make sure you have a WORKING backup if you can't keep things running!!

I'm not trying to belittle you're experience! far from it! it's wise to have a working solution in place while you learn everything you need to get it working using a Linux box!!

If your Company needs 24/7 connectivity (I've worked there so I know what I'm talking about!)
Then don't endanger that uptime by playing about with things you don't know 100%. Get a temp solution that works ($200 is a good investment in ANY project!!) and then use that to build your confidence in the Linux Box route!

Once you know what to do, you can impress the Bosses and they will be more likely to let you do what you will with the network!

---

### Post by limrick on 2008-08-12
draytek looks good, we'll test one out.

still want to try to build one using linux.

---

### Post by fwre01 on 2008-08-12
yeah i agree the dreytek could probably do it. but to have some fun with the linux box would be cool :-). Will the linux box recieve both the public IP addresses on its NICs? im assuming theres a third NIC on the server connected to the internal switch?

If so, the easiest way to do it would be to have two default routes, one with a metric of 10 pointing to ISPA and one with a metric of 20 pointing to ISPB, the lower metric route would win. This means that in the event that the NICA went down (i.e the ethernet cable broke between your server and the modem) the traffic would flip to ISPB. putting the routes in the route table is easy enough
```
route add -net 0.0.0.0/0 gw <ISPA gateway address> metric 10
route add -net 0.0.0.0/0 gw <ISPB gateway address> metric 20
```

Three problems exists as i see it.
1, what happens when the net connection fails on the modem and doesnt take down the server nic?
2, what happens if the ISP is having routing issues but all link statuses stay up?
3, in the event that ISPA returns from a failure, how to swing the traffic BACK to ISPA?

One possible way to cure the first two problems would be to have a script run that pings certain addresses on the net, if they fail to respond then you could have the script take the interface down, thereby forcing the failover.

---


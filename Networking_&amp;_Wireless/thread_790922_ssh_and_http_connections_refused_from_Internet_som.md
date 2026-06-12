---
title: "ssh and http connections refused from Internet *sometimes*"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2008-05-11
I've been running an ssh and http server on my home computer for a couple of weeks.  *Sometimes* when I try to connect to it from a machine beyond the local network, or when I attempt a connection by using my router's Internet IP address (that is, not the 192.168.x.x address), I get a "connection refused" message for ssh, or "Failed to Connect" error in Firefox if I try to access my http server.  The rest of the time, the connection works without a problem, and I'm seeing no consistency between when it works and when it doesn't.

I am always able to connect from a machine on the local network (a 192.168.x.x machine) or to localhost, so I don't think that the problem lies with any local configuration.

I've done research and most threads say that problems like this are due to firewalls or failure to forward ports from a router.  My router, a Netgear WPN824v2, doesn't have any ports blocked, and is set to forward the ssh and http ports to my machine.  I have verified that the settings are correct during times when the connection gets refused.  I also don't have any services blocked on my computer.  I contacted my ISP to ask if it might be blocking the services, but it says it doesn't.  Rebooting my router doesn't help, nor does trying to connect via non-standard ports (after configuring the forwarding correctly).

I'm at a loss on what to try next.  Is there a way to do a kind of traceroute on an ssh request to see where exactly it's getting refused (this would at least let me know whether it's the ISP or the router)?  Is there any logical explanation for why http and ssh connections would work fine sometimes and not other times?

Thanks in advance for any help.

---

### Post by SpaceTeddy on 2008-05-12
does your ISP kick you out every now and then to assign you a new IP-address ? or do you statcially always run the same IP to the internet ?

That would be about the only explanation i have as to why it blocks something. 

Otherwise, you would need to to log the traffic on the server and see if the pakets come through when the connection is refused. If they do, then something is up with the server - if they don't (what i suspect) then either your router or your ISP is blocking something...

---

### Post by pytheas22 on 2008-05-14
Thanks for the reply.  I don't have a static IP but it doesn't seem to get renewed unless the cable modem gets rebooted, which only happens once every few months.  I'm sure the IP address to which I was trying to connect was correct.

Anyway, I've noticed that if I delete the port forwarding rules on my router (using its configuration utility in a web browser) and then rewrite them, the forwarding will work for a while (anywhere from an hour to twelve hours) and then break again, and it can only be repaired by refreshing the rules.  This has led me to conclude that there's most likely some problem with the router itself where it seems to forget port-forwarding rules after an arbitrary amount of time.  I guess it's just either some bug in the software or a hardware problem.  I'll be moving soon anyway and will have a new router, so I'll probably let it go for now.  But I guess the lesson is: don't buy cheap wireless routers if you need to run an ssh or http server.

---


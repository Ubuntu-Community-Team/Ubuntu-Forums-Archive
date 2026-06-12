---
title: "dhcp problems? could be ubunutu NOT using dhcp (it's BOOTP)"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by rocket777 on 2007-04-29
I see there are a lot of posts about dhcp problems. Most are wireless issues, but many are wired connections too.

I have a ***WILD ***hunch. It's *only *a hunch. Here's my findings/ideas.

[LIST]
[*] I discovered that my 7.04 ubuntu on a wired connection is not using the full DHCP protocol. It appears it is using the backwards compatible BOOTP protocol - designed for diskless workstations.

[*] Maybe!! this subset of DHCP is not as well supported by newer equipment (dhcp servers) that are on the market today.

[*] It's much harder to find out this sort of thing today, since it requires either looking at the source code, or having a hub instead of a switch and a little knowhow to use an ethernet sniffer. I sometimes need to do this so I bought a hub (and they actually are hard to find - and even cost more than a switch nowadays).

[*]I got to looking because my router will not show a connected ubuntu system. When I ask to see the dhcp client tables, my windows systems all show up, but not my ubuntu systems.

[*] I found that my ubuntu system uses only the 2 packet protocol of BOOTP while my windows boxes are using the full 4 packet DHCP protocol. 

[*]I don't know what all the differences are, but I think that BOOTP does not have leases and there might be other quirks. The rfc's are too dense for me, so I can only speculate here.
[/LIST]


I don't expect this has anything to do with wireless issues, but it could be a cause of wired ethernet problems.

Again, this is just a crazy idea, but it might be meaningful :idea: :idea: and so I am posting it here - so please, if this is a dumb idea, be nice to me :)

---

### Post by tturrisi on 2007-04-29
It could also be that the driver for an adapter does not fully integrate w/ dhcp and falls back to using workarounds, ie. 2 packet vs 4.

---

### Post by rocket777 on 2007-04-29
In looking further, I don't think this would be a driver problem. Here's why.

1. The 2 packet protocol is essentialy packets 3 and 4 of the 4 packet protocol. These show up with no problem. 

!! just found !!  

When I use the high level network manager (the gui) and uncheck then check the wired connection, it does a release,  and then on the reconnection, it does the full 4 part protocol - discover, offer, request, ack. But it still does a second request, ack which I wonder about. 

!! and !! if I zero out the file /var/lib/dhcp3/dhclient.eth0.leases  then on the next reboot, it will do the four part protocol. Apparently this file saves the last lease so it can reuse the remaining portion of that lease on a reboot, and does just a 2 part protocol in this case.

BUT, I still don't know why it won't show up in my linksys router's dhcp table. 

I did find that windows also seems to do this same thing, i.e. a 2 part protocol if the machine is rebooted while it has a lease. But something is different, since it will show up in the linksys dhcp tables. 

It might still have something to do with the fact that ubuntu sends this request,ack twice. But I really am grasping at straws here....

I was thinking of reporting this as a bug, however, I can't get through with the bug reporting system (keeps timing out on me).

---

### Post by Alex&amp;Linux on 2007-05-02
Could be....
Im having trouble obtaining IP via DHCP. Had noticed this earlier while looking into the issue.
Ran "sudo tcpdump -v"

code:
 
 IP 0.0.0.0 bootpc > 255.255.255.255.pootps: BOOTP/DHCP request from 00:18:f3:27:af:61 (oui unknown)
 length 300

Im a complete beginner, and so the inner significance of this I do not understand, but it looks like my NIC isnt making a simple DHCP request, which may indeed mean that the packet(s) arent in the proper form to be accepted by my Linksys routers server...
¿Quien sabe?
Anyhow, Im going to try some of the suggestions given, and for those I thank you!

---


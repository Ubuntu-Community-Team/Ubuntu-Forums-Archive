---
title: "Doing things &quot;right&quot;: Add a extra route."
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by DataJohan on 2007-09-04
Hi,

I have a box that will be a Asterisk server. To make things less problematic, i have installed two network cards. One will be external IP with no NAT inbetween the box and Internet. The other has got an intenal IP (192.168...) to reach our voip phones.

The box sits IN PARALLELL with a D-link router that gives our internal network NAT access to Internet but also handles a few ipsec tunnels to other locations. (other 192.168... nets)

I have default route/gw on the EXT network.

I understand that i need to add a route on my INT network, to reach the other locations over ipsec through my dlink router. 

My main question si just WHERE, according to the Ubuntu way, to not conflict with any "automated setup" like the /etc/networking/ and so on, should i add this routing?

In Windowze you just add the /p flag to make an extra route persistent between boots. I know about /etc/rc.local but is this the most "Ubuntu clean" way of doing such thing??

For example, nowdays you can configure bridge interfaces in /etc/networking/interfaces . Is there some similar "modern" way of configuring "non default routes"?

Sorry for the long post. :oops:

Thanks in advance

/Johan, Phuket

---

### Post by Sendervictorius on 2007-09-04
You add routes with the "route" command. The command by itself gives a list of the current routes.

On the command line, type "man route" to read how to use the command to set routes.

---

### Post by DataJohan on 2007-09-04
Hi, Thanx for answering.

I know how route command works.

I just want to know if there is a better way to add this information that to add a cruel "route add..." line to rc.local.

/Johan

---

### Post by DataJohan on 2007-09-04
Hi again

No one that can help me with "Best Practice" Where to add a non standard route so that it does not conflict with any more automated or high level configuration tools?

Plz HELP!:)

/Johan

---

### Post by Sendervictorius on 2007-09-05
The route command should be all you need. No rc.local needed. Just sudo route!

It should not conflict with any apps. I can't think of which ones you mean, but they should all be accessing the same routing table.

---

### Post by netztier on 2007-09-05
> **DataJohan said:**
> Hi, Thanx for answering.

I know how route command works.

I just want to know if there is a better way to add this information that to add a cruel "route add..." line to rc.local.

/Johan

If it's just a one-liner, add it to /etc/network/interfaces, under the corresponding interface with the **up** keyword:

```
auto eth0
iface eth0 inet static
 address xxx.xxx.xxx
 ...
 ...
** up route add... **
```


If you want to do more complex things, write a shell script that holds the route commands and whatever else you want it to do.  If you want it to run specifically for this interface, you can call it  from this "up..." line.

If the setting in the script are "of global interest" for all interfaces, place it in **/etc/interfaces/if-up.d/** and it will be executed automatically. Things like configuring speed/duplex modes can be done from the /etc/network/if-pre-up.d directory.

best regards

Marc

---

### Post by DataJohan on 2007-09-05
Hi,

Sendervictorius: 

Yes you are right. It is only the ROUTE ADD command that is needed but it will not be persistent on reboot, nor will it be removed and added again if the interface is reconfigured.

netztier/Marc:

That was the kind of solution i was looking for! Just like it feels wrong to configure bridges manually, now when they could be configured through network/interfaces, it felt wrong to just add the ROUTE command anywhere where it would have been executed.

After reading man interfaces, i see it clear:
post-up route add .....
pre-down route del ....

Thanks to you both for helping out!

Best Regards

Johan@phuket

---


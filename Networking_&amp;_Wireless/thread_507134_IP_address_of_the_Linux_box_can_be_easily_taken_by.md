---
title: "IP address of the Linux box can be easily taken by Windows machine"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by Nacker on 2007-07-22
Hi, everybody,
We have IP address conflict problem with our home network. It consists of approx 200 computers, all have static IP addresses assigned. The server is running Ubuntu 7.04 and acts as the gateway to internet for all network users. Users machines are running Windows XP.

The problem is that the user can easily assign itself the IP address of the server and it will be assigned without any warning (the one that states that IP address is already in use on the network). After that all other users machines start communicating with the hijacker and lose the internet connection and server access. At that moment there are two same ip addresses on the network.

This problem generally affects all linux boxes.
If you try to take the IP of the Windows box using the other Windows box, you'll get the warning "IP address is already in use on the network", which is not happening when you try to take Linux's IP.
So, I guess, the question is obvious, how to avoid that? There is no way for us to buy an expensive controlled switches. DHCP is not an option either as the user sill can assign itself the IP of the server. I think it's not good enough to hide Linux box behind windows either ;-)
Thanks guys in advance for your answers.

---

### Post by QuinnHarris on 2007-07-22
Are your windows systems basically out of your control?  DHCP would work unless you are trying to protect against someone intentionally trying to take down the network by assigning a system a static IP.  And if this is a problem, the duplicate IP detection in windows can be worked around (by using a linux boot CD or laptop for example).  If the systems are under your control and malicious use isn't a problem, setup DHCP and all the systems to use it.  If they are out of your control, the only thing that could reasonably ensure one system couldn't screw up the others that I am aware of would involve using VLAN switches and placing each home customer on a different vlan.  All vlans can be served by one linux box.  I know a 48 port smart VLAN switch can be had for less than $300.  I use this configuration in an office building to serve 12 different offices.

---

### Post by Nacker on 2007-07-23
**QuinnHarris**
Thanks for the reply.
*Are your windows systems basically out of your control? DHCP would work unless you are trying to protect against someone intentionally trying to take down the network by assigning a system a static IP.*

Yes, that's the main problem, I don't have control over the windows machines. We are running a private non-commercial home network that is spread across several buildings. The PCs are the property of their owners and I can't control them. Sometimes user just make a mistake and sets the gateway (Linux box) as its IP address. This case at least can be tracked by arp records analysis. Sometimes someone takes serve's IP intentionally - this is hard to trace.


*And if this is a problem, the duplicate IP detection in windows can be worked around (by using a linux boot CD or laptop for example).* Could you please, be a bit more specific on this? I didn't catch, sorry.

VLAN switch is not an option, as we have about 80 switches that are spread all over the network. Replacing 80 SOHO Switches by VLAN ones will cost :).
I really hate the idea of using windows box as the server, but if we run into many scammers someday this might be the only solution (the cheapest at least) as windows will not give its IP to other windows machine. I just wonder, why it's happening in case of linux?
Anyway, I really appreciate you help, thanks for that.

P.S. As temporary solution we currently ask users to put static arp record for the server in autostart, so most of them always have "arp -s SERVER_IP SERVER_MAC" record in their arp table. But this solution is far from good as there are too many problems in case server's hardware needs to be replaced.

---

### Post by #Reistlehr- on 2007-07-23
Is the DHCP Server fromthe router or is it running on the linux box?

---

### Post by QuinnHarris on 2007-07-23
One of your home users can hijack the gateway IP using Linux even if the gateway is running windows bringing down your network.  They would have to be a bit more sophisticated to do that.  The point is, even if you could prevent the IP from being taken by a typical Windows box you won't protect against ambitious malicious users.

I am not totally sure but the package farpd in universe might be just what you are looking for.  You will need to put the gw address in /etc/default/farpd under NETWORK.  Then "sudo /etc/init.d/farpd start" to see if it works.  Use update-rc.d to get it to start at boot.

Also check out
[http://support.microsoft.com/kb/q120599/](http://support.microsoft.com/kb/q120599/)
[http://marc.merlins.org/linux/arppatch/](http://marc.merlins.org/linux/arppatch/)

Is there a good reason you don't use DHCP instead of having all the users use a static IP?

It kinda sounds like you have a bit of a cluster *ck of a network on your hands.  80 SOHO switches all daisy chained together has to be nightmare.  I can image many of them are in houses where people sometimes unplug them, or just have failures (do you have much lightning).

You should strongly consider using VLAN switches in the future (not expensive CISCO stuff though).  Something like [http://www.newegg.com/Product/Product.aspx?Item=N82E16833122146](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122146)
That's less than $8 USD per port.  These switches support Spanning Tree Protocol so it can deal with a mesh network topology with some redundancy (some SOHO switches do this).  Each customer would be assigned a VLAN.  All those VLANS would show up as a different interface on Linux, giving each customer a different gateway and isolating the subnets if desired.

I know the famous WRT54G wireless router actually has a VLAN switch in it, of course you need after market linux firmware to utilize it (OpenWRT).  Other Linux driven network appliances could have similar features.  VLAN has become a very common feature, you might already have hardware that supports it or be able to get it for less than you expect.

---


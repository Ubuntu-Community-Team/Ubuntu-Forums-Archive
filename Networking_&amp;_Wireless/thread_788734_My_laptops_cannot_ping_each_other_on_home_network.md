---
title: "My laptops cannot ping each other on home network"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by rikxik on 2008-05-10
Hi,

I am using Ubuntu gutsy and am able to connect to internet using the WRT54G router provided by my ISP. The setup is using DHCP. I am able to ping localhost, gateway, google. This machine has ip 192.168.1.101 

I am also able to connect my office laptop to my network and get on the internet. This machine has been assigned ip 192.168.1.100.

However, I simply cannot ping these two machines from each other even when they are using the same DHCP based network even with IP Address instead of machine name. Any ideas?

Thanks.

---

### Post by helgman on 2008-05-10
Have you tried to ping both ways?

There might be firewalls involved ... or there might be some sort of isolation done in the router (are you using wired or wireless connections?).

After you've tried to ping, check the arp-cache to see if they communicate at all. In Linux the command is *arp -n* and if I remember it correctly it's *arp -a* or something similar in Windows.

Any luck?

Helgman

---

### Post by rikxik on 2008-05-10
Thanks for responding. I've tried both ways. Even I was thinking regarding some possible filtering in Router. I checked and the firewall is disabled in Router and in one of the laptops (192.168.1.101). The other laptop (192.168.1.100) is running a firewall (but I cannot disable it since the configured Windows policy restricts me from making any changes).

In the router, the settings are:
> Block Anonymous Interest Requests - Off
Filter Multicast - On
Filter Internet NAT Redirection - Off
Filter IDENT(Port 113) - On

I'm using Wireless setup. I did ping and then I did arp -n:

> $ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.100            ether   00:1B:77:93:57:43   C      eth1
192.168.1.1              ether   00:18:39:84:62:12   C      eth1

Unfortunately I'm not very good at interpreting this :(

---

### Post by fain on 2008-05-10
> **rikxik said:**
> Thanks for responding. I've tried both ways. Even I was thinking regarding some possible filtering in Router. I checked and the firewall is disabled in Router and in one of the laptops (192.168.1.101). The other laptop (192.168.1.100) is running a firewall (but I cannot disable it since the configured Windows policy restricts me from making any changes).

In the router, the settings are:


I'm using Wireless setup. I did ping and then I did arp -n:



Unfortunately I'm not very good at interpreting this :(

the laptop running the firewall is most likely the problem. I wouldn't disable the router firewall though, im sure that wasn't the problem.

---

### Post by rikxik on 2008-05-10
I thought even if I couldn't ping the firewalled laptop, it should have been able to ping out to the non-f/w one. In office, I'm able to ping from it to other machines w/o any issues.

---

### Post by helgman on 2008-05-10
I agree with fain, the firewall-settings in your router only filters between your network (where you have your laptops) and the Internet.

If you did the ping from the client with IP-address 192.168.1.101, then it's communicating with the other laptop (192.168.1.100) on one level. That is what the post in the ARP-cache is telling. So the "problem" there is most likely a firewall setting.

I have a WRT54G-something and I know there is a setting under wireless that says something like "AP Isolation". I don't have the router set up so I can't investigate right now, but the [user guide](http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fpdf&blobheadervalue2=inline%3B+filename%3DWRT54G_UG_WEB_20070529.pdf&blobkey=id&blobtable=MungoBlobs&blobwhere=1193775701174&ssbinary=true&lid=0703200349B41) states (page 13):

> **AP Isolation** This isolates all wireless clients and wireless devices on your network from each other. Wireless devices will be able to communicate with the Router but not with each other. To use this function, select On. AP Isolation is turned Off by default.

As you see it should be turned off by default ...

And yes, you should be able to ping any computer that normally would respond to an ECHO REQUEST.

Have you checked the ARP-cache on the Windows machine?

To bad I don't have a XP machine (if that is what you use) here, there are some commands that might let you investigate the firewall rules ...

Regards,
Helgman

---

### Post by helgman on 2008-05-10
The Windows Command (at least in XP and Server 2003) for checking the built-in firewall settings regarding ICMP is **netsh firewall show icmpsetting**. This should work even if your not Administrator. If it only leaves a (few) blank line(s) you don't have any "exceptions" for ICMP so there will be no replays to ICMP-packages (such as ping ECHO_REQUEST).

Regards,
Helgman

*EDIT: This is how the machine filters INCOMING packages. Just want to make that clear, should not effect the way it send them ...*

*EDIT: You might also be able to find these settings via the Control Panel, if you don't like using the Command Prompt.*

---

### Post by rikxik on 2008-05-10
The issue is identified. I was connected to my office VPN (Nortel) at the time I tried to do the ping. When I disconnected from the VPN, I could ping both ways between the machines! So, the firewall wasn't the culprit. So, it would seem that the Nortel VPN client (Contivity) does some mess-up of routing where everything must be going to the defined gateway instead of the router. Atleast that's what I think :)

Now, the final step is to figure out how to ensure that only work related applications gets routed to the vpn gateway and the remaining/non-work apps get routed to my home gateway :) 

Many thanks for all the inputs provided!!

---

### Post by mips on 2008-05-10
Might want to look into static routes.

---


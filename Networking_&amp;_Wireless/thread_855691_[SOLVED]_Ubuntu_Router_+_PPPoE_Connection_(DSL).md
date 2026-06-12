---
title: "[SOLVED] Ubuntu Router + PPPoE Connection (DSL)"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by WIGGMPk on 2008-07-10
I have Ubuntu Hardy Heron Server installed using the following "modules=ppp-udeb". The installation went fine, pppoeconf was able to setup the DSL connection perfectly.

The server consists of the following interfaces.

eth0 (primary network connection, connected to the DSL modem set into bridge mode)
eth1 (internal LAN with static IP, connected to a wireless router set into bridge mode)
eth2 (future network interface for DMZ currently disabled)
ppp0 (eth0, primary network interface for DSL connection)

The server can reach the internet without any problems. The internal LAN is having the issue, they can get an IP address fine. /etc/resolv.conf reflects the appropriate information. DNS is setup correctly on the server. The firewall rules are setup (to what I think is correct). It is set to MASQUARADE on outgoing interface ppp0. I used webmin to configure this, and have setup the firewall rules exactly the same for my cable connection (expect for the use of ppp0) and have had no problems.

The clients on the LAN can talk to certain places. I can get to google.com, and acctually search something, but then after clicking on a search result it just sits there and says "waiting for <insert url here>"

Other sites like msn.com or youtube.com just sit and try and load. I have no content filter, this is a fresh install. All updates, and firewall rules worked previously with cable except for this ppp0 interface.


Any help would be appreciated, more info available upon request.

---

### Post by syscode on 2008-07-10
Hummmm

I wonder if we have a similar problem.. (see my post on [http://ubuntuforums.org/showthread.php?t=855718](http://ubuntuforums.org/showthread.php?t=855718) )

Can you get bbc.co.uk ??

Main though is not a server, just the desktop version of 8.04..
Also on AMD64 3200..

---

### Post by WIGGMPk on 2008-07-10
I believe the situations may be related, but not completely similar.

I believe my problem is with my NAT / Firewall Rules.

Although is doesnt make sense. Im going to post my firewall rules the best I can remember them.

INCOMING (Packet Filter - DEFAULT 'Drop')
ACCEPT - if incoming eth1
ACCEPT - if incoming lo
ACCEPT - if incoming ppp0 and connection is ESTABLISHED & RELATED
ACCEPT - if incoming eth0 and connection is ESTABLISHED & RELATED

FORWARD (Packet Filter - DEFAULT 'Drop')
ACCEPT - if incoming ppp0 & if outgoing eth1
ACCEPT - if incoming eth1 & if outgoing ppp0
ACCEPT - if incoming eth0 & if outgoing eth1
ACCEPT - if incoming eth1 & if outgoing eth0

OUTGOING (Packet Filter - DEFAULT 'Accept')
No Rules Defined

OUTGOING (Network Address Translation)
MASQURADE - if outgoing ppp0
MASQURADE - if outgoing eth0


The rules defined with "eth0" are not being used right now, but I have tried switching ppp0 with eth0 and trying both of them exsisting at the same time just to see if its the problem.

It does not seem to fix it at all. The other page I can get to is verizon.net (trying to check my mail, on one of the clients). I can get to the landing page fine (even though it takes forever to load it) but will not go anywhere else. Also, while trying to check for updates, it will hit some of the repositories and fail on more then 50% of them.

While the server machine handles everything fine, no connection issues.


Any thoughts.

---

### Post by WIGGMPk on 2008-07-11
> BUMP

This is very important, does anyone have a thought to rectify this...?

Thanks in Advance

---

### Post by WIGGMPk on 2008-07-13
Does anyone have a clue what might be the problem here??

---

### Post by WIGGMPk on 2008-07-14
I have tried everything I can think of.

I have discovered another site that my LAN clients can reach:

cnn.com
google.com
verizon.net

But other places It just sits and loads.... Like these:
msn.com
hotmail.com
youtube.com
yahoo.com
wachovia.com


Although, on the host machine, I can execute this:
```
links youtube.com
```

And it will display it immediatly.

This is driving me insane....!!!

---

### Post by WIGGMPk on 2008-07-15
Bump

---

### Post by lswb on 2008-07-15
I don't recall the exact details, but checking the man pages for ppp and pppoe (or googling) will mention setting an mtu of 1492 or less for using pppoe. IIRC this should be set for all systems on the subnet that may send packets through the pppoe gateway. 

A normal ethernet frame is a max of 1500 bytes, with pppoe, 8 bytes are used for the ppp header, leaving only 1492 for the ethernet frame. If an app tries to send a 1500 byte ethernet packet over the net, when that packet needs to be encapsulated into a ppp packet, there is no room for the ppp header. I'm simplifying here, google for a better explanation. Hope this helps with your problem.

---

### Post by WIGGMPk on 2008-07-16
> **lswb said:**
> I don't recall the exact details, but checking the man pages for ppp and pppoe (or googling) will mention setting an mtu of 1492 or less for using pppoe. IIRC this should be set for all systems on the subnet that may send packets through the pppoe gateway. 

A normal ethernet frame is a max of 1500 bytes, with pppoe, 8 bytes are used for the ppp header, leaving only 1492 for the ethernet frame. If an app tries to send a 1500 byte ethernet packet over the net, when that packet needs to be encapsulated into a ppp packet, there is no room for the ppp header. I'm simplifying here, google for a better explanation. Hope this helps with your problem.

Dude you have no idea how estatic I am that someone answered with a theory on why it might not be working.

I understand what your saying behind the MTU settings being to high. But, the host machine gets out to the internet perfectly. Would this be something pppoeconf had already setup?

Furthermore, why would I be able to get to certain sites and not others?

Thanks for you help, im going to set the MTU lower when I get home.

---

### Post by lswb on 2008-07-16
You can find a much better explanation than I can give by googling, but the symptoms you describe are not inconsistent with the mtu setting problem. 

As I understand it, the gateway machine, being configured for pppoe, knows to negotiate the lower mtu when it sends a request out on the internet. Other hosts that go through this gateway, do not know about it and can send a request out without negotiating the lower limit. If the return packet from say a web server is 1492 bytes or less, it can be routed back to the requesting host. If it is more, than the pppoe system will reject it and send a retransmit request to the web server. The remote server still does not know that the packet size must be limited, so it sends another 1500 byte frame. While this looping is going on, the poor computer that first sent out the request is timing out.

BTW, many if not most DSL modems these days can do the pppoe translation thing and act as routers and dhcp servers, you may want to consider that for your setup.

---

### Post by WIGGMPk on 2008-07-22
Settings the MTU to 1492 on all Server & Clients Adapters corrected the problem


Thank you very much.

Is there a parameter for dchp3-server to just PUSH the MTU settings to all clients??

---

### Post by lswb on 2008-07-22
I'm pretty sure you can set this in the dhcp3.conf file or whatever file it uses to store configuration, but I don't have it installed on my system. Does the man page specify? If not you should be able to google it pretty easily. Glad your main problem was fixed.

---


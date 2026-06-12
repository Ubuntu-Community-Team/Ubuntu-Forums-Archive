---
title: "SSH Connection Troubles..."
date: 2005-09-20
forum: Networking &amp; Wireless
---

### Post by GeekWar on 2005-09-20
I've been searching the forums for quite a while now not quite finding anything applying directly to my problem; however I've tried multiple things so far with no success. Please excuse me if I'm not thorough enough for an immediate answer but any help would be greatly appreciated.

My problem:
I'm trying to connect to a telnet server for some hacking games I used to tinker around with on my old windows box. I started out with the following command:

> telnet drill.hackerslab.org 23 

with the response:

> Trying 211.239.123.40...
telnet: Unable to connect to remote host: Connection refused

After doing some searching I'd come across multiple threads advising against using telnet at all and instead using SSH. So I've installed ssh as well as ssh-server and verified a successful connection to myself (localhost).

I've used the following commands:

> ssh drill.hackerslab.org 

& > ssh -p 23 drill.hackerslab.org 

Still getting told my connection is refused. I've checked my firewall on my router and tried all sorts of permission changes (Even setting all applications & ports to DMZ (temporarily)) with no success. The router is for a DSL service that I'm not in control of nor am I paying for so I'd like to avoid needing to permanently change anything if possible. However I'm open to any help that could be provided right now.

Again excuse me if I was too vague; I'd be more than happy to help in any way I can answer any questions to better aid some assistance with my problems. Thanks

---

### Post by KingBahamut on 2005-09-20
IP/IPsec Passthrough on your adsl router enabled?

---

### Post by GeekWar on 2005-09-20
Well - erhm...
I'll do my best here
The router type is a 2Wire wireless DSL router
The IP Address Type is set for Private NAT

The best documentation I can find on this idiot-proof router about IPsec is the following:

> Yes. The 2Wire HomePortal supports NAT (Network Address Translation). Many applications use NAT, which enables a LAN to use one set of IP addresses for internal traffic and a second set for external traffic. However, some applications cannot work with NAT unless an ALG (Application Level Gateway) is used to allow the application data to route to the Internet. 2Wire has incorporated an ALG in the HomePortal that allows IPSec VPNs to pass through the HomePortal in ESP Tunnel mode. Many VPN clients can support ESP Tunnel mode. 

I searched high and low through the configurations on the router and saw nothing regarding the ability to change any of these settings. (First thing I looked for was port fowarding/etc settings but no such settings exist for this router I'm afraid)

I'm starting to think I'm sh*t outta luck in this case.

---

### Post by KingBahamut on 2005-09-20
Unless you can pinhole through the router, which Im thinking you should be able to do Geekwar. 

Ill look and see what I can find about your router. Got a few friends down at the local pnap.

---

### Post by GeekWar on 2005-09-21
Yes I've basically verified my problem is with my router as I've tried connecting to this server as well as others from other computers in the house with the same connection refusal.

Ah I should have known better to move out here in the woods with this crappy DSL connection!  ](*,) 

Oh well; I appreciate the help KingBahamut

---


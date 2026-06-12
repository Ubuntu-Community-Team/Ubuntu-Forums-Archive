---
title: "Network File Sharing"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by lorenfb on 2008-06-10
Running 7.04 and 8.04 on two different machines.
Both have problems with accessing either a NAS
or WIN XP file sharing on the network when a DSL modem 
is attached to the router. When network access is attempted 
by Ubuntu, the DSL modem LAN light flickers and Ubuntu
is unable to access network files.

Once the modem is powered off and the router is reset, 
both machines can access the NAS or XP files on the network.
To again access to the internet via the DSL modem, the
router must be reset after the modem is powered on which 
no longer allows access to the NAS nor the XP files
by the Ubuntu machines.

Using a Linksys router (non-wireless). Tried another
router (Netgear) and the same problem occurs. Using both
XP and MAC O/S machines on the network which have no problems
accessing the NAS nor using file sharing with the DSL modem 
attached to the router.

Thanks for your insights.

---

### Post by dmizer on 2008-06-11
sounds like your dsl modem is not only a modem.  it may also be a router.  to test this, you should connect a computer directly to the dsl modem and check the ip address.  if you get a [non-routeable](http://support.easystreet.com/easydsl/general-info/iptutorial.html) ip address like 192.168.x.x then your dsl modem is also a router.

if your dsl modem is also a router, then you will have to configure your linksys or netgear router as a network bridge (disable nat), or make sure that your external router is on a different subnet than your dsl modem's router.

---

### Post by lorenfb on 2008-06-11
Thanks for the feedback.

Checked the modem and it's not a router too as suggested.

The key point is that other O/Ss (MAC/WIN) have no problem
accessing each other and the NAS via file sharing. It's only
Ubuntu that has this problem. I can directly access (192.168.1.107)
the NAS, i.e. get into its setup app, via Ubuntu but can not 
access its "share" nor the other file sharing machines with 
the modem connected to the router.

This problem appears similar to:

[http://ubuntuforums.org/showthread.php?t=820272](http://ubuntuforums.org/showthread.php?t=820272)

Have this problem with Ubuntu 7.04 running on another machine also.

Thanks again for additional insights.

---

### Post by jetsam on 2008-06-11
Is there any chance you have the modem connected to the LAN, "local", or "uplink" ports of the router instead of the port labeled WAN or "internet?"  It's possible that a mis-wiring like that could cause the behavior you describe.

---

### Post by molotov00 on 2008-06-11
Clearly this isn't an easy one to fix... but... I'd start with this:

Do pings to the other computers work? Try by hostname and by IP.

I have a wireless extender (entirely different than your situation, I know) that ***** up my network so hostnames dont resolve, for example. My point is that hostnames not resolving could create the situation you're talking about. BTW, you can mount Samba shares by IP address.

---

### Post by lorenfb on 2008-06-12
"Is there any chance you have the modem connected to the LAN, "local", or "uplink" ports of the router instead of the port labeled WAN or "internet?""

Thanks for the suggestion, but the modem is connected to the WAN
port of the router.

"Do pings to the other computers work?"

Unbuntu always "sees/finds" WORKGROUP but not the "shares",
e.g. NAS. Once the DSL modem is disconnected, Ubuntu has no
problem.

My next plan is to buy another modem, i.e. cable which are
basically generic, and just connect it (obviously no internet
access) and determine if the problem is unique to the DSL modem.

---

### Post by jetsam on 2008-06-14
I have a different idea on this one.  Some DNS servers, including OpenDNS, return spurious false positives when they should return NXDOMAIN (negative) responses.  This interferes with the Ubuntu default setup of Samba and breaks Nautilus browsing. 

When your modem is disconnected, you have no DNS server available, so you don't get the false positives and Samba browsing works OK in Nautilus.  

If I'm right, probably the easiest way to fix this  is to force Samba to try broadcast name resolution before it tries DNS by adding this line to the global section of your smb.conf:

```
name resolve order = lmhosts bcast wins host
```

Then restart Samba with:
```
sudo /etc/init.d/samba restart
```

Hope that helps.  It's less expensive to try anyway than buying a cable modem you can't use.

---

### Post by lorenfb on 2008-08-24
The problem was the DSL modem (Westell) which attempted to connect
to internet when a local general network address was given by
Ubuntu. Another DSL modem which was an integrated modem/router/wifi
(Verizon - GT704WGV) did not have this problem.

With further troubleshooting, the modem problem was easily resolved
by a more direct Ubuntu network addressing approach:

NAS address: 192.168.1.XXX

Then to access the share on the NAS;

smb://192.168.1.XXX/share

Thanks to all that helped to provide insights.

---


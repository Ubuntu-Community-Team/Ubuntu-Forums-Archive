---
title: "Where to install Squid Proxy in network and using a software bridge"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by RaisinBoy on 2014-01-30
Hi there,

I know that it seem obvious that you would put the squid box before the gateway, but I am not sure where...

Current network layout...

Router connects to a singe Windows 2008 R2 Server with 2 NICS. Internal and External. Server handles all DHCP, DNS and Routing and Remote Access and is the internal netw.

Would I put the Squid box between the router and the Windows server, or do I put it between the servers Internal NIC and the rest of the network?

For either, can I simply use two NIC's in the Ubuntu box running Squid and bridge them, or is there merit to downloading a software switch to do it? Which would be better to pull off NetFlows. And no I do not have a managed switch available that I could use...

The point of me wanting a Squid box, is primarily to log Internet traffic so that I can see who is abusing bandwidth, and secondly to have the benefit of caching.

If I should be looking to do or use something else, I would greatly appreciate the advice.

Matt.

---

### Post by TheFu on 2014-01-30
I'll be honest. I would never connect a Windows box to the internet in the way you have described, especially if it was running those critical network services.  Windows wouldn't be anywhere near the DMZ.
```

WAN-router
   pfSense-firewall
       {DMZ switch}
              {DMZ Linux/UNIX/BSD boxes}
       Core-router w/ firewall
              {Windows Server Network}
              {Wired Desktop Network}
              {Wifi Network}
```

Does that make sense?

If you just have 1 router, 1 Linux machine and 1 Windows server, then:
```
WAN-router
     {DMZ Linux/UNIX/BSD boxes}
              {Windows Server Network}
```

Have all the internal machines point to the DMZ squid proxy as their default gateway.
Clearly the Linux machine would need to be hardened, secured, patched, remote logged, and maintained. Nothing extra on that box, definitely NOT any GUI.

If your end-users can be known by IP, then just let the router software handle your bandwidth management. pfSense does this easily, though you can use squid and a few squid addons too.  Check out Cacti for fancy network graphs - do NOT run it on an externally accessible box. I have a server for logs and network monitoring where all the logs from every server gets sent using rsyslog. Easy peasy AND more secure.

---

### Post by SeijiSensei on 2014-01-30
I find it easiest to place the Squid proxy between the router and the local network, but it need not be configured that way.  For instance, if you can write rules for your router that can forward traffic based on the destination port, you can have it intercept all outbound port 80 traffic and forward it to the proxy server.  If you place the proxy between the network and the router, you'll need to enable packet forwarding (see /etc/sysctl.conf for details) and add a NAT masquerading rule to your iptables ruleset.  Otherwise your users won't be able to access any external services on ports other than 80.

Do not use bridging.  Just assign both network cards an address in their appropriate address spaces and enable packet forwarding.  Linux will handle the rest.

---


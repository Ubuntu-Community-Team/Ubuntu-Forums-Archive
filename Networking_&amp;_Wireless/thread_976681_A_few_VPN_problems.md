---
title: "A few VPN problems"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by williambertram on 2008-11-09
Ubuntu version: 8.10 (with current updates as of November 9, 2008).  Tested both with upgrade and fresh install.

Hardware tested on:  Stock Dell Optiplex GX520 SFF, stock Dell Latitude D610, stock Dell Latitude D620.  All with current firmware.  Also tested on my home brew system.  Same testing results from all hardware.

Problem #1:  KVPNC will not disconnect or close the application after connecting PPTP.  Not sure if the problem occurs for other types of connections, as I don't have a server available to test for those.  Connect PPTP, everything works fine, then disconnect and the green checkmark stays on the tray icon, and the tray icon does not go away.  Connection is dropped however.  This does not occur in 8.04LTS.  Have to log out or reboot to clear the icon.

Problem #2:  Configuration for the "built in" connection manager VPN needs some work.  I'm assuming the target audience is home users who want to easily connect their work PPTP connection.  If that's the case it should be set up similar to the Windows XP and KVPNC VPN connection managers.  Essentially what's wrong and missing (IMHO) is the following:

2a.  No check box for "Keep default route" or "Use default gateway on remote network".  There is a box for "ignore automatically obtained routes" but it doesn't seem to do the same thing.  What we need the ability to easily do is send all VPN traffic through the VPN connection, and all other traffic through our normal ISP connection.  XP just kind of "magically" does this, and KVPNC allows you to create routes to remote networks (Example: 172.16.12.0/22).  Ubuntu's built in network manager has configurable routes, but far as I can tell it's only possible to configure routes for specific hosts.  On routes we just need the ability to type an IP address for the remote network, subnet mask, and choose which interface to use (Example: ppp0).  I've messed with this thing for hours, googled, and searched forums.  The only way I can get it to work is by sending "ALL" traffic through the VPN connection or configuring routes to individual hosts (which is not practical due to the large amount of hosts on the remote network).

2b.  Saving the password in the VPN manager is broken.  If you type in the password in Configure VPN, then save it, the connection will fail with "Bad Secret" or something like that.  If you type the password in manually it will connect.

At the very least, configuring VPN in this manner would be more familiar to people used to XP / KVPNC style VPN configuration.  I'm just assuming this would encompass 90% - 99.99% of the people using it.

If I'm just flat out not understanding how to configure my PPTP connection through network manager, which is highly possible, someone please post some "for dummies" instructions for me.  :)  

I would be EXTREMELY happy if the VPN configuration in network manager worked like I mentioned above, because I'm really big on trying to use as many of the default apps as humanly possible.  I ONLY use Ubuntu on the home computer (no Windows in the house) and work from home 1 day a week, so I rely heavily on the PPTP connection.  KVPNC currently works fine, it's just an annoyance to reboot or log out / in every time I want to clear the icon off of the tray.

Again, thanks to the entire community for another fabulous release of what I consider to be the best operating system ever.  8.10 is awesome!!

Update - KVPNC does eventually disconnect, and I can close the icon out of the task bar.  It just takes a long time.  More than 30 minutes on the slower PC's, and almost 15 minutes on the Latitude 620 and Optiplex 520.

Ok a few other things that might be helpful.  I'm fully patched on 8.10 (Ubuntu) as of 11-26-08 and the problems persists.

If the KVPNC PPTP connection is dropped anywhere other than my pc (cable modem unplugged, connection dropped on vpn server, etc) KVPNC will turn from a green check to a red x like it is supposed to, and I can quit the icon out of the system tray.

Also, if I right click disconnect, the connection is apparently disconnected, but the icon stays green and I cannot remove it from the tray.

Anyway, just thought I would keep this thread updated, because I've seen posts in other forums about it, so I don't think it's a unique case.  I didn't bookmark the links but you can just Google them easy enough if interested.

I noticed a new PPTP update in automatic updates and was hopeful, but... no go.  The password saving thing was fixed, but the other things I mentioned were not.

Here's where I'm at.  I don't even understand the VPN configuration tool in Network Manager.  There just seem to be some critical things missing.

1.  We need the ability to enter an interface (like ppp0) when adding a route.  KVPNC allows you to enter IP, Netmask, Gateway OR Interface.  As far as I can tell the route gateway box is forcing you to enter an IP address.  The gateway for most PPTP connections is going to be the address of ppp0 (or whatever the PPTP interface is).  Since most companies have their VPN appliances set up for DHCP, this does not seem to make much sense, because the gateway could actually change if the appliance issues you a different address for ppp0.  If I match up the route gateway box with the IP of ppp0 through trial and error, the traffic is routed correctly, BUT my manually entered search domain and DNS servers no longer seem to be recognised.

2.  We need a box that simply says "Use or don't use the default route" on the routes box.  There is that box that says "ignore automatically obtained routes" but it does not seem to work.

KVPNC still works, so for now I'm sticking to that even though Ubuntu 8.10 broke KVPNC so that you have to reboot to clear off a PPTP connection.  Not a huge issue however, since when I work from home I just leave it connected all day anyway.  It would really be nice to get the Network Manager PPTP connection working like it does in KVPNC though.

Ok I finally figured this out through trial and error.

What I'm trying to do is establish a PPTP connection to work, send all VPN traffic through the VPN interface (ppp0 in this case), and everything else out the ISP interface (eth0 in this case).  I also want to use the DNS servers at work for VPN IP's, and use a search domain so I don't have to type the entire FQDN or IP every time.

Go to the "Configure VPN" screen (left click Network Manager, VPN Connections, Configure VPN.  Click Add.  

Under the VPN tab, type in a connection name, gateway, username, password, and domain (if your company uses NT domain auth for VPN).  Our VPN appliance requires MPPE, so I click Advanced, and put a check next to MPPE, then OK to close the advanced screen.

Next click the IPV4 settings, select "Automatic, VPN Addresses only" in the "Method" box.  Type in a DNS Server and Search domain (this will be a DNS server from work, and the name of the LAN domain at work).

Click "Routes" on the IPV4 settings tab.  Click Add.  Add a host name or network, and netmask (192.168.1.0 / 24 will add a route to the entire network.  If you have several subnets plug in a route to each network).  Leave gateway (will set itself to 0.0.0.0) and metric blank.  Leave "Ignore automatically obtained routes" unchecked.

Next I connect, and the VPN traffic all goes out ppp0 (although if you run a traceroute to anything on the lan it looks weird.  You see the first hop, a few *'s then the last hop, nothing else), and everything else goes out eth0 (our VPN appliance at work will not function as an Internet gateway, so the fact that I am able to browse web pages is proof that my non VPN traffic is being routed correctly).  My work DNS is working, as is the search domain.  

I'll say this, the pptp-manager would still benefit from the ability to specify an interface as a VPN route gateway, and putting in a box that clearly says "Use or don't use the default route".  "Ignore automatically obtained routes" is just confusing in my opinion. 

Anyway, if this helps, yay!  If not, sorry.  Good luck!

---

### Post by T3kG33k on 2009-08-17
I am having the same issue using OpenVPN to my home.  I can authenticate but my web traffic is not being routed through the VPN interface.  The only question that I have is how do I route it through the VPN interface?

---

### Post by SiliconS on 2012-10-10
Thanks for your tips in this thread, williambertram. Much appreciated.

---


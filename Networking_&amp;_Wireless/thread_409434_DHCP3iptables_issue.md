---
title: "DHCP3/iptables issue?"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by disk11 on 2007-04-14
I've got a computer running Edgy server edition with Ubuntu-desktop installed since I'm not completely comfortable in a pure command line environment.  I have dhcp3-server installed to provide my windows box with internet.

I was using Grip to rip and encode a CD when I got a crash.  I left because the computer is a P3 850 encoding with lame using "-q 0 -V 0" and it was taking a long time.  When I came back, the screen was distorted, and no keyboard commands worked.  So I powered down and restarted, everything seemed fine, but my windows computer lost internet access.  The windows computer still was assigned an IP via DCHP and can access the server with ssh.  I tried restarting dhcp3-server, modifying dhcpd.conf, and editing iptables with firestarter to no avail.  Any ideas on what needs to be fixed?

---

### Post by rmemm on 2007-04-14
I'm not sure I'm much help -- but here's a few comments.

DHCP allocates IP address only and also provisions things like DNS server ips to intranet workstations -- and has nothing to do with internet access directly.  How do you connect with the internet -- are you routing through your Linux box that I assumed crashed?  Or though another netowrk device like a router?  What connection type is it -- Dialup/PPP or Ethernet to the internet?

I ask because I don't know what network architecture you have and what your trying to do.

Other thing I would say -- I would ping through each level of the connection to check connectivity -- then I would try to ping to my DNS servers.  The two causes of internet connectivity issues are -- a link is down to IP trafic -- and this can have a number of causes -- or your DNS servers are not accessable for some reason or the DNS IPs are miss-configured.

Otherthing I'd try -- reboot everything -- all the way from the wall to your windows box including the windows box and any components that are part of your connection including modem, gateway/router, linux box that does the dhcp, and windows systems for example.

Hope this helps.

Rob

---

### Post by disk11 on 2007-04-14
How do you connect with the internet -- are you routing through your Linux box that I assumed crashed?  Or though another netowrk device like a router?  What connection type is it -- Dialup/PPP or Ethernet to the internet?[/QUOTE]

I connect the windows box through the Linux box via Cat6/gigabit and that connects to a router.  I have cable internet.

> **rmemm said:**
> Other thing I would say -- I would ping through each level of the connection to check connectivity -- then I would try to ping to my DNS servers.  The two causes of internet connectivity issues are -- a link is down to IP trafic -- and this can have a number of causes -- or your DNS servers are not accessable for some reason or the DNS IPs are miss-configured.

Otherthing I'd try -- reboot everything -- all the way from the wall to your windows box including the windows box and any components that are part of your connection including modem, gateway/router, linux box that does the dhcp, and windows systems for example.

I'm pretty sure it is a configuration thing on the Linux box.  I am posting from the windows box which I have connected directly to the router for now.  The Linux box on its own can reach the internet, but I don't use it as my primary since it is a P3 850mhz with only 128MB of RAM at the moment.

---

### Post by rmemm on 2007-04-14
I think we need someone that's done some routing then since it sounds like your routing through your linux box.

A thing I would try is to figure out if the issue is DNS related or if it's IP related.  For example can  you ping your broadband router IP address -- for and adress on the internet from your windows box when your setup normally -- meaning in your routing config your having problems with.  For that matter -- can you browse to an internet site via ip address not by name.  If you can -- it's a DNS provisioning problem (which could be related to your DHCP setup), if not, it's an IP problem -- meaning something to do with your routing, firewall, etc. 

Other thing you might try -- don't use dhcp and hard wire the addresses just to test using static ips and dns server numbers.

Rob

---

### Post by disk11 on 2007-04-17
I have now determined it is a DNS issue.  I have already opened the DNS port in iptables but that didn't fix it.  What do I need to check for?

---

### Post by rmemm on 2007-04-17
I think you need to figure out if its a DNS access issue or a DNS ip address provisioning issue.  On your windows box are you getting the DNS IPs using DHCP or are you entering them manually?  

If your not entering them manually -- find out what they are from an upstream machine -- such as your gateway and enter them manually and see if this fixes the problem.  If it does -- then it's a provisoning issue and has something to do with your DHCP server setup -- meaning it's not providing the windows system with the correct IPs for the DNS servers.  Note also -- there should be 2 or more IPs for DNS because you need to have at least 1 backup.

The other possibility is routing.  As a hint -- DNS requires both TCP and UDP packet routing.  Make certain your firewall is routing both.

As an aside -- I've been entering static IPs for DNS into all of my computers at home -- mainly because I could never get reliable proxying of the DNS servers through the 2 layers gateways I run.  I say proxying because it seems like all of the cheap home gateways I've used proxy the DNS servers -- I'm not sure why that is.  It's never worked for me -- though I think it should -- and I think what your doing should work also in general.

Rob

---

### Post by disk11 on 2007-04-17
It's a provisioning issue, I was able to reach ubuntuforums.org using the ip address.  So I need to edit the config file for DHCP3 and make sure the DNS line reads my ISP's DNS servers?

---

### Post by rmemm on 2007-04-17
Yes sounds like it.  I don't think I can help you with that as I've never configured the server side of DHCP.  There must be some settings that tell the server what information to send in the DHCP configuration setup to down stream workstations.  From what I've heard I think you can send various things -- but I don't know more than that -- except DNS addresses should be one of these items.

You should probably check to see that your server with the DHCP server works regarding DNS itself as well -- or if it two can't find the DNS servers.  Another option if you can't get the DHCP stuff working is to install a DNS proxy on the server you have -- as I said before this is what most cheap home internet gateways do.

Rob

---


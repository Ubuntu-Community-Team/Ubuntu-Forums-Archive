---
title: "Ubuntu server as router, open ports for clients connected"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by akuzura on 2014-05-28
Hello.
To start things off, about a year ago I bought a cheap computer with two ethernet ports. This computer was supposed to act as an openVPN server for my apartment. The idea was that the server would connect to VPN, and every device that connected afterwards would have the VPN IP without any additional configuration. In addition the server would act like a media server, having all videos/music/movies on that would be accessed by the other devices.

The layout looks like this:
Internet in -> Ubuntu server -> Asus Dark knight router (DD-WRT) -> all other devices

My problem is ports on computers connected to the router seem to be closed. I have done this before successfully, but recently the harddrive wth the operating system (and all the configuration) died. I reinstalled on a new harddrive, but I am having trouble with forwarding ports for the devices connected to the Asus router, and I'm fairly certain this is due to the server being configured incorrectly.

What I've done so far:
[LIST]
[*]installed SSH server
[*]using the GUI I've set eth1 to "Share with other computers"
[*]I haven't touched eth0
[*]I've tried to set net.ipv4.ip_forward=1 in sysctl.conf, but it didn't solve the problem
[*]I've tried to allow everything in iptables, but it didn't solve anything (also: i've heard this is dangerous)
[/LIST]

Just to see if port forwarding works I installed a program called SABnzbd that listens to port 8080, forwarded the port to the IP of the computer it was installed on the Asus router then tried to access it using my phone (on cellular network) entering my external IP:8080 (the one found on whatsmyip.org), but it won't open. I CAN access the server remotely using SSH, if that tells you anything.

The problem is I have very limited knowledge about how iptables or firewall works on ubuntu, but I think there's something that I should do there. I remember this being a problem the first time around as well, but I can't figure out what I did to fix it then.

Any help is appreciated
Thanks!

---

### Post by TheFu on 2014-05-28
If you aren't certain about your networking skills, perhaps having 2 routers isn't a good idea?
If I had a spare computer, I'd load pfSense and use that as the router, then get a $15-$20 cheapo GigE switch for all the other computers to connect through and make the Asus router as a bridge for wifi only (on a different subnet).

To get this working as shown, you'll need different subnets for the 2 routers.  If there isn't anything else at the same level as the Asus router, it seems overly complex for your needs.  OTOH, you will learn a bunch getting this to work.

So ... if you want more help, please post the output from these commands from every different layer of your network.
* route
* ifconfig
* sudo iptables -L

and be very clear about which devices connect to which ports and to which physical connections.  Also, the subnets used for VPN would help ... since that is the point.

Oh - and forget using the GUI for this stuff. You are well beyond that and it will just screw up your outcomes. I think it is a mistake to have a GUI on any internet-facing system.

---


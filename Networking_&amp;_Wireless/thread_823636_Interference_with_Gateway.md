---
title: "Interference with Gateway???"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Pug505GR on 2008-06-09
Now I'm not sure about this problem, but it has me stumped.

I have recently installed Kubuntu 8.04 (64 bit) on my new Presario V6000 laptop.

Without going into too much unneccesary detail, it appears that my outward WAN connection seems to be failing from this machine, but none others in the network,

What happens is that I lose connection with the outside world on the network, although internal LAN connections remain good. For example I have two consoles open, one pinging google while the other pings the router. The router one continues on ad infinitum, but the google one stalls after a (short) while. Upon rerunning 'dhclient' communication with google - in this case - resumes, but again only for a short while.

The laptop does this through both the ethernet conenction as well as the wireless, so I don't think the issue is there. This does not happen with any of my other machines either, so that rules out the router.

I think it is something within KDE network management that might be causing the problem, but can't find anything. I am not running the default KDE network manager, not any other - that I know of. All configuration that I'm aware of is through the CLI using dhclient and wpa_supplicant.

Bit of further information is that I'm running an Atheros 5700 wireless card using ndiswrapper and the 64 bit XP driver and the router is a Netgear DG 834G wireless and ADSL router. Not that I think that's the issue.

Am I missing something obvious here. I'm not sure what KDE is running in the background by default that is conflicting with my wpa_supplicant/dhclint script.

Oh, not sure if it matters, but when I installed the system it was not currently connected to a network, either through ethernet nor wireless - has this affected the configuration of the network interfaces??

Thanks

Matt

---

### Post by Pug505GR on 2008-06-09
Just to update.

As soon as I run dhclient route -n shows this
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

But after a short perios (about 30 pings) a route -n results in
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Is there any reason for my routing to be changed??? This is just running with the ETH card ATM with the wireless disabled.

Thanks

---

### Post by Pug505GR on 2008-06-10
Have made some more discoveries.

Something weird is going on with my interfaces. What appears to be happening is that eth0 is acquiring an ip address - even when the cable is unplugged :confused::confused:

So I do a dhclient and wlan0 gets an ip address and eth0 gets nothing. WAN access is fine at this stage - continuously pinging google proves this. Then when the ping stalls, runnin ifconfig shows that eth0 has acquired itself an ip address too - although it's not connected to the router.

Now I've got no idea why this could be happening. Any thoughts??

Thanks

---


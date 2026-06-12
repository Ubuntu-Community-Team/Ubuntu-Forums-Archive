---
title: "Ubuntu Video server with WIFI, act as gateway?"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by speed32219 on 2007-04-03
I have the Net Gear USB attached MA101 802.11b connected to Ubuntu Video Server for my Xbox (1), Xbmc (On a sperate local Lan).  I woiuld like to get the RSS feeds as well as weather working on the Xbmc using the Ubuntu video server as a gateway to the Windows/DSL network.  The Wireless works fine for the local as well as internet using the ubuntu 6.10 server to access.  

What I would like to do if I can is access the local as well as the internet from the Xbox(1) using Xbmc accross the 10/100 localized LAN (Only Xbox and Ubuntu server in HT room) for the RSS feeds and weather.

Can it be done or will the Net Gear MA101 USB wireless device only support one hardware machine/IP.  I was wondering if I could set the server to act as a wireless gateway for the Xbmc front end server or any other 10/100 ethernet attached devices in the future.

Current Wireless:

Ubuntu 6.10 Video Serv--------->USB MA101--------(100')-------->Dlink DI-524 DSL GW

Trying to achieve:
 
Xbox_Xbmc---10/100 Lan---->Ubuntu 6.10 Video Serv----->USB MA101----------(100')---------->Dlink DI-524 DSL GW.

---

### Post by spd106 on 2007-04-03
This looks like a job for [internet connection sharing]("https://help.ubuntu.com/community/InternetConnectionSharing"). 

You will probably find that installing firestarter is the simplest option, though if you have no X then you will probably have to go the hand configuring ip tables/dnsmasq route.

---

### Post by speed32219 on 2007-04-03
> **spd106 said:**
> This looks like a job for [internet connection sharing]("https://help.ubuntu.com/community/InternetConnectionSharing"). 

You will probably find that installing firestarter is the simplest option, though if you have no X then you will probably have to go the hand configuring ip tables/dnsmasq route.

Thank you, you put me in the right direction.  I've read that article you posted, and just want to run something by you.  The DL-524 DSL GW is config. for DHCP (Except for the Xbox which is set for a static 192.168.0.120 IP).  All devices on the network are already within the 192.168.0.xxx space. Since the Ubuntu server has a eth0 and a Wlan0 (USB wireless), I should be able to just configure the IP and GW tables as follows? 

$sudo iptables -A FORWARD -i eth0 -o Wlan0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT (Not sure on that port though)
$sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
$sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"$sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

Configure routing/GW:

$sudo route add default gw <192.168.0.254>      NOTE: (DI_524 DSL GW IP)

Finally edit /etc/resolv.conf  and add:
<nameserver> <ipaddress> <192.168.0.254> <192.168.0.254>  (I think this is default DI-524  DNS name server and GW IP)

Does this look feasible or am I off the beaten path?

Thank you for your assistance, I'm new to this stuff.  Now I need to figure out how to view the current IP tables, I did have firestarter installed but it was messing with my Xbox/Xbmc server trying to get to the SMB videoshares and I didn't take the time to resolve the issues within the IPtables.

---

### Post by spd106 on 2007-04-04
Yes, you're almost there. The only thing to change it to put the private network on a different subnet i.e. if your wifi is on 192.168.0.0/24 then put the private network on 192.168.1.0/24. Effectively treating the wifi network as you do the internet.

There is very useful [howto]("http://ubuntuforums.org/showthread.php?t=111972") that goes into more depth and provides a script that you can adapt to automate the procedure, then you can make it persistent.

The command to view the current iptables is ```
sudo iptable -L
```

---


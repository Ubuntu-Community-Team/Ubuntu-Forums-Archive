---
title: "dansguardian trouble"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by ananaboogie on 2007-07-14
I am having a problem with Dansguardian not working after installing firestarter. Here is a little background on what I am trying to do. I am setting up a computer lab for a non-profit private school. The network looks like this: Internet>Router>Ubuntu CE 7.04 Server>Switch>5 XP Workstations. I would like the Linux server to filter the internet for the other workstations. Dansguardian works on initial installation just fine and continues to work after applying all the OS updates. When I install Firestarter to configure Internet Connection Sharing, Dansguardian breaks for some reason and I lose the content filtering. I have read the info on the Dansguardian website and have tried some different settings with TinyProxy and Dansguardian, but nothing seems to work. The 5 workstations are setup on static ip addresses and work just fine. Firestarter also works and filters all the connections like it is supposed to. My guess is that when Firestarter is installed it writes a new table for iptables and it looses the settings for tinyproxy and dansguardian. I have 5 years of Linux experience and am not afraid of the command line, so any solution is welcome. Thank You.

---

### Post by ananaboogie on 2007-07-14
With more experimenting I have found that installing firestarter is not the problem. Here is what I have done.

1) Tested the content filtering with default installation. Filtering works.
2) Changed eth0 ip address from dhcp to static ip. Filtering works.
3) Installed firestarter. Filtering works.
4) Setup firestarter to work without Internet Connection Sharing. Filtering works.
5) Changed firestarter settings to enable Internet Connection Sharing. Filtering doesn't work.

It would seem that Internet Connection Sharing instead of Firestarter is causing the problem. Eth1 is going out to the internet and Eth0 is going out the switch and serving my lan. Any suggestions?

---

### Post by s4s on 2008-04-09
my set up is:
eth0 going to the internet
eth1 going to the local lan

the following are from /etc/firestarter/configuration:
$IPT refers to iptables
$IF refers to eth0
$INIF refers to eth1 

So I use the following in /etc/firestarter/user-pre:
 
#redirect http requests to dansguardian
$IPT -t nat -A PREROUTING -i $INIF -p tcp --dport 80 -j REDIRECT --to-port 8080

with the above iptables command I got it working. 
hope this helps.

---


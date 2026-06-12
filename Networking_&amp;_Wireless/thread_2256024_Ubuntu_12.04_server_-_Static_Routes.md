---
title: "Ubuntu 12.04 server - Static Routes"
date: 2014-12-09
forum: Networking &amp; Wireless
---

### Post by CheeseAndPickle on 2014-12-09
Hi,

Battling to get static routes available on startup. I just get a 60 second time out and a message that it will not startup with a full config. My /etc/networking/interfaces is as follows:

	# This file describes the network interfaces available on your system					
	# and how to activate them. For more information, see interfaces(5).					
						
	# The loopback network interface					
	auto lo					
	iface lo inet loopback					
						
	# The primary network interface					
						
	auto eth0					
	iface eth0 inet static					
						
		address 	192.168.50.235			
		netmask		255.255.252.0		
		broadcast 	192.168.51.255			
		network 	192.168.49.0			
		gateway		192.168.50.250		
																
post-up	route add -net	194.0.0.0	netmask	255.0.0.0	gw	192.168.50.250
post-up	route add -net	80.0.0.0	netmask	255.0.0.0	gw	192.168.50.250
post-up	route add -net	8.8.8.8	netmask	255.255.255.255	gw	192.168.50.250
post-up	route add -net	192.168.85.0	netmask	255.255.255.0	gw	192.168.50.250
post-up	route add -net	192.168.0.0	netmask	255.255.255.0	gw	192.168.50.254
post-up	route add -net	192.168.1.0	netmask	255.255.255.0	gw	192.168.50.254
post-up	route add -net	192.168.2.0	netmask	255.255.255.0	gw	192.168.50.254
post-up	route add -net	192.168.85.0	netmask	255.255.255.0	gw	192.168.50.250
post-up	route add -net	192.168.90.0	netmask	255.255.254.0	gw	192.168.50.250
post-up	route add -net	192.168.95.0	netmask	255.255.255.0	gw	192.168.50.254
post-up	route add -net	192.168.111.0	netmask	255.255.255.0	gw	192.168.50.254												
post-up	route add -net	172.0.0.1 	netmask 255.255.255.255	gw	192.168.50.4 
post-up	route add -net	172.0.2.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.4.0	netmask	255.255.254.0	gw	192.168.50.250
post-up	route add -net	172.0.6.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.6.157	netmask	255.255.255.255	gw	192.168.50.250
post-up	route add -net	172.0.8.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.10.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.12.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.14.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.16.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.18.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.20.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.22.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.24.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.26.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.28.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.30.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.32.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.34.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.36.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.38.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.40.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.42.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.44.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.46.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.48.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.50.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.52.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.54.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.56.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.58.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.60.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.62.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.64.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.66.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.68.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.70.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.72.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.76.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.78.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.80.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.82.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.84.0	netmask	255.255.254.0	gw	192.168.50.250
post-up	route add -net	172.0.86.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.88.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.90.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.92.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.94.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.104.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.106.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.108.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.112.0	netmask	255.255.248.0	gw	192.168.50.4
post-up	route add -net	172.0.114.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.116.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.120.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.122.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.224.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.228.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.0.230.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.7.120.0	netmask	255.255.255.0	gw	192.168.50.250
post-up	route add -net	172.7.121.0	netmask	255.255.255.0	gw	192.168.50.254
post-up	route add -net	172.7.122.0	netmask	255.255.255.0	gw	192.168.50.250
post-up	route add -net	172.16.6.1	netmask	255.255.255.255	gw	192.168.50.4									
post-up	route add -net	172.200.2.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.4.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.6.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.8.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.200.8.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.10.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.200.10.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.12.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.14.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.16.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.18.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.20.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.22.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.24.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.26.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.28.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.30.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.32.0	netmask	255.255.255.0	gw	192.168.50.4
post-up	route add -net	172.200.34.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.36.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.40.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.42.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.44.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.46.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.48.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.50.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.52.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.54.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.56.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.58.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.60.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.62.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.64.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.66.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.68.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.70.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.72.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.74.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.76.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.78.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.80.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.82.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.84.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.86.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.88.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.90.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.92.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.94.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.104.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.108.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.114.0	netmask	255.255.254.0	gw	192.168.50.4
post-up	route add -net	172.200.116.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.118.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.120.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.122.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.224.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.228.1	netmask	255.255.255.255	gw	192.168.50.4
post-up	route add -net	172.200.230.0	netmask	255.255.254.0	gw	192.168.50.4

Cheers,

---


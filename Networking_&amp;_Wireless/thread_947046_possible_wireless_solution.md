---
title: "possible wireless solution"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by strider22 on 2008-10-13
I was without wireless all day and got it going again.
I am posting in case someone else can test and verify the conditions described. I'm hoping I trapped a bug, unfortunately given the time I have already spent and that testing would be affected eight other users, I can't test the conditions again.

A new user bought his own wireless router and plugged it in. The default setup for a router is to serve DHCP. The new router served new IPs to the lan and wireless. Any rebooted machine would not work. Once I tracked down the router and turned it off, the wired PCs were OK but my Ubuntu laptop would not connect. I kept getting the "waiting for network key" message. 

Neither of the two dots on the network Icon went green. Strangely, if I tried to connect to a neighbouring router, the first (bottom left) dot would go green. Of course it would not connect because that router is password protected.  

I changed network passwords, rebooted everything and tried manual connecting per several sources;
sudo iwlist scan
sudo iwconfig wlan0 essid "ID_in_quotes" (many don't say quotes)
sudo dhclient wlan0

The solution is quite simple 
sudo dhclient -r wlan0
is required.

I had wire connected to the network to search the net for answers. I unplugged. Issued the "-r" command, right-clicked the network icon in the panel on the top left. Selected enable wireless. Left-clicked and selected my network, waited and cheered.

It seems that because Ubuntu received a valid IP in a different subnet, although a broken subnet, the GUI tools did not release the old subnet. Seems like a trivial fix for the GUI tools.

I did not want to submit this as a bug in case it is not verifiable. I'm sure the developers have a high enough signal to noise ratio. 

Is anyone willing to test wireless connection failures caused by changing subnets. eg 192.168.2.100 changing to 192.168.1.100
because router 1 is configured to provide 192.168.2.* addresses and router 2 is configured to provide 192.168.1.* addresses.

Thanks.

bump

---

### Post by strider22 on 2008-10-16
bump

---


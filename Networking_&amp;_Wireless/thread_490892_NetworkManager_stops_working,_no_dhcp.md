---
title: "NetworkManager stops working, no dhcp"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by tristano on 2007-07-03
There has been an occasional problem with NetworkManager where, after working for some time, it will simply stop completing connections. This has primarily been wireless connections for me. 

Symptoms:
- Wireless APs appear as expected in "Wireless Networks" list
- nm-applet associates with APs but never receives an IP address (only one green dot in applet)
- NetworkManager fails to connect and prompts repeatedly to enter the key
- Possibly caused by suspend

To solve this problem and allow DHCP to function, simply remove the .leases files from /var/lib/dhcp3/, specifically those of the troubled interface(s). Retry the connection and all should be well again with nm-applet.

---

### Post by best.nose on 2007-07-03
You are a lifesaver! Thanks for the post.

My problem was the network manager applet would screw up a connection that had been working at startup. I could connect to the internet while the littel nm applet 'thing' was going round and round (indicationg connection was being established i guess), but as soon as the 'connected network' icon replaced it my internet connection was dead and i couldn't ping my adsl modem.

The new dhclient.eth0.leases file is empty, while the old one had this in it (after i stried to configure the modem for static ip address hoping to avoid what seemed to be a DHCP problem):

lease {
  interface "eth0";
  fixed-address 192.168.1.2;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 3600;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
  option host-name "ubuntu";
  renew 3 2007/7/4 01:00:53;
  rebind 3 2007/7/4 01:00:53;
  expire 3 2007/7/4 01:00:53;
}
lease {
  interface "eth0";
  fixed-address 192.168.1.2;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 3600;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
  option host-name "ubuntu";
  renew 3 2007/7/4 01:01:20;
  rebind 3 2007/7/4 01:01:20;
  expire 3 2007/7/4 01:01:20;
}

Anyway, I thought this may help somebody else.

---


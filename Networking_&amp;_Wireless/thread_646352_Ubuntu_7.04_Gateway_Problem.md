---
title: "Ubuntu 7.04 Gateway Problem"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by LastAttacker on 2007-12-21
Hi there!

I have installed and setup Ubuntu 7.04 (Server Edition) as my gateway router for the home network.
I have iBurst as my internet connection on ib0, and my network on eth1.
Using IpTables, I can connect to the internet on the server itself and through a windows PC over the network.
However, certain sites won't load. For instance, if I try to load the Documentation page on the Ubuntu site (seems to be HTTPS), Firefox just keeps on saying "Connecting to site" and times out. If I load that page with a text based browser on the server it loads the page. It seems as though it has some trouble with HTTPS connections. Also on my windows PC, if I try to update my AVG Antivirus, it goes and shows a selection of what I want to update but on the update process itself, it doesn't download at all.
Could this be an Ubuntu problem or did I miss something?
I basically have my firewall on ACCEPT for everything and it just has masquerading on.
I tried this with Shorewall firewall as well with the exact same outcome. I just wonder if it is maybe a routing issue? All I have on my routing table is my home network: 192.168.0.0.

I followed this URL for ICS: [https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing")

Currently I have my internet on my windows PC.
Any help will be greatly appreciated.
Thanks!
God Bless!

---

### Post by anubhavrocks on 2007-12-21
I am assuming that your internal Network Address is 192.168.1.0.

Settings on the Server:
sudo ifconfig eth1 192.168.1.1 up
sudo iptables -t nat -A POSTROUTING -o ib0 -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

Settings on the client
sudo ifconfig eth0 192.168.1.2 up
sudo route add default gw 192.168.1.1

Add nameserver to /etc/resolv.conf
Try pinging your gateway to see if everything works.
 
Note:
These are very basic settings,if this works you might want to add other rules to make your network secure and automate the whole thing.

---

### Post by LastAttacker on 2007-12-21
Hi and thanks for the reply.
I have all those things in place.
Like I said, the internet works, but certain connections are blocked or something.
I can connect with a Linux/Windows PC to my Linux Gateway and from there surf the web, but as soon as I try to update my Antivirus or load a page via HTTPS it times out.
I think it has to do with how the packets are forwarded. I just don't know where to look or how to fix.

I tried to update to Ubuntu 7.10 but the updater said that it didn't find an update available.

As soon as the internet gateway works properly, I will add more rules to make it more secure. Know any pages that can assist me with good IpTables rules?

---

### Post by LastAttacker on 2007-12-21
Man nothing so far. Still no developments on my side. I wonder what it could be. I know that it can work because I once had OpenSuSE on but I had an iBurst modem that could connect through a network cable, now I have a USB modem and had to move to something like Ubuntu since SuSE didn't work so well with the iBurst USB modem.

---

### Post by LastAttacker on 2007-12-23
I came on this web page: [https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537]("https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537")
This explains about an IP forwarding bug in Ubuntu. I followed their instructions before, the HTTP pages loads without a problem but HTTPS pages won't.
I commented out those lines in sysctl.conf and no ip forwarding took place, just like with the HTTPS pages.
Does the 7.10 Ubuntu Server have this issue? Is there a way for me to upgrade to the latest Ubuntu server from 7.04?

Thanks

---


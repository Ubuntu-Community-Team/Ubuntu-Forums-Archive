---
title: "VPN Connection Sharing"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by morashti on 2008-08-29
OK, here it goes:

First of all, I'm a totally new Linux user.

Second - I've recently installed Ubuntu (and Kubuntu) and I'd like to share my existing VPN connection to my ISP with another computer running XP (sadly).

I've tried Firestarter to no avail, and also various manual configurations. Unfortunately, whenever I use network manager to manually assign an IP address to my internal network adapter (eth1), somehow I can't use my VPN connection on my eth0 (the Network Manager shows only WIRED NETWORK instead of the usual option of VPN CONNECTIONS).

Even when the XP machine shows the connection as fully functional, no internet connection is active.

Also, my roommate won't join in on a router/switch, so I need to continue using the crossover cable.

Please, could someone help me figure this one out, as I couldn't find a post with a solution to my problem?

Thanks.

---

### Post by SpaceTeddy on 2008-08-31
if i remember this correctly, network manager cannot handle more than one network device at the time. This is mind, you'll need to fingure your internal network card manually via the /etc/network/interfaces (google "ubuntu /etc/network/interfaces static ip example") and setup the internal network card manually in this file. This will prevent network manager to pick the nic up at all and you only configure the vpn dial-in via nm. 
Now, once that is done check if you have internet on the computer. If you have that, check if you can ping the other machine. If this works too - all you need to do now are the following steps:

1.) configure the client
it already has a proper ip (as you can ping it) - set the default gateway of the client to the ip of your ubuntu box. Also, form the command shell in ubuntu run > cat /etc/resolv.conf and put the nameservers from there in the dns fields from your client
2.) make sure you have NO FIREWALL software at all running on your computer (you can do so later, but for simplicity, i recommend not having one when setting this up) - in the command line, run this command to enable your ubuntu box to forward ip-requests:
> sudo sysctl -w net.ipv4.ip_forward=1
3.) masquerade the traffic. For this you will need to figure out what device the internet traffic is taking. I think it should be something like ppp0 - but check this via > route -n
find the line that starts with 0.0.0.0 and check which device is displayed at the back . remember it. Now run this command (change the device to the approriate one - i'll use ppp0 here) to enable ip-masquerading
> sudo iptables -A POSTROUTING --table nat -o ppp0 -j MASQUERADE

Now it should work. Btw, all these changes where temporary - if this works for you i can tell you how to make them permanent... 

hope it helps :)

---

### Post by morashti on 2008-09-04
Thanks! I'll give it a try and let you know how it went. :)

---


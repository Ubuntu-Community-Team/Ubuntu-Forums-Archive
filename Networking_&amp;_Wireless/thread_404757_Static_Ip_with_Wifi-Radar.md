---
title: "Static Ip with Wifi-Radar"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by grogger13 on 2007-04-08
I was trying to set up a samba share(ubuntu really needs to make this more like windows does) and the tutorial said i needed a static IP for it to work, so i went into wifi-radar becuase thats what i use to connect with my router, but when i looked at the menu i wasn't sure what I needed.

I use a linksys wrt54g
Ip:192.168.1.109
Gateway:192.168.1.1
Subnet mask: 255.255.255.0

With just those values put in i cold connect to my router site and change settings, but i couldn't use the internet.  

There is a field labeled Domain and it had by default domain.com so i left it because i didn't know what it was.  It didn't work so i changed it to nothing and it still didn't work.  

Im not sure how to set up a static ip address with wifi.  I have to fill out the following fields in wifi-radar.
IP, NetMask, Gateway, Doman, DNS 1, DNS 2(both fields right now read 0.0.0.0)

---

### Post by Roland of Gilead on 2007-04-08
You can obtain all the information you need from the Linksys router config webpages.

First, pick an IP address outside the DHCP range of the router.  For example, if the router is set to start assigning addresses beginning with 192.168.1.100, then pick an address where the final number is less than 100.  That way, the router doesn't attempt to assign your static IP address to any other device on the network.

Second, the only other information you need is DNS, and you have two options here.  DNS is why you can't access the internet...it's what allows you to type in "ubuntuforums.org" instead of  "82.211.81.186" when you want to browse a site.  The simple option is to plug the router's IP address (192.168.1.1) into DNS1 and leave DNS2 blank.  Hopefully, the router will forward DNS requests to its configured servers.  The other option is to look at the router's DNS config page and copy the IP addresses of the DNS servers you see there.  This tells your machine to send all DNS requests directly to one of these servers...which is fine, as long as your ISP doesn't change the addresses of its DNS servers.  If it does, you'll have to manually change your config settings to match.

---


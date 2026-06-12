---
title: "Network problem"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by lovefreesoftware on 2008-11-07
I have a Realtek 8187B wireless card. Ubuntu 8.10

I downloaded the new wireless linux drivers and it seems to work fine.

I can connect to the wireless router and it assigns an IP address. 

However, I can only ping the wireless router for the first few seconds of the connection. Then it times out. However, the connection stays live, doesn't drop out.  

I cannot ping anything beyond the router, even in the first few seconds no matter whether I do it by DN or ip address.

I have automatic DHCP set. I'm not sure what the problem is. :)

It works fine with windows.

---

### Post by stanley drew on 2008-11-07
network-manager is giving a lot of people problems right now. try wicd instead, [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php). other than that i think we have to wait for a network-manager fix.

---

### Post by lovefreesoftware on 2008-11-07
I tried this and had exactly the same problem.

But I found out I could acutally ping beyond the router by ip address. So it seems that I'm just being disconnected very quickly. I don't know why.

I got drivers for realtek 8178b from here : [http://linuxwireless.org/](http://linuxwireless.org/)

I have the one that shows lsusb as 0dba:8189.

I dunno if the driver is the problem. Any ideas how I can tell?

---

### Post by stanley drew on 2008-11-14
I'm no expert with this stuff but I kind of doubt that the driver is the problem. A lot of people are experiencing this problem or similar inconsistency issues with wireless in 8.10. wicd doesn't work for me either but I thought it was worth a shot.

Are you trying to connect to a secure network with WPA or WEP? If so try connecting to an unsecured network. That should give you a little more information about whether it's the driver.

---

### Post by GepettoBR on 2008-11-14
I have other problems with my wireless connections, but I can ping the router, my LAN devices and web hosts, both by domain name and by IP, whenever my connection is alive.

---


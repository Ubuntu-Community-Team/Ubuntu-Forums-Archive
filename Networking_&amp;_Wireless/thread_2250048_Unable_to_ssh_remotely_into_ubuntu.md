---
title: "Unable to ssh remotely into ubuntu"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by jeremyyeo on 2014-10-26
Just installed ubuntu and open-ssh server. I am able to ssh into my ubuntu installation locally but not remotely. Meaning when I ssh into my ubuntu installation using its local ip using the router (DHCP) provided local ip 192.168.xxx.xxx, I can login just fine. When I login remotely using ssh into the public ip using [www.ipchicken.com]("http://www.ipchicken.com") or [www.whatismyip.com]("http://www.whatismyip.com"), I get a connection refused error using my mac connected to the same router as the ubuntu device is and a Connection Failed! Failed getting banner error using a ssh client on my iphone connected to mobile data. openssh is configured with port 2222 and the Asus AC-86U router configured to forward port 2222 to the local ip of the ubuntu installationat 192.168.xxx.xxx. 

Anyone know whats happening?

---

### Post by weatherman2 on 2014-10-26
You may have two different problems.

First, your router may not do "loopback" of your external IP while you are on your Mac on the local network.  I answered a similar question about that here:

[http://ubuntuforums.org/showthread.php?t=2249821&p=13151209#post13151209](http://ubuntuforums.org/showthread.php?t=2249821&p=13151209#post13151209)

But that person could connect from an external network - and it sounds like you can't (with your iPhone and mobile data).  That suggests the port is still being blocked.  Did you check to see if port 2222 is open?   Try a website like [www.canyouseeme.org](www.canyouseeme.org) .  If you have a modem with a firewall, it needs to forward the port too through to the router.

If you haven't already, fix the IP of your Ubuntu machine (static, basically), but you can use your Asus router to make a DHCP reservation for the Ubuntu machine so it always gets the same IP, so the forwarding will always go to the right IP.

---

### Post by jeremyyeo on 2014-10-27
Hey weatherman2, thanks for your reply. With your reply I did a port check at [www.canyouseeme.org](www.canyouseeme.org) and noticed that the port was not open despite being routed in my router. Then I figured that it was because my Asus router was connected to the main modem router which shares the internet to the Asus router which was blocking that port. So I forwarded the port on both routers and that solved it. Thanks!.

---


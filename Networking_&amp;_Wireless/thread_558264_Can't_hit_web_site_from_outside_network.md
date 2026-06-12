---
title: "Can't hit web site from outside network"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by hudpuck on 2007-09-23
I am new to Ubuntu and linux for that matter, and am setting up a web site to run from home on an Ubuntu server.  I have everything all configured and it runs great from inside the router.  If I try to hit it from outside the router, it gives the following error:

(101) Network is unreachable

I have done all the port forwarding on the router that I can see to allow port 80 through.  I called my ISP and they said that they don't block port 80.  I registered my domain name and set it to the static IP address my ISP gave me, and when I use the domain name inside the firewall, it works just fine (as well as the straight IP).

I am at a loss as to how to solve this.  How do I know if it is the router that is causing grief or some little thing I don't have set correctly in Ubuntu.  It is wierd that I can hit it fine from inside the router from my windows box with the registered domain name or IP.  I have checked the Apache error log and nothing is entered there when I try to hit it from outside the router, so I suspect it isn't even making it to the Ubuntu server.

Anyway, any help would be useful.  Maybe somebody could suggest a better router...

Some info about the system:
Ubuntu version: ubuntu 7.04 server
Router: Linksys BEFSR41 ver. 4

---

### Post by hudpuck on 2007-09-23
This is wierd...I turned on logging for the router, and it logs all the outgoing requests.  But when I try to hit the web site from outside the router, no entry is placed in the incoming requests log.  It is almost as if the router is not getting any requests at all.  I have a static IP address for the router from my ISP, but maybe it some alias IP or something wierd like that.  I'll have to check into this more.  Any ideas would be great.

---

### Post by hudpuck on 2007-09-23
Doing more research...it seems that Linksys doesn't allow port forwarding if DHCP is running.  I also read that NAT had to be turned of to ping a router...a security feature.

Does any of this make sense?  I'll have to try them.

---

### Post by ev5unleash1 on 2007-09-23
Make sure your router is giving the internet connection info and configuring it. If not the router has no control over your internet connection. Note that most ISPs block port 80 if your using Verizon or comcast. Try other ports and maybe try out Port Forwarding.

---

### Post by str8line on 2007-09-23
There are a couple of ways to move your home server outside of the network protection of a router.  One is to open the ports via port forwarding (yes you can forward ports with DHCP on- The DHCP that is being talked about is when your ISP uses that connection type instead of a PPPoE connection) the other is putting your server in the DMZ (demilitarized zone).  Even with either of these solutions you will still need to connect the router to a Dynamic DNS service so that your internet connection will be found outside of your Local Area Network.

Hope this helps some.

---

### Post by kevdog on 2007-09-24
All incoming ports to your Linux box are blocked by default.  This means you need to open up port 80/443 in your firewall (technically you are modifying the iptables).  If you dont know how to do this by hand (Im sure you could find some good tutorials on the web), you need to install either Guarddog or Firestarter which provides a GUI that you can use to modify the firewall and allow all outside network traffic through 80/443 or whatever ports you want.

---


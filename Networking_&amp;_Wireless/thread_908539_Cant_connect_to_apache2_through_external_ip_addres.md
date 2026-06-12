---
title: "Cant connect to apache2 through external ip address"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by bobman11345 on 2008-09-02
Im running ubuntu 8.04 server and i can connect to apache2 and my website though my LAN, but when i try to connect to it outside of my lan using my external ip address, i can't connect to it.

my dd-wrt router is forwarding port 80 to my server.

---

### Post by pytheas22 on 2008-09-02
Double-check that the port is really being forwarded by the router.  You may also want to install ssh or vnc to see if you can connect to them externally as well, or put your Ubuntu computer directly on the Internet to see if it works that way.  I've had routers that say they're forwarding the ports, but in reality they're not, which causes a lot of frustration until you realize that it's just the router being stupid.

By default, the iptables rules and Apache configuration on Ubuntu should allow external traffic, so unless you modified something, there's no reason on Ubuntu's end that it shouldn't work.

---

### Post by bobman11345 on 2008-09-02
how would i check if the port is actually being forwarded?

---

### Post by pytheas22 on 2008-09-02
> how would i check if the port is actually being forwarded?

Double-check your router settings, first.  If you're sure that they look correct, then I'd install an ssh server ('sudo apt-get install ssh') and see if you can connect to that from beyond your LAN (you need to enable forwarding on your router through port 22 for ssh)...if you can't connect through ssh either, then you know that the problem is most likely with your router.  If you can connect to ssh but not http, then we can look more closely at your Apache settings.

EDIT: there are also some [websites]("http://www.canyouseeme.org/") that will tell you which ports appear to be open on your router.  See if that site thinks that port 80 is open for you.

---

### Post by bobman11345 on 2008-09-02
ok. well, its most likely my router, seeing as i sshed into the ubuntu server using the terminal command: 
ssh bobman11345@myexternalip
it said that it could not connect to myexternalip port 22: connection refused.

i checked my router, a linsys wrt54gl running DD-WRT v24 SP1 and it says that port 22, and 80 are both open.

EDIT: i can still connect to the server using my internal LAN ip address.

---

### Post by pytheas22 on 2008-09-02
Yes, it's probably the router then.  Rebooting it might help, or you could try upgrading the firmware.

If you want to be 100% certain that it's the router, then connect your Ubuntu machine directly to the Internet and see if you can access Apache or ssh that way.  But since both Apache and ssh connections get refused now, I'd bet with high confidence that the router is at fault.

Another possibility is that your ISP is blocking the connection.  A lot of ISPs like to block the http port on residential connections.  ssh is usually allowed, but I guess it's possible that it's being blocked.  You could call them and ask if they block any ports (try not to mention that you're running a web server from home, because they might threaten to charge you for it...just say you want to know why ssh won't work).

---


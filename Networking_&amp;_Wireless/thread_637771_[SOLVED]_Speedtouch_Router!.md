---
title: "[SOLVED] Speedtouch Router!"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by khurrum1990 on 2007-12-11
In Fiesty I just typed in firefox speedtouch.lan and I could configure my router, this doesn't work in Gutsy though. What should I do?

---

### Post by sisco311 on 2007-12-11
try  [http://192.168.1.254/](http://192.168.1.254/)
if works add this line to your /etc/hosts file:
> 192.168.1.254 speedtouch.lanrestart your network

---

### Post by markp1989 on 2007-12-11
> **sisco311 said:**
> try  [http://192.168.1.254/](http://192.168.1.254/)
if works add this line to your /etc/hosts file:
restart your network

my spped touch is [http://10.0.0.138](http://10.0.0.138) so try that if the one he suggested doesn't work

---

### Post by khurrum1990 on 2007-12-11
Hi, thanks for ur help. Here is what happenned. I restarted in live cd just to check whether it works there. First time I entered speedtouch.lan in firefox, it worked. Then I configured pppoe with the sudo pppoeconf command and after that it never worked again. WHat could have gone wrong?

---

### Post by Austin_KW on 2007-12-12
If you have a router, what are you running ppp on the PC. This will tunnel thru the router and you will not use the router as your dns server. You will use the ISP dns which does not know speedytouch.lan.

Configure pppoe on the router and then use the router to share this ppp connection to all your PCs and devices.

---

### Post by khurrum1990 on 2007-12-13
> **Austin_KW said:**
> If you have a router, what are you running ppp on the PC. This will tunnel thru the router and you will not use the router as your dns server. You will use the ISP dns which does not know speedytouch.lan.

Configure pppoe on the router and then use the router to share this ppp connection to all your PCs and devices.
can u explain how please? I set up the connection using the command:
sudo pppoeconf

---

### Post by khurrum1990 on 2007-12-13
I fixed it, all I need to type in is sudo dhclient eth0. That gives me the correct address and Ubuntu starts talking with the router.

---

### Post by Austin_KW on 2007-12-13
> **khurrum1990 said:**
> I fixed it, all I need to type in is sudo dhclient eth0. That gives me the correct address and Ubuntu starts talking with the router.

runing the dhclient command will get a new address, default route to the internet and set an new dns address (usually the router). These may override the settings from the ppp interface.

You sill have not said why you are configuring ppp on the ubuntu box. Usually if you use a router you configure ppp on the WAN (internet) side of the router and then the router NAT shares this connection with all the PCs on the LAN (local) side of the router.

---

### Post by khurrum1990 on 2007-12-14
I have 2 computers connected to this router. When I installed Fiesty or anyother distro in fiesty I setup a pppoe connection for Ubuntu which was my first time with a debian distro and using Windows previously I thought this would be it. When I ever closed my dsl connection in fiesty and typed speedtouch.lan in firefox it would take me to my router page.

The problem was after installing Gutsy I again made a pppoe connection but I could no longer visit speedtouch.lan whether I was using pppoe or not so thats why I needed this command. The reason I was using pppoe was cause remember in windows u use the pppoe protocol to connect to broadband, I thought it worked the same way with Linux.

---


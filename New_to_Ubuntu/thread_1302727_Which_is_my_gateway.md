---
title: "Which is my gateway"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-10-27
I have a network set up like this...

ISP --> firewall (10.10.10.1)  --> server01 (10.10.10.2)


which one is the gateway?

---

### Post by CharlesA on 2009-10-27
Is the firewall asking as a router as well?

---

### Post by wlraider70 on 2009-10-27
no sorry i forgot to mention that both are connected to the switch. 

ISP --> firewall (10.10.10.1) -->  switch (no ip or configurations) --> server01 (10.10.10.2)

---

### Post by martrn on 2009-10-27
ISP-----------[ ********]--------->?????????
                           --------->?????????
                           --------->?????????
                           --------->?????????
                           --------->?????????
                           --------->?????????


******  ==  the gateway (usually a router with two network cards in it and a min-cpu albiet a small one or a computer with two network cards in it, regardless of how powerfull.

You gateway (router) is connected and plugged straight into you isp.  Follow the line in from your isp.


????????? == computers connected to your network.

---

### Post by CharlesA on 2009-10-27
If the firewall isn't doing any NAT or routing, you won't have internet access. 10.x.x.x is a private IP and isn't allowed onto the internet.

The answer is that you don't have a gateway, since something is routing the packets outside of your network.

You'd need it setup like this:

ISP == Router == Firewall == Switch == Server

---

### Post by wlraider70 on 2009-10-27
ok, I guess the gateway must be doing DHCP.

and the firewall is the gateway.

---


---
title: "Using Ubuntu Problems"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by yuddie on 2009-09-30
i Recently switched from windows to ubuntu 9.04 the reason is that i want to use the OS for my commercial cafe. i got both the desktop edition and the server edition. now my problem is :
i cant seem to master using two network cards on the same system to bring in and send out network connection to my switch.
configuring one of them to use the WAn and the other to use the Lan. 
please i would really need help on this. 
thanks in anticipation.

---

### Post by tomBorgia on 2009-09-30
What are you using to bridge the connections - are you trying to set up Squid to act as a proxy server?

---

### Post by Peter09 on 2009-09-30
Typing
```
route
```
into a terminal will give you some idea of what the system thinks the setup of the machine is. Post the output here for help.

---

### Post by yuddie on 2009-09-30
> **tomBorgia said:**
> What are you using to bridge the connections - are you trying to set up Squid to act as a proxy server?

i am only trying to get in internet connectin to the system from one lan card which will carry my ISP provided Ip address and then send it out on the other card carrying my local arear network IP Address to a switch for other systems to connect.

---

### Post by Peter09 on 2009-09-30
You will need to configure the internet connection as a gateway so that the machine knows where to go.

---

### Post by yuddie on 2009-09-30
> **Peter09 said:**
> You will need to configure the internet connection as a gateway so that the machine knows where to go.

Im very new to this lunux stuff but i know what i want just that i dont know how to get it. please can you be more explicit.

---

### Post by tomBorgia on 2009-09-30
It's not exactly a 10 min job mate... [this link]("http://newbiedoc.sourceforge.net/networking/homegateway.html") tells you what to do... if you were expecting a GUI and a couple of mouseclicks you'll be sadly dissapointed ;-)

---

### Post by Peter09 on 2009-09-30
You can try this command

```
route add default gw {IP-ADDRESS} {INTERFACE-NAME}
```show us the output of route

Note this assumes that you are not trying to set up a NAT router but merely to route LAN traffic to an established router on your other cards network.

---


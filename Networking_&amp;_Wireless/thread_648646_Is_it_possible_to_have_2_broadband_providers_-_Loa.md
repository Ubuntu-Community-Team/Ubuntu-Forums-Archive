---
title: "Is it possible to have 2 broadband providers - Load balancing maybe?"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2007-12-23
I was wondering if it is possible to use my Linux box as a router/switch for 2 broadband connections. I would have 3 NIC's.  One for DSL, one for Cable and one that goes to the switch on the LAN.  

Is there a way to combine the bandwidth of these two connections?

---

### Post by tuproxy on 2007-12-23
I've thought of a few possibilities of how to set this up and was wondering what anyone would suggest.  

Option 1
ISP A ->**DSL  Modem**  ->   Router->    **Linux box**  <- Router<- **Cable Modem **<- ISP B

Option 2
ISP A **->** DSL Modem ** ->  Linux box  <-** Cable modem  **<-** ISP B

Option 3
ISP A ->**DSL  Modem**  ->   Router->    **switch**  <- Router<- **Cable Modem **<- ISP B

Option 4
ISP A ->**DSL  Modem**  ->   Router->    **router**  <- Router<- **Cable Modem **<- ISP B

Ideally I would like to try option 2 as it reduces the need of two routers.  

If you don't know how to do this, can you point me in the right direction?  Any suggestions as to what I should look up?

---

### Post by az on 2007-12-23
It's called ethernet bonding and it requires that the source of both incoming ethernet cards stripe the data.  I don't think there is a way to do with the net connections from both ADSl and Cable.

When you have a switch that can do it, this is how you set up the connection:
[http://glasnost.beeznest.org/articles/179](http://glasnost.beeznest.org/articles/179)

---

### Post by tuproxy on 2007-12-23
I have a feeling that it can be done. I've been reading about multi-homing that has been done for the last 10 years.  There has to be some process available now.

---

### Post by burbankmarc on 2007-12-24
Yes, it is possible to load balance between 2 different ISPs. But the only way to do it is BGP routing. There's a couple things you have to do in order for it to work though.

1) purchase an entire class C address block

2) purchase an AS number

3) convince both ISPs to share their routes with you, and with each other.

If you do not do all of those you will NOT be load balancing. I.E. have the traffic go out one pipe, and in another. you can set up a sort of round robin system that divvy's up the traffic, but if you do it that way whatever pipe the traffic goes out it MUST come back in that same pipe.

So yeah, unless you have all kinds of disposable income, this isn't a home solution.

P.S. if you choose to go BGP, and decide to use like a Cisco router, you'll need at LEAST a 3700 series, because BGP eats up a ton of memory.

---


---
title: "cable too long from adsl router to second box"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by JAPrufrock on 2007-07-04
I'm trying to get a second computer connected to my adsl router.  The problem is that it's too far away (35 meters).  I'm using a standard 24 AWG 8 conductor cable (not twisted) with RJ45 connectors.  If I set up the computer 25 meters away from the router, I can connect - but not at 35 meters.  Any easy solutions?  Thanks.

---

### Post by chippy99 on 2007-07-04
According to the spec you should be able to go 100 metres with cat5 cable. Are you sure your cable is ok ?

---

### Post by netztier on 2007-07-05
> **JAPrufrock said:**
> I'm trying to get a second computer connected to my adsl router.  The problem is that it's too far away (35 meters).  I'm using a standard 24 AWG 8 conductor cable (not twisted) with RJ45 connectors.  If I set up the computer 25 meters away from the router, I can connect - but not at 35 meters.  Any easy solutions?  Thanks.

Well (Fast)Ethernet is specified for Cat5 (or better, of course) cables and these must have twisted pairs by design. There is such a thing a s "flat" twisted pair cables to put under the carpet etc. , but pairs *must *be twisted - that's how they work. 

In fact, you're even lucky that the network runs at all with untwisted cables - I wouldn't want to see the collision and CRC error counters on these ethernet ports...

best regards

Marc

---

### Post by JAPrufrock on 2007-07-05
> **chippy99 said:**
> According to the spec you should be able to go 100 metres with cat5 cable. Are you sure your cable is ok ?

When I Googled max cable length for an adsl router, I found  some info (from wikipedia, I think) that said that total cable length shouldn't exceed 30 meters, which is the result that I seem to be getting.  I tried using standard untwisted cable because with cat5 cable the maximum distance seemed to be even less (15 - 20 mts).  Surprisingly, there seemed to be little noise with the untwisted cables (my adsl speed is at the low end- 256k/sec).

---

### Post by netztier on 2007-07-06
> **JAPrufrock said:**
> When I Googled max cable length for an adsl router, I found  some info (from wikipedia, I think) that said that total cable length shouldn't exceed 30 meters, which is the result that I seem to be getting.  I tried using standard untwisted cable because with cat5 cable the maximum distance seemed to be even less (15 - 20 mts).  Surprisingly, there seemed to be little noise with the untwisted cables (my adsl speed is at the low end- 256k/sec).

Well - cable length from the telco's wall outlet to the "outside" (or "DSL" or "WAN" interface)  router interface  definitely is limited - but this is telco/telephone stuff - here you may use Cat3 or telephony grade cabling - your plain AWG24 might do. 

But you were giving the impression that you were talking about what happens on the "inside" side of your DSL router, about the **LAN**, from the DSL Router to another PC - and that's where we're talking Ethernet, FastEthernet, Twisted pair cabling, Cat5 etc. And that's where the 100m-rule of Cat5 applies and where wire pairs in the cable *must* be twisted.

When you were googling for xDSL cabling requirements, you were barking up the wrong tree. xDSL stops where the cable from the wall outlet reaches the router. From the router to the PC, there's no xDSL anymore, here we have a LAN, Ethernet, Cat5 world.

Telephony, ISDN, xDSL etc use completely different signal and frequency spectra than Ethernet does, hence the difference in cable quality requirements.


best regards

Marc

---

### Post by JAPrufrock on 2007-07-06
> **netztier said:**
> Well - cable length from the telco's wall outlet to the "outside" (or "DSL" or "WAN" interface)  router interface  definitely is limited - but this is telco/telephone stuff - here you may use Cat3 or telephony grade cabling - your plain AWG24 might do. 

But you were giving the impression that you were talking about what happens on the "inside" side of your DSL router, about the **LAN**, from the DSL Router to another PC - and that's where we're talking Ethernet, FastEthernet, Twisted pair cabling, Cat5 etc. And that's where the 100m-rule of Cat5 applies and where wire pairs in the cable *must* be twisted.

When you were googling for xDSL cabling requirements, you were barking up the wrong tree. xDSL stops where the cable from the wall outlet reaches the router. From the router to the PC, there's no xDSL anymore, here we have a LAN, Ethernet, Cat5 world.

Telephony, ISDN, xDSL etc use completely different signal and frequency spectra than Ethernet does, hence the difference in cable quality requirements.


best regards

Marc

    Sorry about the confusion: yes, I was talking about the max length from the dsl router to another computer.  The maximum length may be 100 meters, but I haven't had much luck even at 30 meters with the cable I bought.  I will try buying some new cat5 cable.
    Regarding different cable quality requirements for different kiinds of hardware, I'm sure that's true (otherwise, why have different kinds of cables?); however, I was surprised to find out that I could get ethernet connections to work well at a distance of 20 - 25 mts with regular non-twisted 24 AWG cable.  I'm not talking theoretically, but rather empirically.

---

### Post by foxmulder881 on 2007-07-06
To clear all the confusion from several posts here...
cat5 cable is certified for up to 100 meters. That includes both patch and cross-over. Anything longer than 100 meters and you are running the risk of data loss and other problems.

---


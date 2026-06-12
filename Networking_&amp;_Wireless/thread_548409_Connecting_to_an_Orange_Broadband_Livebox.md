---
title: "Connecting to an Orange Broadband Livebox"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by MajorOwned on 2007-09-11
help!

i'm new to ubuntu, ive got a new install of ubuntu 7.04 and i can't get it to connect to the internet through the Orange Livebox router (in the UK) 

the usb wireless adaptor finds the network no problem, after i enter the wep key it logs out a few seconds after, same thing happens with a wired connection - it finds it and then disconnects a few seconds later :confused:

---

### Post by Steve1961 on 2007-09-11
log into the router from another machine - 192.168.1.1 username and password are admin.  Then go to Configuration -> Advanced -> Wireless and set the maximum pairing time to unlimited.

---

### Post by MajorOwned on 2007-09-11
excellent, thank you so much, im posting from it now

that worked for the wired connection, although the wireless still doesn't work, it finds the connection, although neither of the two little 'lights' turn green, they both stay black

---

### Post by Steve1961 on 2007-09-11
> **MajorOwned said:**
> excellent, thank you so much, im posting from it now

that worked for the wired connection, although the wireless still doesn't work, it finds the connection, although neither of the two little 'lights' turn green, they both stay black

Ah, that sounds like a driver problem with the wireless adapter.  Search these forums for the make and model of the wireless adapter - someone is bound to have got it working :)

---


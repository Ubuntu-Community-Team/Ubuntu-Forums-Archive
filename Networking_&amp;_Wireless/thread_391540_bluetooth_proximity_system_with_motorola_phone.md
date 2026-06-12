---
title: "bluetooth proximity system with motorola phone"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by mgvbstar on 2007-03-23
Hi all.  I am trying to set up a bluetooth proximity system for my laptop with my motorola v3m similar to what is described [here]("http://www.novell.com/coolsolutions/feature/18684.html").  

The problem is that I need to pair my v3m with my laptop.  The v3m only supports handsfree and dial-up networking services, so I cannot pair my phone and laptop as described in the link.  hcitool scan shows that my computer can find my phone, and when I use my phone to search for handsfree devices, it finds my computer but when I try to connect to it I get a service not available error.  Is there any command I can run from my computer to make it pair with my phone or enable handsfree so that my phone can connect to it? Thanks.

I am using edgy and my hardware is a acer laptop (aspire 5672wlmi) which has built in bluetooth.  Thanks!

---

### Post by mgvbstar on 2007-03-23
ok, so I got it to work with one problem.
if i do 
```
sudo hcitool cc [MAC ADDRESS OF PHONE]
```
followed by 
```
sudo hcitool auth [MAC ADDRESS OF PHONE]
```
Then running
```
hcitool con
```
lists the phone as connected and script in the above link works wonderfully.
However, after about 10 seconds, the connection between the computer and the phone somehow gets proken and "hcitool con" returns no connections.  Anyone know how to make the connection between the phone and computer permanent? Thanks.

---


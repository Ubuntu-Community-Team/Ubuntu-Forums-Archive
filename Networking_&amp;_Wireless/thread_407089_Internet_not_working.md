---
title: "Internet not working"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by amchl7 on 2007-04-11
Hi

I have installed Ubuntu (6.10) but unfortunately I cannot access the internet, I have a USB ethernet adaptor (SMC) attatched into the router which I assume is working fine as I can access my router and log in to change settings e.t.c.  However I am unable to visit any websites or ping any addresses.  Me being me assumed it would work straight off though this seems not to be the case, i was hoping it is something daft that I have not done, I havent used Ubuntu before and I would really like to get on the net so I can start experimenting.  Thanks in anticipation of great help :D

---

### Post by bernied on 2007-04-11
The first place I'd look is in 
System Settings - Network Settings - Routes
(the way to get there might be a little different as I use kde instead of gnome)

Have you got a default gateway IP address there?
It should be the IP address of your router.

To change it you'll need to use administrator mode, which will need your password.

Does this help?

---

### Post by PurplePenguin on 2007-04-11
I had an internet problem a few days ago.  Nothing on the web would come up (or if it did, it would take ages), pinging [www.google.com](www.google.com) wouldn't work, and my torrents were unaffected.  The solution was to add OpenDNS servers to my DNS network settings.

If you can ping 64.233.187.99 (which is Google) but not [www.google.com](www.google.com), a switch to OpenDNS might fix your problem (or anybody else who's reading this).  [Here's a link to Ubuntu-specific instructions]("http://www.opendns.com/start/ubuntu.php").

---

### Post by amchl7 on 2007-04-11
thankyou both for your quick responses, changing to open dns did the trick and I am now responding to you whilst using ubuntu :-) thank you very much

---

### Post by PurplePenguin on 2007-04-12
Just a quick follow-up to the OpenDNS stuff...

Wikipedia has a great [entry on OpenDNS]("http://en.wikipedia.org/wiki/Opendns") that explains exactly what it is.  Most importantly, to linux guys like us, it is necessary to point out that OpenDNS is not open in terms of open source software.  It is, however, a valuable service that improves upon the old way of doing things.  For example, OpenDNS offers phishing protection and typo correction (go ahead, try it!).  In return, OpenDNS will display a page of advertisements any time it can't successfully correct your typo.  The ads do not affect a user's internet experience in a negative way.

So as long as you don't make huge typos, you will not see any ads!

Wikipedia does mention a criticism of OpenDNS: > The traditional form of DNS relies on a decentralized collection of servers scattered throughout the world which offers a high level of redundancy. OpenDNS centralizes this system, making it more susceptible to failure.
In order to take advantages of all of OpenDNS's benefits, but to add the redundancy of traditional DNS, you can always add traditional DNS to your network preferences after OpenDNS's lines.

---


---
title: "Can't get IP Address with Ubuntu 7.10 + Linksys WPC54GS"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by qbert00001 on 2008-11-09
I've been struggling with this for some time, and have recently given it another go.  I think I'm damn close this time, but can't quite get things working.  Here's my current situation:

I have a Linksys WPC54GS with Speedbooster card in my laptop.  I've got the card working using fwcutter/ndiswrapper.  This all went fine.  My network setup at home is a Netgear WGT624 v3 with latest firmware, configured for WPA2 encryption with AES cipher.  

My problem is this:  my laptop can associate with the router; iwlist scan shows the router, and iwconfig shows my card associated with the router.  Additionally, when I log in to the router I can see that it has associated with the laptop.  This, sadly, is as far as I get.  No matter what I do, I *cannot* get an IP address.  DHCP fails on ifup (the ubiquitous "No persistent leases is database -- sleeping" message).  Additionally, even when I configure the laptopn for a static IP, the router doesn't give it out.  

The other odd thing here is that even when 'associated' with the router, I can't ping it.  I can ping lo, of course.  

So my question is two-fold:  1) any ideas on what might be wrong?  Is it the WPA authentication step?  and 2) any tips on how I can go about debugging this?  Is there a verbose flag that I can use to see more diagnostic information when I bring up the interface?  I'm thinking of soemthing like the ssh -v flag, which gives tons of information about the handshake, etc.  

I spent a fair amount of time looking on the boards for other threads, but didn't find anything specific, so pointers to other possibly related threads would also be helpful.  

Thanks.

---

### Post by gpsmikey on 2008-11-09
It may be an issue with the router firmware etc, but I think the first thing I would do is turn off encryption on the card and router until you can get it working in the simple mode.  Once that works as expected, then go ahead and work the encryption problem.  There are too many variables in the equation at this point to solve the problem.  Networking is funny (well, usually funnier when it is someone elses problem ... ) - one bit wrong and nothing goes anywhere.  You might also want to check and see if the router has the latest firmware in it -- I found a problem a while back with my SMC router that was giving me fits until I found an obscure note in one of the "changes" page for the firmware to DNS forwarding.

mikey

---

### Post by qbert00001 on 2008-11-09
Good point.  This all started when I decided to switch from WEP to WPA and my linux laptop stopped working.  That led to several upgrades (had to get new wireless card as the on-board one did not support WPA, upgrade to horribly out of date OS, etc).  At one point I had no problem connecting wirelessly, but never with WPA.

---


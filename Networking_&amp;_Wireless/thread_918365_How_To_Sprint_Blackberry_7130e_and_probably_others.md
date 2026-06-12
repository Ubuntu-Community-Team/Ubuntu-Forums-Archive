---
title: "How To Sprint Blackberry 7130e and probably others"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by rubing on 2008-09-12
:KSI am tethering using my sprint 3130e blackberry using just Barry.  I have a phone as modem plan and do not know if this is even neccesssary....whatever....here's how I set it up.

chris frey from the barry project helped me get this set up...he rules!

OK first go to the barry page here: [ http://www.netdirect.ca/software/packages/barry/]("http://www.netdirect.ca/software/packages/barry/")

And read about it. It's not very long and overly complicated. Really pay attention to the software dependencies.  You gotta go and get all of those.  After you have all of the deps then you can install the barry debian binaries.  Get all of the latest ones barry, lib-barry, and barry-util.  


Barry auto installs all the chatscripts for the major phone providers.  All I had to do was make a minor modification to the sprint script:

sudo nano -w /etc/ppp/peers/barry-sprint

Then I made I had the following 2 lines:

REPLACEDEFAULTROUTE
DEFAULTROUTE

ok, now all i do is issue the following command

sudo pppd call barry-sprint

Presto.  I have internet 

pinging doesn't work, but just open firefox and it's there!!!!!

If you have any trouble just ask chris for help.  And if he's selling anything on his site buy it cause he's really cool!
:guitar:

Also I just did a speed test and got about 1000kbps down and 100kbps up:

[[IMG]http://www.speedtest.net/result/322557092.png[/IMG]](http://www.speedtest.net)

---


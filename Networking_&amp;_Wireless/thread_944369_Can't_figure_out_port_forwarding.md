---
title: "Can't figure out port forwarding"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by pfeifdog on 2008-10-11
I'm trying to get port forwarding to work.  I'm pretty sure I've properly set my Xubuntu machine with a Static IP, as it's connected to the internet.

I installed and am running Firestarter and opened the ports.

I followed the portfoward.com and figured out how to set my Linksys router to forward those ports to the IP I set as the static IP on the Xubuntu machine.

Still nothing!  I'm experimenting with aMule, and I always get a "Low ID" error message and extremely low download speeds.  (The ports I am forwarding are the same as those set in the aMule options).

Here's a guess at the problem.  I have this Westell 6100 DSL modem, and when I pull up the modem IP it displays options for Advanced Settings and "Enable Gaming and Applications."  The only problem... I don't know the username and password to the modem!  I wasn't there when the installation guy set it up, and neither my Verizon account login nor the default settings ("admin"/"password") work.  

Does anyone think that I *also* have to enable port forwarding on the *modem* to get it to work?

Additionally, is there an easier way to test my port forwarding setup?  I've heard of port scanning but I don't know how to do it.

---

### Post by superprash2003 on 2008-10-11
yes.. you mostly need to enable port forwarding in the modem.. if you are sure on how to configure your modem again, you could always reset your modem and configure it again, this time the modem would have the default username and password so you can access it.. Here's an online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by pfeifdog on 2008-10-11
Great ... making progress.  I contacted Verizon and the actual default password was admin/admin so I enabled port fowarding on the modem too.

Now when I try to connect, I see that Firestarter is blocking connections on the port I arbitrarily selected for TCP service (Port 5001).

Why would it do this if my Inbound Traffic Policy says: 
Allow Service: Unknown
Port: 5001
For: everyone

Do I need to specify a particular protocol?  I'm not sure which one to select.

---

### Post by pfeifdog on 2008-10-11
Scratch that!  I think Firestarter just needed to restart.  Awesome.  Thanks!

---


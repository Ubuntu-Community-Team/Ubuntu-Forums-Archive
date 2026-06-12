---
title: "Diagnosing bad connection"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by Jaymoid on 2005-10-17
Hey y'awl,

I'm having a little trouble. Basically my connection on my ubuntu pc at work is a bit ropey. Its an ethernet connection that works 99% of the time, however I find myself geeting kicked off remote servers whilst using them via a terminal (terminal just freezes up [tried both rxvt and gnome-terminal] and then it dissapears).  Also Gaim (with both goggletalk/jabber and msn accounts) and Synergy constantly disconnect. Its all very frustrating. So....

I was wondering if I could get some help diagnosing this problem, could I see a log, or a note of when my conn goes down and ideally why? I don't know whether its my network card, faulty wire (although I've tried several), faulty port, etc.

I'm a bit of a ubuntu noob, so if you can please dumb your answers down to almost spelling words phonetically that would be appreciated.

Thank you kindly

James

---

### Post by geokker on 2005-10-17
Exactly the same is happening to my Breezy installation. Terminal sessions die and Gaim signs off.

I have looked at /var/log/syslog and get this:

[I]Oct 17 17:18:56 localhost dhclient: No DHCPOFFERS received.
Oct 17 17:18:56 localhost dhclient: No working leases in persistent database - sleeping.
Oct 17 17:25:48 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5[/I]

Which suggests to me that there is a DHCP issue, but I have a static IP, so surely it's not relevant.

So, I need to know where to look to troubleshoot intermittant network connection problems. The logs seem useless.

I've just removed the network indicator from the notification area. A colleague suggested it - I'll post the upshot. Innit.

---

### Post by Jaymoid on 2005-10-18
Thanks for the reply, unfortunately I don't have the same error or anything to suggest any network problems in syslog (as far as I know anyway!). 

I also have static IP, and the network monitor on the notification area although I installed it because of my network problems, in an attempt to monitor when it goes down, so I don't think its the cause of any of my problems.

---


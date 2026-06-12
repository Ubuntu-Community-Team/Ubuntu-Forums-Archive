---
title: "Can't Access Ubuntu box with new DSL Modem"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by csete on 2007-12-30
Hello,

I'm trying to get external access to applications on my Ubuntu server through a new DSL modem, but I appear to be getting blocked and I'm not sure why.  I'm using Ubuntu 7.10 with Shorewall for iptables configuration.  I have various servers (ssh, https) poked through using rules in Shorewall that have worked fine for a long time.  I'm trying to replace my current Actiontec GT701 DSL modem on Qwest with an SBC branded 2Wire 2701HG-B.  While this "feels" like a problem with the DSL modem configuration somehow, in my discussions with others regarding the modem ([http://www.dslreports.com/forum/remark,19702535](http://www.dslreports.com/forum/remark,19702535)) they believe that it must be in my Ubuntu configuration somewhere.

I have the Ubuntu box in 2Wire's "DMZPlus" mode at the moment, which *should* allow all traffic through the firewall to the Ubuntu box.  Any attempt to connect from a remote system results in a connection timeout.  The primary difference from the Ubuntu's perspective is that the Ubuntu box now has the public IP address via DHCP.  With the actiontec modem, it had a private IP address that was static.  

I've also tried to put the modem into bridged mode and use pppoeconf to configure the connection.  That process failed due to an inability to find any concentrators.  

At this point, I've run out of ideas on what to try and I'm hoping that someone might be able to offer up some suggestions on what I could look for or try to get this working.  I need external access (especially port forwarding) for a few parts of my job, so I'm quickly running out of time to figure this out.

Thanks,
Craig

---


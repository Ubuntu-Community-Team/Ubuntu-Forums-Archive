---
title: "Iptables and Firestarter *confused*"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by adam_kimber on 2007-07-09
I use many inbound and outbound services from my machine and have been running Ubuntu for ages now. Only recently, (i think when the kernel updated but am not sure) have i had internet problems. My machine is behind a hardware firewall and NAT and I have had port forwarding set AND working for ages. 

However the only way now to get my system running as it used to is install Firestarter and click "stop firewall". Then everything works fine again. How do i permanently make this setting? Any files to edit, any programs to remove? I know Firestarter is swish GUI for iptables but am not sure what to do with iptables as I afraid that I might break my box. 

Doe sanyone have any suggestions on how to solve this annoyance. 

Thanks!

Adam :)

---

### Post by moore.bryan on 2007-07-10
*have you ever tried to uninstall firestarter?*

---

### Post by adam_kimber on 2007-07-18
Hey thank you for your reply. 

I had tried that before now and had installed Firestarter to resolve my problems with remote Samba and MPD connections to my Ubuntu box. However upon uninstalling today everything worked at it used to. So I am at a loss to what transpired between the orginal incident and today. I have had updates to my iptables package but am not really sure if that did anything. 

Anyway all resolved.

---

### Post by meindian523 on 2007-09-01
I don't know whether this is what is called hijacking a thread but this is related to the topic.
I hope no-one minds since the OP has had his problem solved.If the mods have a problem with this,please PM me about any possible violation and delete the posts.

My net connection is through the ISP called MTNL,in Bombay,India.(I believe my machine is connected to the Net through a proxy which assigns me a dynamic IP addres.I have installed Firestarter firewall but when I try to scan my PC by the [ShieldsUP! ]("https://www.grc.com/x/ne.dll?bh0bkyd2") resource,it shows me that ports 21,22,23 and 80 are open while 25 is stealthed and others are closed.Though I'm at a home-desktop,I wouldn't want my machine to be part of a zombie network implicated in a DoS attack.My machine also replied to pings.

Now,I don't know whether this analysis tested my machine or just the proxy,but I would prefer if someone could help me setup an iptables firewall(I guess it's the strongest??).I've tried various Google searches and searches of these forums but none of them described a procedure to setup an iptables firewall without going through the intricacies of iptables,NAT and masquerading.I have no objection to learning them but I would prefer my computer to be safe before I start understanding exactly how he firewalls work.Another port scan service went through the proxy and revealed my private IP address to me,therefore I'm seriously worried.Can someone help?

---

### Post by meindian523 on 2007-09-01
hello??nobody knows?

---


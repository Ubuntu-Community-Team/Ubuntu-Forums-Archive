---
title: "Sporadic Problems with NAT"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by nbt-tech on 2007-03-27
I recently installed a D-Link WIreless Router so that I can share out my internet connection between a few systems.

The router uses NAT.

I'm seeing some very weird behaviour in Ubuntu and Mozilla apps.

For instance, while I can send new mails and receive mails, I can't reply to mails!

I can't use scp.

There are certain websites that Firefox just won't connect to

eg

[www.essendex.com](www.essendex.com)

When I remove the router and plug straight into my Ubuntu system, everything works fine.

Also, everything works fine when I use the router with Windows XP.

Any help or shared experience appreciated.

---

### Post by Mr. C. on 2007-03-27
I'm betting your router's IP address is in /etc/resolv.conf.

If so, replace with your ISPs nameservers, fastest ones first, up to three nameserver lines.

If this solves the problem, we'll go to the permanent solution.

MrC

---

### Post by nbt-tech on 2007-03-27
> **Mr. C. said:**
> I'm betting your router's IP address is in /etc/resolv.conf.

If so, replace with your ISPs nameservers, fastest ones first, up to three nameserver lines.

If this solves the problem, we'll go to the permanent solution.

MrC

Thx, but this isn't the problem.

Firstly, I'm not using my router's ip address in resolv.conf

Secondly, its not a DNS issue.

e.g.

When I try to reply to an email in TB, I get prompted for a password from my SMTP server (i.e. name resolution is OK), and then the delivery process just stalls.

It has something to do with client ports in Ubuntu. ie Ubuntu is not allowing remote servers connect to client ports, because of the way they are being presented by NAT.

---

### Post by Mr. C. on 2007-03-27
There are several problems that exhibit these behaviors, so we have to start somewhere.  DNS is the easiest.  I doubt there is some mysterious NAT problem.

If you are sure that DNS is working perfectly, and you have disabled IPv6 globally, then review these:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435)
[http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/)
[http://marc.info/?l=postfix-users&m=115739945701551](http://marc.info/?l=postfix-users&m=115739945701551)

MrC

---

### Post by nbt-tech on 2007-03-27
I'm pretty sure DNS is working correctly. I don't have any name resolution problems.

And I have disabled IPV6.

I've tried the tcp_scaling fix, but no good.

Some more observations:

The problem with Thunderbird is not to do with replies, its to do with the size of the mail text. I can reply if I remove a portion of the quoted text.

Also, I have now determined that I scp small files, just not bigger ones.

So the problem is something to do with the volume of data in the network transaction.

e.g. I couldn't make this post when I included your quoted text!

---

### Post by Mr. C. on 2007-03-27
I'm sure you've checked for firmware updates from your router.

Perhaps this is a fragmentation issue.  See if ping with different payload sizes up to 1500 works.

MrC

---

### Post by nbt-tech on 2007-03-27
> **Mr. C. said:**
> I'm sure you've checked for firmware updates from your router.

Perhaps this is a fragmentation issue.  See if ping with different payload sizes up to 1500 works.

MrC

I think thats it.

I lowered the MTU on the router from 1500 to 1420, which was the maximum payload I could send in a ping and it seems to have worked.

Why would this affect Ubuntu and not my other systems (Redhat and Windows XP).

---

### Post by Mr. C. on 2007-03-27
Is your system or router is blocking ICMP fragmentation needed messages ?

Sometimes tinker's tinker too much...

MrC

---

### Post by nbt-tech on 2007-03-27
> **Mr. C. said:**
> Is your system or router is blocking ICMP fragmentation needed messages ?

Sometimes tinker's tinker too much...

MrC

Not sure. How would I check that?

Anyway, thanks for your help. I really thought this was going to be one of those "buy new hardware" problems.

---

### Post by Mr. C. on 2007-03-27
Your router may have a setting to block ICMP (or ping) messages.  There are many ICMP message types, ping being one of them.

If you are running iptables on your system, it may not be configured to receive these important messages.  This may explain why your other systems work (no iptables, or different iptables config in the RedHat case).  You'll have to look at your iptables if there are any.

If you are using and ADSL modem and/or a PPPoE connection, the MTU will be lower.  So either some downstream piece of hardware is either blocking or not delivering those messages, or some hardware on your end is blocking them.

If trial and error does not disclose the problem quickly, then tcpdumps may be required.

You said things work fine w/out the router, but fail with the router.  So, I'd lay odds that's the troubling component.  Again, be sure your Dlink's firmware is up to date.

MrC

---

### Post by nbt-tech on 2007-03-28
> **Mr. C. said:**
> Your router may have a setting to block ICMP (or ping) messages.  There are many ICMP message types, ping being one of them.

If you are running iptables on your system, it may not be configured to receive these important messages.  This may explain why your other systems work (no iptables, or different iptables config in the RedHat case).  You'll have to look at your iptables if there are any.

If you are using and ADSL modem and/or a PPPoE connection, the MTU will be lower.  So either some downstream piece of hardware is either blocking or not delivering those messages, or some hardware on your end is blocking them.

If trial and error does not disclose the problem quickly, then tcpdumps may be required.

You said things work fine w/out the router, but fail with the router.  So, I'd lay odds that's the troubling component.  Again, be sure your Dlink's firmware is up to date.

MrC

I had shut down iptables as part of my testing. 

The router is obviously blocking some sort of downstream response that Ubuntu cares about but that Redhat and WinXp don't. Seems like something is missing in the TCP handshake that prevents Ubuntu from carrying on with the negotiation.

I suppose it could also be something to do with my NIC.

---


---
title: "How much traffic is there really?"
date: 2018-02-03
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-02-03
I've been fighting an attack on our network and I think I've gotten it under control, however in the course of that I used a number tools to see what the traffic actuallt was, but none of the agreed. I used Performance Monitor, iftop and nethogs and they all gave wildly different versions of the amount of traffic on the network.

Does anyone understand what is going on here?

---

### Post by gordintoronto on 2018-02-03
Presumably, your network is connected via a router. In that case, the bulk of the attacks should stop at the router, and Performance Monitor, for example, would never see the activity. Unless your router is a Linux computer.

---

### Post by rsteinmetz70112 on 2018-02-05
Well in this case part of the attack was on a Linux Computer within the network, basically it was brute force ssh attempt from a single IP address which I have blocked at the router. That is not really what I'm asking about. Various tools viewing that computer gave vastly different answers on how much traffic there was on the network.

---

### Post by 1clue on 2018-02-05
Those tools probably focus on a specific type of traffic.

Some may collect data on all traffic seen by your system's network card, or ALL network interfaces. Others might focus on traffic directed at your system. Others might focus on inbound or outbound traffic, or ssh traffic, or http traffic, or whatever.

The more flexible/powerful a network monitor, the more you need to know in order to get useful data from it. For the less powerful ones, you need to know exactly what it is they're keeping track of.

It sounds like your ssh attempt was directed at a port forwarded system. The other alternative would be a public IP address on a commercial router, but I don't think you would be wording your post the same way were that the case.

If your attacked host is NOT port forwarded then probably the attack is coming from an internal host which was compromised somehow. That's much more likely than most people imagine, because in any office and most homes there is always somebody who will click on that stupid link.

Every Linux system with network access should, IMO, have fail2ban running at the bare minimum.

I've been using Linux since 1996. I have dozens of physical systems doing work in the enterprise, and most of those are hosts for VMs which usually also run Linux. Every time I set up a host, and almost every time I set up a VM, I go over security checklists again. The checklists are continually evolving and best practices will change over time. I keep builds which are good starting points for the types of systems I use, I try to keep them up-to-date for security, and then use those to build my guests from.

I recommend these for light reading, in order:
[LIST=1]
[*][https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[*][https://www.ubuntu.com/security](https://www.ubuntu.com/security)
[*][https://bbs.archlinux.org/viewtopic.php?id=27205](https://bbs.archlinux.org/viewtopic.php?id=27205)
[*][https://usn.ubuntu.com/usn/](https://usn.ubuntu.com/usn/)
[*][https://wiki.archlinux.org/index.php/security](https://wiki.archlinux.org/index.php/security)
[/LIST]

Note that I have a couple articles from Arch linux. One thing to note is that Linux security is not really very dependent on what distro you use. Arch has the best documentation of any Linux system I know. Gentoo is also extremely good. Get into the habit of reading these wikis/sites/notices and, whenever you have a question, open a new tab and google your question. Read, read, read. Understand.

Also understand how vulnerability databases are populated, how they're used and what that means for you as a system administrator.

Sorry for the rant. You seem like you know enough about Linux to have these questions, and that means you should be introduced to the real world of securing your system.

Another thing:

Many people insist that installing Ubuntu and running it as-is is secure. Under normal user circumstances they're probably right: It's *reasonably* secure for what normal home users do. Many people insist they've been running Linux for X number of years and have never been hacked. It's possible, but unlikely if their system is exposed to the outside world. The problem with normal as-is installs is that the user will not likely know whether they've been hacked. The days of the intruder/malware trashing your system are pretty much over. They want to use your system, either to get information about you or to work toward their goal which may have nothing to do with you. They don't want you to know they're there.

---

### Post by rsteinmetz70112 on 2018-02-06
It is a public IP address on a commercial router, but port 22 was open  it appeared to be a dictionary attack from a single IP address in China aimed a root ssh access which was blocked and so even though no login succeeded, the amount of traffic from repeated attempts had a severe impact on our networks Internet access.

---

### Post by 1clue on 2018-02-07
> **rsteinmetz70112 said:**
> It is a public IP address on a commercial router, but port 22 was open  it appeared to be a dictionary attack from a single IP address in China aimed a root ssh access which was blocked and so even though no login succeeded, the amount of traffic from repeated attempts had a severe impact on our networks Internet access.

You're using fail2ban right?

---

### Post by rsteinmetz70112 on 2018-02-08
> **1clue said:**
> You're using fail2ban right?

Yes and I've blocked the original IP at the router, but it keeps coming back from other IP addresses. I've also increased the ban time.

---

### Post by SeijiSensei on 2018-02-08
> **rsteinmetz70112 said:**
> Yes and I've blocked the original IP at the router, but it keeps coming back from other IP addresses.

Are they all in separate subnets?  If they're in a few subnets, block the whole subnet like
```
sudo iptables -I INPUT -s 172.16.0.0/16 -j REJECT
```

I bet there isn't any legitimate traffic originating on those addresses for you to worry about.

---

### Post by 1clue on 2018-02-08
> **rsteinmetz70112 said:**
> Yes and I've blocked the original IP at the router, but it keeps coming back from other IP addresses. I've also increased the ban time.

I've had bad luck increasing ban time.  The thing is, the longer your iptables rule list the slower your whole networking stack goes. Increasing ban time grows your iptables list in a huge way when you're being brute forced.

There has been some work about banning iptables from specific geographic locations, like by country. Some of that requires a patch to iptables and some data to be loaded regarding net blocks allocated per country.  IMO it might be simpler to simply enable only the country your users are in. Whatever gets you the shortest rule list is best for speed and probably for security. I haven't yet had reason to try it but I've been very tempted sometimes. So I don't know how well it works. It would obviously require periodic updates for what blocks are in the country in question.

The geographical blocks obviously can be easily circumvented by compromising hardware in non-blocked geographical locations. There's only so much you can do, but IMO the normal fail2ban functionality would still work. But if you're a company in (for example) the USA, and you only do business in the USA, then you could only allow traffic from the USA and save yourself a world of hurt. Any other country would not even see your services, or possibly even your IP address as being active at all.

[I]**Edit: **This has even more interesting possibilities if it's a limited number of users, say a small office with a handful of people who get access. You could find the IP blocks in the locality of your users, and enable only those. You'd likely be able to get down to the state at least, possibly to the city. This IP block range would likely be fairly static and also probably pretty short, so your iptables rule set would still be manageable, and again fail2ban would still be going.
[/I]

---

### Post by 1clue on 2018-02-09
I just checked geolocation and compared it to my gps coordinates. They got my location to within 4 km. So you could use a geolocation service if that works for you. I can't imagine that would be fast with respect to iptables though.

---

### Post by 1clue on 2018-02-09
> **SeijiSensei said:**
> Are they all in separate subnets?  If they're in a few subnets, block the whole subnet like
```
sudo iptables -I INPUT -s 172.16.0.0/16 -j REJECT
```

I bet there isn't any legitimate traffic originating on those addresses for you to worry about.

You're using a non-routable IP address as an example right? You (and hopefully everyone else reading this) will understand that the only way that address comes through your router is if you're attached to a VPN?

---

### Post by SeijiSensei on 2018-02-09
Yes, of course. I don't want to use a real address that might be in use.

Anyone who knows enough to write iptables rules should recognize that a 172.16 address is private.

---

### Post by rsteinmetz70112 on 2018-02-09
> **SeijiSensei said:**
> Are they all in separate subnets?  If they're in a few subnets, block the whole subnet like
```
sudo iptables -I INPUT -s 172.16.0.0/16 -j REJECT
```

I bet there isn't any legitimate traffic originating on those addresses for you to worry about.

I have no worry about legitimate traffic from those addresses. Unfortunately some come for the same subnet, but others are completely different. I'd have to monitor it for a while to determine if the number of subnets is limited.

---


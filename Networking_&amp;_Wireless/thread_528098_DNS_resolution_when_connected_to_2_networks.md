---
title: "DNS resolution when connected to 2 networks"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by ihristov on 2007-08-17
How can I have selective DNS resolution depending on the target domain name?

I have an annoying issue with DNS resolution when I am connected to a second private network with a VPN.

On my laptop when I am in the office I have DNS resolution from the local DNS server, which returns me local IP addresses. For example a query like mail.mydomain.com would return the local IP address of the mail server and I can connect to it.

After I establish a VPN connection, my DNS settings (/etc/resolv.conf) gets overriten and the DNS server from the remote network takes over.

Now the query mail.mydomain.com returns the public IP address of the mail server and I can't connect to it.

The only workaround I have is to update my local /etc/hosts with the correct private IP address. However when I take my laptop outside my office I have to go in there and remark the entry (or update it to the correct public IP address).

I would assume this is a pretty common issue. How are people dealing with this?

---

### Post by PirateFanAZ on 2007-12-08
bump.

I am having very similar issues on Gutsy.  When connected to my work network via VPN I can not use my system's web browser without using IP addresses.  For example I can't navigate to [www.google.com](www.google.com) but i can get to google via [http://72.14.253.103](http://72.14.253.103).  I also see that /etc/resolv.conf is overwritten while my VPN is running and only contains my work network's dns server names.  I can connect to my work machine using terminal server client but I really need to access the internet while connected to work.

I find myself having to use VMWare Server to start a VM running XP and using XP's VPN client and remote desktop instead.  I feel very uncool........  :(

Any help would be much appreciated.

---

### Post by ihristov on 2007-12-08
One workaround is to override /etc/resolv.conf. You could even have this done automatically.
This could have the bad side effect to break your name resolution for the hosts in the private network you have connected to. It depends.

The ultimate solution is to have a DNS server that is smart enough to know which upstream DNS server to use depending on domain. I don't know of any DNS server that does this. Also this could be potentially fixed in the local resolver library that decides how to resolve names in the first place.

I am just not clear why no one has complained about this. Maybe I am missing some obvious solution?

---

### Post by thale on 2007-12-11
I'm curious if anyone else has found a solution for this as it makes Ubuntu somewhat useless in a "working from home" capacity . . . which makes me very sad . . .

---

### Post by ihristov on 2007-12-11
> **thale said:**
> I'm curious if anyone else has found a solution for this as it makes Ubuntu somewhat useless in a "working from home" capacity . . . which makes me very sad . . .

I disagree. It's not Ubunu's fault. Any other OS that I know of suffers from the same problem. Including Windows.

The only workaround I know is to hard-code the names to servers you need in /etc/hosts. Not very convenient, but don't know of another way.

---

### Post by mrgrave on 2008-05-09
Combination of techniques: create a CACHE/SLAVE local DNS with bind, where you can set the zone that corresponds to your company's to be queried with your company's DNS but any other route should be resolved by an external DNS.

Your own box will query your LOCAL bind service and that will take care from where it grabs the name resolution, either internal DNS (your company's) or the outer world.

---

### Post by ihristov on 2008-05-10
> **mrgrave said:**
> Combination of techniques: create a CACHE/SLAVE local DNS with bind, where you can set the zone that corresponds to your company's to be queried with your company's DNS but any other route should be resolved by an external DNS.

Your own box will query your LOCAL bind service and that will take care from where it grabs the name resolution, either internal DNS (your company's) or the outer world.

I agree it's possible. The question is how to do it. What is the exact configuration for this? How difficult it is to do? 

I was hoping someone smarter than me has solved the issue and post the solution. I would imagine it involves having to install BIND (or probably better to use dnsmasq), configure it to listen only to localhost, configure it to query the corresponding upstream DNS servers and finally make sure /etc/resolv.conf is using localhost.

Ideally this configuration would be location aware. I.e. would use different upstream servers when in different networks.

---


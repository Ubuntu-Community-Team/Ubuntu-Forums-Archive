---
title: "Ubuntu won't Detect my LAN"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by xalem on 2006-10-25
Hi :)

So I decided to try Ubuntu yesterday. What I've seen looks pretty nice....

The one thing that didn't go accroding to plan was that the networking won't recognize my LAN port. So, I have no connection and no network.

What's the process with Ubuntu?

Thanks for you help,
Xalem

---

### Post by Iowan on 2006-10-25
My first two installs on this machine went beautifully (Breezy and Dapper).  Since then I've been having problems - so my advice might be suspect...
What is controlling your network (An awkward attempt to ask what the local subnet is - 192.168.1.X)?
If you're running Ubuntu (as opposed to Kubunto or Xubuntu), check under System>Administration>Networking to see if your interface is active. (You didn't mention wired or wireless).  
It's possible that the default installation doesn't support your NIC, but drivers may be available.
Depending on your network, you may choose DHCP or static address.  If it's already set for your network, you can use System>Administration>Network Tools to (attempt a) **ping** one of the other machines on your network.

---


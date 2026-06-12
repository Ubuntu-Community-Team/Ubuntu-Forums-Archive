---
title: "Filter websites by URL?"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2005-11-18
I'd like to filter what URLs an individual can and cannot go to.

Basically I just want to make a whitelist that only root can modify, that will determine what websites the PC can connect to.  We have a row of computers to use specific web applications, but people are surfing the web and playing games instead, and it would be nice just to shut them out completely.  It would also be cool to give the windows users an interface to modify the config file and update whatever app blocks the pages.

Anyway, the most important thing is how do I block all but a few websites from an ubuntu machine running firefox?

---

### Post by OneSeventeen on 2005-12-08
Here's an update, I figure I can do this with iptables and just filter based on IP, but is there a way to tell iptables to dissallow ALL IP addresses and ALL ports, then **only** allow a specific range of IPs and port 80/443 and whatever port SSH uses?

---

### Post by mips on 2005-12-09
[https://lists.netfilter.org/pipermail/netfilter/2005-February/058703.html](https://lists.netfilter.org/pipermail/netfilter/2005-February/058703.html)
[http://www.siliconvalleyccie.com/linux-hn/iptables-intro.htm](http://www.siliconvalleyccie.com/linux-hn/iptables-intro.htm)
[http://www.naspa.com/PDF/2002/0602%20PDF/T0206005.pdf](http://www.naspa.com/PDF/2002/0602%20PDF/T0206005.pdf)
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

---

### Post by mips on 2005-12-09
You could set this up on every machine but it would be much easier having one machine act as an gateway/router and setting up the IP filtering on that one machin, can even do on a per host basis.

Also look into Squid.

---

### Post by OneSeventeen on 2005-12-09
I'll look into squid, I've come across most of these in my previous searches, which lead me to think it would be super easy just to write a quick script that would execute on each machine that would basically say:

iptables {block everything}
iptables {allow 3 IPs on port 80/443 and another on port 22}

done!

I was hoping I could do that since I don't need advanced filtering techniques, I just need to block all but a few IPs, which seems like a simple task.  I'm hoping to keep this as simple and easy to use as possible.

If I set a computer up as a Firewall, how do I tell all the other computers to go through that one first?  and then does that mess up the existing network (as I have no control over the network whatsoever)?  Also, does that make it more difficult for me to SSH into the machines to do maintenance from my office?
**EDIT:**
Just a side note, the IP's I'm using change once every few years if the servers move into a new subnet, but that's about it, so we're not talking sites like CNN or MSN, just some simple internal apps.

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=OneSeventeen]I'll look into squid, I've come across most of these in my previous searches, which lead me to think it would be super easy just to write a quick script that would execute on each machine that would basically say:

iptables {block everything}
iptables {allow 3 IPs on port 80/443 and another on port 22}

done!

I was hoping I could do that since I don't need advanced filtering techniques, I just need to block all but a few IPs, which seems like a simple task.  I'm hoping to keep this as simple and easy to use as possible.

If I set a computer up as a Firewall, how do I tell all the other computers to go through that one first?  and then does that mess up the existing network (as I have no control over the network whatsoever)?  Also, does that make it more difficult for me to SSH into the machines to do maintenance from my office?
**EDIT:**
Just a side note, the IP's I'm using change once every few years if the servers move into a new subnet, but that's about it, so we're not talking sites like CNN or MSN, just some simple internal apps.[/QUOTE]

How is your LAN set up?  Normally, all the computers in a small LAN are going to route to the Internet through the same gateway, so that is where you would logically set up the firewall and IP filtering.

If you can arrange things so that a particular Ubuntu machine serves as the gateway, then you can simply install your rules there.  However, if that is not an option, you can install the rules on each of the PCs individually.

---

### Post by mips on 2005-12-10
[QUOTE=OneSeventeen]
If I set a computer up as a Firewall, how do I tell all the other computers to go through that one first?  and then does that mess up the existing network (as I have no control over the network whatsoever)?  Also, does that make it more difficult for me to SSH into the machines to do maintenance from my office?
**EDIT:**
Just a side note, the IP's I'm using change once every few years if the servers move into a new subnet, but that's about it, so we're not talking sites like CNN or MSN, just some simple internal apps.[/QUOTE]

That all depends on how your network is setup. Maybe you can give us a simple diagram/layout to comment on.
On the other computers You would basically specify the firewall IP address as the default gateway. It should not mess up your network or make things more difficult.

A simple diagram would help a lot in formulating a more accurate reply.

---

### Post by OneSeventeen on 2006-02-09
The layout looks like this:
10 computers I have 100% control over plug into the wall.

The cables go from the wall to a routing closet I have 0% control over, then on to our main building with the servers I have 0% control over.

I'm trying to do this as simply as possible, considering the only thing I have access to are the computers themselves.  I was hoping for a simple whitelist utility, as I really can't figure out why it would be hard to just deny all but a few IPs in each system's software firewall.

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=OneSeventeen]The layout looks like this:
10 computers I have 100% control over plug into the wall.

The cables go from the wall to a routing closet I have 0% control over, then on to our main building with the servers I have 0% control over.

I'm trying to do this as simply as possible, considering the only thing I have access to are the computers themselves.  I was hoping for a simple whitelist utility, as I really can't figure out why it would be hard to just deny all but a few IPs in each system's software firewall.[/QUOTE]
You can do what you want to do.  You just have to make sure the script stays in sync on each machine.  If your setup were larger (many PCs), it might start to become impractical.

---

### Post by OneSeventeen on 2006-03-20
[QUOTE=cwaldbieser]You can do what you want to do.  You just have to make sure the script stays in sync on each machine.  If your setup were larger (many PCs), it might start to become impractical.[/QUOTE]
Any tips on what that script might look like?

I've looked into a few different iptables/squid/etc type apps, but none of them seem to have a simple whitelist feature that is easy to use and setup on each computer.  (or at least they don't advertise this feature on their website)

I know most networks would use a single application on the gateway server, so my method of doing this is the exception, not the rule, but a simple whitelist app shure would be welcome.  (I'm also thinking of just making my own liveCD with the whitelist built in, so the computers don't even need a hard drive)

---


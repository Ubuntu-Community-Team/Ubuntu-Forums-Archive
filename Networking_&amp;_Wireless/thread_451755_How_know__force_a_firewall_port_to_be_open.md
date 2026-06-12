---
title: "How know / force a firewall port to be open?"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by christian.convey on 2007-05-22
Can anyone tell me how to discover whether or not my vanilla Feisty box is letting in TCP traffic on a particular port #, and if not, how I can open that up?

Thanks,
Christian

---

### Post by moore.bryan on 2007-05-22
[I]all ports should be closed by default, afaik... you could either write an iptables rule or use a firewall program.

[this]("http://www.cse.msu.edu/%7Eminutsil/iptables.html") is a good start for the former, while i personally use [ubuntu-firewall ]("http://rob.pectol.com/content/view/2/29/")for the latter; you could use any firewall program, though, like firestarter, guarddog, etc.

[/I]

---

### Post by christian.convey on 2007-05-22
Actually, doesn't the following output mean that they're all *open* by default?

root@pascal:/home/cjc# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by Harkainos on 2007-05-22
I am editting ubuntu-firewall and setting the ports I'd like to allow.

This is for World of Warcraft. How would I allow ports 6881-6999 w/out typing each one individually?

---

### Post by moore.bryan on 2007-05-24
> **christian.convey said:**
> Actually, doesn't the following output mean that they're all *open* by default?

root@pascal:/home/cjc# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

[I]first question, why are you running as root?  secondly, i don't think they're open unless you've opened them.  afaik, when you install ubuntu, all the ports are closed by default.  to find-out for certain, use a port-scanner like the one at hackerwatch ([http://probe.hackerwatch.org/probe/probe.asp](http://probe.hackerwatch.org/probe/probe.asp))

[/I] > **Harkainos said:**
> I am editting ubuntu-firewall and setting the ports I'd like to allow.

This is for World of Warcraft. How would I allow ports 6881-6999 w/out typing each one individually?

*unfortunately, i don't think you can... i wanted to do the same thing and emailed the author a while ago, but never heard back.*

---

### Post by robert_pectol on 2007-05-24
> **moore.bryan said:**
> [I]first question, why are you running as root?  secondly, i don't think they're open unless you've opened them.  afaik, when you install ubuntu, all the ports are closed by default.  to find-out for certain, use a port-scanner like the one at hackerwatch ([http://probe.hackerwatch.org/probe/probe.asp](http://probe.hackerwatch.org/probe/probe.asp))

[/I] 

*unfortunately, i don't think you can... i wanted to do the same thing and emailed the author a while ago, but never heard back.*

Actually, you can!  Simply separate the first and last port with a colon.  In this case, you'd put:
```

OPEN_TCP_PORTS="6881:6999"

```

Hope that helps.  :-)

---

### Post by psusi on 2007-05-24
By default, all ports are open, and wow does not need any open ports; it does not listen for connections.

---

### Post by robert_pectol on 2007-05-25
> **psusi said:**
> By default, all ports are open, and wow does not need any open ports; it does not listen for connections.

Actually, by default, all ports on an Ubuntu Box are closed, but not blocked.  In order for a port to be open, there has to be a listening socket established by some server app or program.  As for WOW, I don't know.  I don't have it.

---

### Post by moore.bryan on 2007-05-25
[I]@robert_pectol

thanks for the info about the range!  i just figured you were super-busy and unable to reply to most emails... kudos to writing an excellent firewall!!
[/I]

---


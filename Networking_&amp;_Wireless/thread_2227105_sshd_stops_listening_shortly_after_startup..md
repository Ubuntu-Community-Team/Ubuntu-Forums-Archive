---
title: "sshd stops listening shortly after startup."
date: 2014-05-30
forum: Networking &amp; Wireless
---

### Post by 1clue on 2014-05-30
Hi.

Ubuntu Server 12.04 on VMware ESXi, 64-bit.

I have a server that suddenly stops accepting connections.  If I'm logged in it will boot me out.

It's a remote server, and I have to RDP to a Windows box in order to get to the console.  The console keeps repeating characters at random, so I hate using it.  You type a g and you might get ggggg.  But that's not the real problem.  It just makes the real problem much, much worse.

The server stops listening on ssh.

OK so this thing is behind a firewall, so I ssh to another system (which also happens to be an ESXi guest) in order to get access to this one.

Right now the system is in a state where ssh is up but not responding.  The black screens are from the box with the problem, the tan screen is the remote client.

As you can see, the box thinks it is still listening, but the nmap doesn't detect it.  It's also listening on an ipv6 address so I don't know if that's a problem.

Thanks.

---

### Post by papibe on 2014-05-30
Hi 1clue.

If your connection is drop while you are connected, it could be a [non statefull firewall]("http://en.wikipedia.org/wiki/Stateful_firewall"), or if behind NAT, non properly set up port forwarding or DMZ rules.

I'd recommend checking the rules of any firewall, router in the path (including the server itself). 

As a side note, you can even change the ssh port, restart ssh, and the current connection (over the old port) won't get drop.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by 1clue on 2014-05-30
Except that the host I'm connecting to first is on the same ESXi box on the same network.  This is a new install, no firewall setup.

And as far as i can tell, no logging as to why ssh doesn't like me anymore.  It seems that the only thing that gets it started again is rebooting the box.  Then I get ssh connectivity for 5 minutes or so, and it stops again.

---

### Post by papibe on 2014-05-30
Sorry to hear that.

A few thoughts:

Is the server bridge to the open network, or behind NAT?

Can you ping/mtr/traceroute the server after ssh connectivity is gone?

Have you check the ESXi Firewall configurations?

Are you using the same ssh port on both VMs (the one that's working and the one's that's not)?

Regards.

---

### Post by 1clue on 2014-05-30
It's bridged network according to the LAN, the site router is using NAT.  So whether you're using real computers or VMs, they're all on the same 192.168.1.x and the only DHCP server is the same one real computers use.

The hosts in question are servers though, so they have static IP addresses.

There is a configured firewall on the site, but not within the site.  iptables is not installed, nor is ufw on this box I'm having trouble with.

I can ping it, and I can nmap it and get some ports back.

ESXi has no firewall configuration.  It's deliberately left blank.

There's a box A that has the problem, box B (and C, D, ... about 12 of them) which do not have any problems, and have had months of uptime each.  B is routed such that I can get to it with SSH from outside the LAN with a nonstandard port.  Both A and B are VMs on the same ESXi box.

I ssh to B, then from there I can ssh to A.  Or any other box in the LAN.  There is a box C from which I can run nmap.  Which also happens to be a VM on this ESXi server.

The firewall on this site is a SOHO router with a single IP address.  As such I can't use default ports in most cases.  The ssh port is mapped to a high numbered port.  Internally, they all use the default port.  In other words, from outside I can get to B by a nonstandard port, but from there I can go to C and then back to B again using default ports.  The router is what has the nonstandard port, not the Linux box.

---

### Post by 1clue on 2014-05-30
Solved.  I pulled my head out of my ... self ...  (see image), and thought about it.

I changed the IP address, rebooted and I can still ping the original IP address.  I have a rogue on the network who thought to get his own IP address.

Thanks.

---

### Post by papibe on 2014-05-30
Glad you worked it out! ;)

---

### Post by 1clue on 2014-05-30
Took me long enough.  I've been a network admin for years, but in this case there are a few supposedly knowledgeable people with access, I figured they would be smart enough to ask for an address.  Most of them do DHCP and let me handle the servers.

Thanks for your time though.

---


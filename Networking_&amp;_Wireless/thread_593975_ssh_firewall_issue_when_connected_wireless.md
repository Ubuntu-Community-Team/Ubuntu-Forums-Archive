---
title: "ssh firewall issue when connected wireless"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by Nokia on 2007-10-27
Hello everyone,

I ran into a problem lately and I'm asking for your help in solving this peculiar issue.
For about two years now, I've been using Guarddog as a graphical tool to help me setting up  in relatively short time a firewall on various  boxes  where I had to install  Ubuntu. Until recently, all went fine as long as I dealt with wired connections, eth0 to be more precise.
My puzzle appeared a few days ago when I noticed on three different Dell laptops that I could ssh without problems form inside to outside and vice-versa when connected to wired network on eth0, yet when using wireless on eth1, a connection initiated from outside to inside could not be established despite the fact that on the same wireless connection I could ssh without problems form inside to outside. To add to the confusion, I have to mention that in case of disabling and re-enabling the firewall manually when connected on the wireless link, ssh form outside to inside works perfectly.
I hope someone could explain to me what could be done to resolve this situation, and also what is the cause for this mess. I suspect that there's something wrong regarding the firewall's configuration when having two different networking cards on the inside, eth0 and eth1.
To avert false interpretations on the issue I described above, I want to state very clearly that any other networking issues such as port forwarding have been eliminated. It's just a matter of understanding how iptables works when using Guarddog.
Thanks in advance for any suggestion you might have.

---

### Post by Nokia on 2007-10-28
Maybe someone could indicate a place to start looking for similar issues being discussed.

---


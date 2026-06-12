---
title: "Telnet connection troubles... localhost works."
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by daifanshi on 2007-03-02
Greetings,

I'm having problems connecting (connection refused port 23, etc...) to my Ubuntu Edgy computer from within my own LAN.   From the Ubuntu computer, I can use telnet localhost and telnet <my LAN ip address> with no problems. However, I cannot use another computer on the lan to connect.  This Ubuntu computer can connect to the internet.

I installed netkit-inetd and telnetd in order to get the telnet daemon running.  I can ping the Ubuntu box from any computer on the LAN.    I am using an Atheros wireless card that shows up as "ath0" as the interface.

So far I've disabled iptables with lokkit and confirmed by iptables -L that there are no rules. And using netcat on the localhost shows that port 23 is listening. 

And I have the same problem with SSH. Anybody have any ideas?
Thanks.

DFS

---

### Post by nyinge on 2007-03-02
Have you installed openssh-server?  Ubuntu doesn't have sshd installed by default.

---

### Post by daifanshi on 2007-03-02
> **nyinge said:**
> Have you installed openssh-server?  Ubuntu doesn't have sshd installed by default.

I installed the openssh server when I became frustrated with telnet. I can't connect with SSH either.

---

### Post by nyinge on 2007-03-02
hmm... ok..  All I can think of... is to check if the default port 22 has been changed and to make sure you're using the username that is created on the box you're ssh'ing into.

---

### Post by daifanshi on 2007-03-04
Some progress.

If I use the wired adapter (eth0) instead of the atheros wireless interface (ath0), I can telnet into the Ubuntu box without any problems.  

Any ideas?

DFS

---

### Post by endtroducing on 2007-03-05
Hi!

Did you check your hosts.allow and hosts.deny?

E

---


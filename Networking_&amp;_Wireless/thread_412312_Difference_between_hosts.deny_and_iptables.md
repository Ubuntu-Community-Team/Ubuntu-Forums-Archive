---
title: "Difference between hosts.deny and iptables?"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by kwas101 on 2007-04-17
Hi there,
This is probably a stupid question, but I'll ask it anyway - what is the difference between a firewall and the hosts.deny file? I mean I know that a firewall blocks packets based on what port they are going to/from. but if I set hosts.deny to all:all does that also block everyone from accessing my system or have I missed something? Does ubuntu come with any kind of iptables default setting?
Cheers Stephen :)

---

### Post by joft on 2007-04-18
Well, the host.deny file is read by some/most (?) daemons (mail servers, ftp ...) and then these daemons follow the rules you gave there. iptables is in-kernel and sits on the network/tcp/ip stack. So if you block a port with iptables the daemon which is listening on that port _never gets any packet_. If you use host.deny (and your daemon supports host.deny), the daemon _will still get all packets and just refuses them_.
So: No, setting all:all in general does not block everyone, it depends.

IMO you shouldn't call/think of host.deny feature /as a firewall ...

Hmmm, by default iptables is "off" in Ubuntu - all things are "allowed".

---

### Post by kwas101 on 2007-04-19
Thanks Joft. Anothe question then, I've been using Ubuntu for about 12 months now, but always on my home desktop (I have a smoothwall firewall). Last week I finally got the courage to install it on my laptop (see my sig!). And it went really well. I have a wireless broadband modem which I had some minor troubles getting working, but all was cool. Then (*smacks forehead*) I realised that I had been running the modem for about an hour with no firewall! hosts.deny was set to all:all at the time - but no iptables. I have since download and enabled firestarter, so I hope all is OK. My next questions 1) Firestarter is a gui front end to iptables right? Once I have made changes in fs they are permanent rules in iptables? 2) Can I scan my laptop with some kind of tool which will check and see if anyone has installed any nasties on my PC when it was unprotected?
Thanks for your help
Cheers Stephen:)

---

### Post by joft on 2007-04-19
I'm sorry, I haven't used Firestarter yet, so I can't answer any question regarding Firestarter. But I think Firestarter is a iptables fronted, at least a quick call on apt-cache show firestarter reveals, that it depends on iptables. By 2), do you mean rootkits? But not much experince here ether ... sorry. This would be a question for a new thread.

---

### Post by kwas101 on 2007-04-20
Hi,
Yep rootkits :-(
OK will ask new question thanks for your help!
Cheers Stephen :-)

---


---
title: "How do I share 2 Internet connections (ADSL + CABLE) using Ubuntu?"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by SoulSlave on 2008-01-02
Good Morning, I've been using ubuntu for some time now, but so far, only for networking file server, and "download server" (P2P).

But now, I've added another internet connection to my old one, and I want to share both ADSL and Cable conections to my network and I dont want to buy a router.
I want to know how to do that with ubuntu.

Can anyone help me? Maybe sugest a tutorial (I wasn't able to find one for may case).

THX!

---

### Post by Predator[23rd] on 2008-01-02
Hi!

Silly question: why do you want to share both connections?

Anyway, what you can do is to setup one ubuntu box as router ([https://help.ubuntu.com/7.04/server/C/ip-masquerading.html](https://help.ubuntu.com/7.04/server/C/ip-masquerading.html)) and have as many computers behind it as you want.

---

### Post by SoulSlave on 2008-01-02
I wanna do some load balance, in order to have the bandwidth of both connections + being sure to always have a internet connection available.  (The DSL line came for free to me, as part of my work, but I cannot change the speed, so i ordered another one, Cable in this case).

---

### Post by Predator[23rd] on 2008-01-02
Interesting! Hope you can make it work, although I think it will be quite a challenge. Simple masquerading won't probably not work here .... Good luck!

---

### Post by GTvulse on 2008-01-02
> **SoulSlave said:**
> 
But now, I've added another internet connection to my old one, and I want to share both ADSL and Cable conections to my network and I dont want to buy a router.
I want to know how to do that with ubuntu.

Can anyone help me? Maybe sugest a tutorial (I wasn't able to find one for may case).

THX!


Well, you are talking big leagues here. What you want is a load-balancing (and probably bridging) firewall.  It is a lot of work to get it right by  hand but it is certainly the best way to become an expert on Linux networking (tip: shorewall is an excellent tool to program iptables and create such setup). The how-to you want is the "Linux Advanced Networking Guide" available at [http://lartc.org/](http://lartc.org/) It expects you to have read some other material first; all the links are there.

Now, being quite frank, you would be far better off using a prepackaged firewall distribution. I've played with most free firewalls out there and my recommendation for the kind of need you have is pfSense ( [http://www.pfsense.org/](http://www.pfsense.org/) ) which is based on FeeBSD and the OpenBSD's Packet Filter (PF). Get the latest release candidate of the 1.2 version at [http://snapshots.pfsense.org/FreeBSD6/RELENG_1_2/iso/](http://snapshots.pfsense.org/FreeBSD6/RELENG_1_2/iso/) . You can program it with a simple web interface. Many people who recommend IPCop forget to mention that you need to hack the iptables scripts by hand if you want to do anything advanced.

---

### Post by SoulSlave on 2008-01-02
> **dradul said:**
> ... Now, being quite frank, you would be far better off using a prepackaged firewall distribution. I've played with most free firewalls out there and my recommendation for the kind of need you have is pfSense ( [http://www.pfsense.org/](http://www.pfsense.org/) ) which is based on FeeBSD and the OpenBSD's Packet Filter (PF). Get the latest release candidate of the 1.2 version at [http://snapshots.pfsense.org/FreeBSD6/RELENG_1_2/iso/](http://snapshots.pfsense.org/FreeBSD6/RELENG_1_2/iso/) . You can program it with a simple web interface. Many people who recommend IPCop forget to mention that you need to hack the iptables scripts by hand if you want to do anything advanced.

Sounds very nice, i've given some thought into it myself, but in this case, I would still lack my file and downloads server, so my next question is: Can I use such distros in a Virtual machine? I know it has o hole new pack of implications, but it is possible isn't it? THX again!

---

### Post by GTvulse on 2008-01-03
> **SoulSlave said:**
> Sounds very nice, i've given some thought into it myself, but in this case, I would still lack my file and downloads server, so my next question is: Can I use such distros in a Virtual machine? I know it has o hole new pack of implications, but it is possible isn't it? THX again!

Hmm... If there is something that should not be virtualized is a firewall. If you have only a box to dedicate for your gateway and servers, I'd suggest you explore other kind of OS distro. Hmm.... Either ClarkConnect or Vyatta community edition would be a better choice. I would pick Vyatta myself, because it is based on Debian, as Ubuntu, and you can use Debian repositories to install the extra wares.

---


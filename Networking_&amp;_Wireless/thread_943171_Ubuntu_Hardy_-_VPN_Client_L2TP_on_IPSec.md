---
title: "Ubuntu Hardy - VPN Client L2TP on IPSec"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by softfarr on 2008-10-09
Hi. I need to connect my laptop with a Win2003 VPN Server working with L2TP on IPSec. My laptop is installed with Hardy Heron. I've read about but I don't know how and what to install. openvpn client? openswan? NetKey? Klips?

I'm newbee to this.

What should I install to become connected?

Thanks for your cooperation.

SoftFARR:guitar:

---

### Post by n00blar on 2008-10-30
I've been trying to get this to work as well, and I have yet to find a way to do this.
I need to connect to my office PIX firewall using l2tp, but it seems that this topic isn't too popular in linux.

---

### Post by kangyu29 on 2008-12-11
I believe there are alot of people have the same problem. So many universities, companies are using l2tp on ipsec. ubuntu team should really consider making some head way with this now.


> **n00blar said:**
> I've been trying to get this to work as well, and I have yet to find a way to do this.
I need to connect to my office PIX firewall using l2tp, but it seems that this topic isn't too popular in linux.

---

### Post by max_freespirit on 2009-02-06
I have a 8:10 and ubuntu as a client must
connect into a vpn firewall clavister,
that exploits the vpn l2tp over ipsec.
Help me, Thanks!
Good day!
Massimo

---

### Post by matrixblue on 2009-04-12
Why are post regarding l2tp ignored? This is very important for some people. I convinced someone to switch to Linux but their ISP uses L2TP authenticate users accessing the internet.

I've googled the topic and found a few posts on several forums but all have been ignored just like this one.

Unfortunately I'm going to have to put windows Xp back on their system so that they can get online.

I think the community (both Linux and Ubuntu) really let us down on this issue.

---

### Post by K_REY_C on 2009-08-27
> **matrixblue said:**
> Why are post regarding l2tp ignored? This is very important for some people. I convinced someone to switch to Linux but their ISP uses L2TP authenticate users accessing the internet.

I've googled the topic and found a few posts on several forums but all have been ignored just like this one.

Unfortunately I'm going to have to put windows Xp back on their system so that they can get online.

I think the community (both Linux and Ubuntu) really let us down on this issue.

Let me jump on the bandwagon by saying that this is disappointing indeed. While I wish the whole universe used items flawlessly compatible with ubuntu, etc... it is not the reality. This is a major frustration and an almost certain deal-breaker for most people who need this for work.

Any help appreciated. I'm not going to stop using Ubuntu... but this certainly makes it harder.

---

### Post by zeroandone on 2009-10-01
> **K_REY_C said:**
> Let me jump on the bandwagon by saying that this is disappointing indeed. While I wish the whole universe used items flawlessly compatible with ubuntu, etc... it is not the reality. This is a major frustration and an almost certain deal-breaker for most people who need this for work.

Any help appreciated. I'm not going to stop using Ubuntu... but this certainly makes it harder.
It is the only thing that stops me from switching to Ubuntu. I have to connect to my office Windows machine through L2TP VPN. Any help is highly appreciated.

---

### Post by krisskross on 2009-11-07
I'm not sure if this is a Ubuntu related issue, anyway I want to find a solution in order to log on to the companies network.

While completely new to the network stuff I had to learn how the MS clients connect to our RADIUS (is that the right term?) which is reachable via internet if I point the connection to vpn.mycompany.com

My first try was to use PPTP but that was the wrong move from my side.
The company uses computer certificates plus user certificates to authenticate the request and as soon as this request is accepted prompts for the RSA securID token in conjunction with my Username. Tough stuff!

I can't figure out how to set up such a VPN connection with XP. I only have to guess how it works. 

The computer must become member of the windows domain first time when logging on. Then the necessary certificates will be issued for the machine as well as the user.

So first thing I have to find out if and how this can be done with Ubuntu.

If not I need to find out if the computer and the user certificates can be transfered from the XP box to the Linux box. Especially for the computer certificate I actually think it is almost unlikely.

Anyway: even if I can manage to get those certificates (Can a Linux box become member of a windows domain to obtain that?), I haven't found a solution or a how to describing what must be done to create the connection with the certs in hand. How to include that in the network manager would be a final step after creation.

Anyone ever found a way to get in to his companies domain using those certificates and RSA token?

Cheers

Chris

---

### Post by tors on 2010-01-13
This might be of interest:

[https://bugs.launchpad.net/network-manager/+bug/264691]("https://bugs.launchpad.net/network-manager/+bug/264691")

---

### Post by uaaquarius on 2010-11-23
Hi,

you might want to try out Werner Jaeger's PPA:
[https://launchpad.net/~werner-jaeger/+archive/ppa-werner-vpn/+packages](https://launchpad.net/~werner-jaeger/+archive/ppa-werner-vpn/+packages)
As Werner [states]("https://bugs.launchpad.net/network-manager/+bug/264691/comments/20") you need to install all 3 packages.

Best regards

---


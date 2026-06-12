---
title: "Do I really need Firestarter with Bittorrent if I use a router?"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by samuraiCat on 2007-07-12
Hi, everyone. Newbie question for you: Do I really need Firestarter installed if I have a router? My Belkin has its own firewall, and the only time I will be doing any file sharing is to use BitTorrent or rTorrent. Since that one port would be forwarded outside Firestarter anyway, do I really need it? Thanks!

---

### Post by AegisTalons on 2007-07-12
Go to [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") and see for yourself if you need it. From my own experience almost all ports are closed or in stealth mode (Closed and not responding). For me, thats good enough. From what I read, you really only need Firestarter if you want to forward ports. Plus your behind a router with a firewall. But check out Shields up yourself and you decide. Your computer, you know.

---

### Post by az on 2007-07-12
> **AegisTalons said:**
> Go to [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") and see for yourself if you need it. From my own experience almost all ports are closed or in stealth mode (Closed and not responding). For me, thats good enough. From what I read, you really only need Firestarter if you want to forward ports. Plus your behind a router with a firewall. But check out Shields up yourself and you decide. Your computer, you know.

You can postscan yourself using the network-tools utility.

Stealth mode is a joke.  If you are completely invisible, how does Shields Up konw what IP address to scan?  Sounds like a false sense of security to me....

Basically, it's not what your firewall is doing that is providing you with security, it's what your computer is doing to comprimise it.  If you have not installed anything that is listening to the network, you are not vulnerable.  If you have installed something that needs to talk to the network, you will need to "open up" those ports on your firewall anyway...

> **samuraiCat said:**
> Hi, everyone. Newbie question for you: Do I really need Firestarter installed if I have a router? My Belkin has its own firewall, and the only time I will be doing any file sharing is to use BitTorrent or rTorrent. Since that one port would be forwarded outside Firestarter anyway, do I really need it? Thanks!

No, you don't need firestarter.  You wouldn't need firestarter even if you were directly connected to the internet.

---

### Post by samuraiCat on 2007-07-12
> No, you don't need firestarter.  You wouldn't need firestarter even if you were directly connected to the internet.

Thanks for the reply. Why was Firestarted developed, then? That sounds like a lot of work for software that is ultimately moot.

---

### Post by t4thfavor on 2007-07-12
Its developed for people who are paranoid, and want to explicitly deny contact to their machine, and those who want an easier way to set up a nat/ICS box. That is basically all.
All firestarter is is an easier front end for iptables, which basially all linux distros come with anyways. 

I would say unless you have all kinds of services running that open ports, you should be fine with the default rules and a router.

---

### Post by AegisTalons on 2007-07-12
> **az said:**
> Stealth mode is a joke.  If you are completely invisible, how does Shields Up konw what IP address to scan?  Sounds like a false sense of security to me.....

Shields Up pings and does some other stuff. You initiate the service, so it knows your IP address. It goes through all the ports, and sees if they are open, closed, or in "stealth" mode. For linux, like you said, you don't really need to worry to much, because most ports are closed to begin with. If you are paranoid, install Firestarter. Shields Up is just a tool to help you understand exactly what ports are open and closed. 

Shields Up was shown on The Screensavers and Call for Help when those shows were still running and still quality shows.

---

### Post by az on 2007-07-13
> **AegisTalons said:**
> Shields Up pings and does some other stuff. You initiate the service, so it knows your IP address

So, unless you do not browse the internet, or otherwise do not connect to any other computer, you are *never* invisible on the net.  Stealth mode is a joke, a false sense of security.

> **AegisTalons said:**
> 
....

Shields Up was shown on The Screensavers and Call for Help when those shows were still running and still quality shows.

I've also seen adds for a DVD rewinder and weight-loss caplets made out of grapefruits....

---


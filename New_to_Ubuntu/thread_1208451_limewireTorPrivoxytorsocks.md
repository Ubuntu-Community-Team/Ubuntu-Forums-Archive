---
title: "limewire/Tor/Privoxy/torsocks"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by Stan% on 2009-07-09
I'm no expert but......

The following seems to get limewire to run through a socks proxy.

Install Tor, Privoxy, and Torsocks.

Open a terminal and type # (case matters)

This will socksify and open limewire.

In limewire5 go to tools> options> advanced> super really advanced> proxy and set....
    
socksv5 (v4 may work too)
Proxy: localhost Port 9050

It seems to work for me. I don't know any way to verify it. You may have to socksify limewire each time you open limewire.

Anybody in the know please critique this post.

---

### Post by Stan% on 2009-07-09
May two ## characters  are needed...  

##

If this doesn't work it's **tsocks limewire**

---

### Post by Stan% on 2009-07-09
Hmmmmmmm

Someone instruct me on how to do code boxes.

---

### Post by lovinglinux on 2009-07-09
> **Stan% said:**
> Anybody in the know please critique this post.

From: [http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29#Etiquette](http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29#Etiquette)

> **Etiquette**

Because of its inherent anonymity, the traditional practices that network operators use to curb abuse may be insufficient with regard to connections coming from a Tor network. Tor has some features intended to reduce this problem, both from the perspective of exit node operators and third party sites.

Exit nodes each maintain an exit policy of what traffic is and is not permitted to leave Tor network through that node. It is possible to prevent most major abuses of Tor network using a combination of addresses and ports. Potential abuses include:

**Bandwidth hogging**
    [COLOR="Red"]It is considered impolite to transfer massive amounts of data across the Tor network &#8211; the onion routers are run by volunteers using their own bandwidth at their own cost.[/COLOR]

**BitTorrent**
    [COLOR="Red"]Due to the high bandwidth usage caused by the use of this protocol, it is considered impolite and inappropriate to use the Tor network for BitTorrent transfers. By default, the Tor exit policy blocks the standard BitTorrent ports.[/COLOR]

**Spam**
    The default Tor exit policy prevents connections to port 25, preventing people from sending spam directly from the Tor network.

**Anonymous users**
    The Tor project attempts to ensure that websites that wish to set different access policies for users visiting through Tor can do so. 

---


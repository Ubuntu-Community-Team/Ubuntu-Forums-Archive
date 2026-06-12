---
title: "Setting up a proxy for Ekiga/Empathy"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by jdpipe on 2008-11-24
Hi all

I have had no luck getting a SIP connection through my home firewall, NAT, ADSL ISP, etc.

On the assumption that I can only initiate outgoing connections, is there some kind of *proxy server* software that I can set up on a remote linux server so that I will then be able to use Ekiga and Empathy to make voice and video calls successfully?

I have a remote linux server with a static IP address, and I can install things on it as required.

Suggestions much appreciated.

Cheers
JP

---

### Post by jonobr on 2009-01-26
Using the Session intiation protocol through a NAT requres supports specifc for that setup.

You need access to a Stun server , I think xten provide access to one, however, SIP with Nats is always tricky

---

### Post by jdpipe on 2009-01-26
What about setting up a SOCKS server, would that work OK for SIP with Empathy/Telepathy?

---

### Post by jonobr on 2009-01-27
I believe SOCKS V5 supports it, 

The trick and problem with employing SIP through a NAT,

The NAT will change the ip addressing of the source and desitination packets.
No SIP aware NATs will not know they need to change information within the body of the message also which messes up the exchange.

I havent setup socks myself, but I think it will work.

---

### Post by jdpipe on 2009-01-27
I think that SOCKS could be the solution here, but I haven't managed to find anyone yet with tips on how to set it up correctly for SIP connections.

---

### Post by Brandon Williams on 2010-01-29
With VoIP, it's not usually the SIP transaction (used for session establishment) that has NAT trouble, but rather the RTP stream (used for content transfer). Some important information about the NAT must be provided to the SIP server so that the peers can establish end-to-end RTP connectivity. Usually, RTP will be transmitted over UDP.

You might be able to make SOCKS work for this purpose if you have a SOCKS mechanism that can relay UDP. This won't be true if, for example, you use ssh to open a SOCKS proxy tunnel to a remote machine. There might be some other SOCKS proxy that will handle it, though. That said, it's not enough to be able to get the packets over there, you also need to have some way to tell SIP the necessary details. Since this isn't a standard way to handle SIP/RTP, most client software won't be able to do it.

If you have a typical home internet gateway, then it does what is called symetric NAT. This means that every connection on your internal machine has its own NAT port mapping. Ekiga does not support this. However, [this link](http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router) explains how to reconfigure your NAT gateway to get a "partial cone" (a.k.a. port restricted) NAT configuration. With a partial cone NAT configuration, ekiga will use STUN (which was referenced in a previous reply).

I can't find support for SIP-based VoIP in either empathy or pidgin. Maybe I'm not looking in the right place for it. I've never been able to figure out how to get empathy to work for any protocol where a proxy is required, so I usually use pidgin. If all you're looking for is a way to make voice calls over the internet and it's not important for those calls to use SIP/RTP, then I suggest that you use pidgin, because it has the most complete proxy support implementation of the three programs (ekiga, empathy, pidgin). If you want to make peer-to-peer connections for voice without having to reconfigure your NAT gateway, then you will probably want to use a TURN server. Pidgin supports this. I'm not aware of any publically available TURN servers, though. I use pidgin for jabber/gtalk communication via an SSH SOCKS proxy, and I'm pretty sure that you can configure it to handle voice chats over jabber/gtalk.

---

### Post by Brandon Williams on 2010-01-29
I just found telepathy-sofiasip for adding SIP support to empathy. The configuration settings dialog indicates that STUN is supported (which should mean that partial cone NAT is, too). I then found pidgin-sipe, which provides SIP support for pidgin. Pidgin and empathy both support SIMPLE, which will work with a partial cone configuration for ekiga.net according to [this link](http://eugenia.gnomefiles.org/2007/05/22/sipsimple-configuration-on-pidgin/).

I also just happened upon [this site](http://numb.viagenie.ca/), which provides a public STUN/TURN server. I haven't used it and don't know anything else about it. Also, I don't think either ekiga or empathy supports TURN; pidgin does, but I don't know how well it works. Using TURN could allow you to avoid having to reconfigure your NAT gateway.

---


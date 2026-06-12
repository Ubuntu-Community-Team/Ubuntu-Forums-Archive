---
title: "Protection against Poisoning"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by defec8ing on 2007-09-11
I've been looking into security issues on this forum and elsewhere, and I am slightly concerned at how easy it is to view information on my network.  Just from experimenting for a few hours this evening, it would seem that programs such as "airdump", "ethereal" and "ettercap"  mean almost anything is up for grabs on my company's network and probably anyone else's... If someone were to use these tools against my network, would I have any way of knowing?  Can someone really hide their comp's id to such an extent that I can't detect if they are a computer that has every right to access my network, or if they are just some malicious person hoping to read confidential company emails?  Is there software that I can obtain to block and alert me to such attacks?  Can I turn the tables on them and find out who they are as they preform the attack so that I can report them?

---

### Post by kidders on 2007-09-12
Hi there,

> **defec8ing said:**
> If someone were to use these tools against my network, would I have any way of knowing?No.

> **defec8ing said:**
> Can someone really hide their comp's id to such an extent that I can't detect if they are a computer that has every right to access my network, or if they are just some malicious person hoping to read confidential company emails? I'm not entirely sure how you would distinguish between the two, even if an attacker made no attempt to conceal his computer's identity. In any case, getting hold of an identifier of some kind (eg a MAC address) belonging to an unauthorised user wouldn't normally give you any useful information.

> **defec8ing said:**
> Is there software that I can obtain to block and alert me to such attacks? That depends on what kind of attacks you're referring to.

> **defec8ing said:**
> Can I turn the tables on them and find out who they are as they preform the attack so that I can report them?No.

Out of interest, what kind of wireless network do you have?

---

### Post by robert_pectol on 2007-09-12
> **defec8ing said:**
> I've been looking into security issues on this forum and elsewhere, and I am slightly concerned at how easy it is to view information on my network.  Just from experimenting for a few hours this evening, it would seem that programs such as "airdump", "ethereal" and "ettercap"  mean almost anything is up for grabs on my company's network and probably anyone else's...
If the bad guy has physical access to your network (either via wire or wireless), then yes.  It's all up for grabs!  However, there is something that can be used to thwart this.  It's called encryption.  Encrypted packets contain no useful data in their present form.  It takes a lot of packets, a lot of time, a lot of processing power, and the right tools to be able to do anything useful with them.

> **defec8ing said:**
> If someone were to use these tools against my network, would I have any way of knowing?  Can someone really hide their comp's id to such an extent that I can't detect if they are a computer that has every right to access my network, or if they are just some malicious person hoping to read confidential company emails? Is there software that I can obtain to block and alert me to such attacks?
Yes, there are tools available that can assist you in discovering unauthorized machines and/or packet sniffers on your network, AntiSniff being one of the better ones out there.

> **defec8ing said:**
> Can I turn the tables on them and find out who they are as they preform the attack so that I can report them?
Possibly.  Especially if you can use a tool such as AntiSniff to first uncover the fact that there is a sniffer on your network, you might be able to associate the device with a user.  This would be more likely on a wired device than a wireless one though.

The first thing I would do is get rid of all wireless access to the, "inner" company network or LAN, period.  This involves periodic checks with a WiFi scanner to make sure there aren't any, "rogue" access points that can mysteriously show up on your network.  Second, use encryption (IPSEC, SSL, etc.) for connections that pass sensitive data.  Doing those 2 things will severely limit both the number of attack vectors and the usefulness of any data that might be sniffed by a miscreant.

Although the world of networking can be a scary place where bad things happen, there are simple things that can be done, and good tools that can make it a much safer place so don't despair too much!

---

### Post by defec8ing on 2007-09-13
Its a wireless router which the computers connetct to.  I'm only able to encrypt with WEP because two of my PC's are of an age that they can't seem to handle WPA.

The kind of attacks I'm talking about is something called ARP poisoning that I've been reading about- is it at all possible for me to detect that a computer is masquerading as a computer "in the link" as it were, intercepting all of my emails, print-jobs and internal messaging?

---

### Post by robert_pectol on 2007-09-13
> **defec8ing said:**
> Its a wireless router which the computers connetct to.
If you're serious about security, do NOT use wireless on a corporate LAN!

> **defec8ing said:**
> The kind of attacks I'm talking about is something called ARP poisoning that I've been reading about
Yes, very familliar with ARP poisining.  After sniffing on the network, the attacker selects a victim or victims and puts himself, "in between" them and the host(s) they are communicating with.  It's commonly referred to as a man-in-the-middle (or MITM) attack.  This is accomplished via ARP poisining.

> **defec8ing said:**
> is it at all possible for me to detect that a computer is masquerading as a computer "in the link" as it were, intercepting all of my emails, print-jobs and internal messaging?
Again, yes.  There are tools available to assist in discovering such attacks.  Among these are AntiSniff, which I previously mentioned, and Arpwatch.  You might want to do some Googling a bit.  Try the search terms, "detect ARP poisining" and do some reading.  Good luck.

---


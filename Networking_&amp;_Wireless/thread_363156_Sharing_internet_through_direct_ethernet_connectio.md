---
title: "Sharing internet through direct ethernet connection"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Roma_emu on 2007-02-16
Hello,

I'm trying to share my ADSL internet connection to another computer in my house. This is how the "network" is set up:

phone line <--phone cable--> ADSL modem <--ethernet cable--> Ubuntu PC <--ethernet crossover cable--> Windows 98SE PC

The Ubuntu PC (this one) has two network cards; the first one (eth0) connects to the modem and the second one (eth2) connects to the other PC. I connect to the internet through PPPoE, using pppoeconf/pon/poff.

I'd like some instructions on how to set up Ubuntu to share the internet connection with another PC. or perhaps a link to a guide. I think it doesn't matter which OS is in the other side, does it? (Anyway, if someone could help me with setting up the Win98 PC to receive internet from this one, I'd be grateful too...)

---

### Post by koenn on 2007-02-16
your question is basically the same as this one:
[http://ubuntuforums.org/showthread.php?t=358169](http://ubuntuforums.org/showthread.php?t=358169)

You can start with post #2 in that thread, then come back if something ain't working right.

---

### Post by Roma_emu on 2007-02-19
Thanks for the reply.

I did what was told in the topic, and it worked partially. The Windows computer is behaving very erratically:

A few sites - only got two of them working so far - open up correctly. Those were Google (and Gmail) and Globo.com.

I can ping some other sites, but they don't open in IE.

Some other sites don't open in IE, and don't reply to my ping.

Note that they don't give me Site Not Found errors in IE - it says "site found" for a short moment in the status bar (indicating that the site exists), but it keeps loading, and loading, and loading, and nothing shows up.

I set the DNS hosts manually, in one of the network settings tab, to be the same that is set here in Ubuntu. In order to do it I also had to give it a name (which I invented) for a host and a domain.

I know it's more of a Windows question now than a Ubuntu question, but I don't know where else to ask... could you help me please? :( 

Obs: I set eth2 in this computer as fixed IP 192.168.0.1 with subnet mask 255.255.255.0. and no gateway. In the other computer, I set it as IP 192.168.0.2 with subnet mask 255.255.255.0, gateway 192.168.0.1 and the two DNS IPs that I have in my Network Settings here in Ubuntu (I don't know where it got those from).

---


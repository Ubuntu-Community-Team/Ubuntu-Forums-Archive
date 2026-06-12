---
title: "Dual NIC server as a bandwidth monitor?"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by aberry9036 on 2008-02-14
Hi, I've got a pretty specific task that I want to do with linux, seeing as every other option is obscenely expensive and I'm pretty sure it's possible with linux. I want to install an old server with Ubuntu Server edition and try to install it between our ISP's presentation and our router.
Basically we've got a 16 meg fibre presentation plumbed in to our building which is then fed in to our router which we use for bandwidth limitation etc for our clients, we basically split off the 16 meg in to a few different partitions. The main problem though is that COLT, our ISP, have been pissing about and we're not sure about the bandwidth we're actually getting from them on a regular basis. Seeing as there are so many different partitions, it's very difficult to install something to monitor bandwidth after leaving our router, however we could measure it between the router and ISP presentation. 

I've used linux, mostly Ubuntu, a fair bit before and I can get by on command line stuff, though I might opt to apt-get install ubuntu-desktop to save time! What I wanted to know is what would I use? After a bit of reading it seems I can use iptables to do this but how would the data be presented afterwards? Are there any webapps or anything I can install that can make the results easier to use/present, rather than having to drag data on to a spreadsheet myself etc. Also I'm pretty much a novice with iptables, barely know anything about them so any help or advice on how to go about setting this up would also be greatly aprreciated :)

Oh and also does anyone know if this will bring in any noticeable lag in to the circuit?

---

### Post by netztier on 2008-02-14
It could. However - does that router of yours support SNMP? 

If yes, then it already has traffic counters ready for you, you just have to collect them.

Configure the router ro respond to SNMP queries of an internal server of yours. On that machine, install some [RRDtool]("http://oss.oetiker.ch/rrdtool/") based app like [MRTG]("http://www.mrtg.com/") or even [Cacti]("http://cacti.net/") (which is available in the universe repository) to poll the counter values at regular intervals and to graph them up. No need for a "bump in the wire" and fears about increased latency and the likes.

However: a 16Mbit/s connection can already be a "Large Fat Network" (LFN), especially when you're connecting to overseas hosts and services, where RoundTripTimes of 100ms and more become very common. A single TCP connection to such a remote host will never reach the full 16Mbit/s without some optimization of window size an the likes. Read up about LFNs, "Bandwith x Delay Product" and TCP flow control and make sure you have good numbers and data material ready before you go shoutig at your ISP.


regards

Marc

---

### Post by aberry9036 on 2008-02-14
Hi, thanks for the advice. The only reason we've been shouting at our ISP is down to *serious* differences in assigned speeds, something along the lines of struggling to reach 100k download speeds on a 1 meg partition. Funnily enough this morning our ISP have just run in very apologetically and said, due to a faulty configuration in an offsite router, the bandwidth reaching is us is 4 meg or less, not 16, so that's down to them to fix. However we'd still like to be able to check bandwidth, so we'll have to look at that SNMP setup you were talking about.

Thanks for the advice!

---

### Post by netztier on 2008-02-14
> **aberry9036 said:**
> However we'd still like to be able to check bandwidth, so we'll have to look at that SNMP setup you were talking about.


What kind of router device are we talking about here? How do actually do the bandwith/capacity split between your own customers?

If it's all done on the router itself and it's working with (virtual) sub-interfaces per customer etc, there's a good chance that you could get a one-off solution. With the router maintaining per-interface traffic counters (ifInOctets, ifOutOctets, ifInErrors, ifOutErrors etc.), you'll just need to collect the data at a single place, and RRDtool acting behind the scenes on a Cacti machine will present you with great graphs. These can come in very handy when discussing and monitoring SLAs with customers.

If your LAN's switches are also SNMP-enabled, you can (and should) also collect individual stats for each switch port and especially up/downlink ports between switches.  This will help a great deal in that you can spot problems before they actually occur: if you observe a >3Mbps increase per month on a 100Mbps link that is already at 75% capacity, you'll know that you'll have to upgrade that Switch-to-Core uplink within half a year... 

Sorry, I'm getting carried away - it's been a while since I was able to write about network management here... :-)

best regards

Marc

---


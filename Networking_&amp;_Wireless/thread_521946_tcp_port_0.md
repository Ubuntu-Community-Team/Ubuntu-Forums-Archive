---
title: "tcp port 0"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by rit on 2007-08-09
Yo Ubuntu Forums, first time poster, long time something-er.

I wasn't sure where to post this or who to ask, and after asking several buddies and co-workers and not really getting anywhere, I decided to give this a shot.  Let's cut to the chase (and I'll try to be clear, sometimes I'm not quite as crystal as people would like):

Using 7.04 on my desktop, I've got a switch and a consumer grade Netgear router between me and the big bad world, and I'm using firestarter on the desktop, because I'm exceedingly paranoid about intrusions.  Last night and today, Firestarter logged a handful of TCP port 0 access attempts from various sources, some of which turn out to be computers and/or devices belonging to my ISP, and others who whois reports are various artists.

Logically, this freaked me out.  As far as I understand it, the router on the border should just drop incoming attempts.  From what I understand, the only reason I'd ever see incoming port 0 traffic is if someone were scanning my network, or trying to get clues as to what OS computers on my network are running.

I ended up powering down the box while I was at work (there's a fan starting to make a bearing noise also as of last night, so I'm thinking it will fail soon... oh when it rains...), and dropping a different Linksys router I had kicking around in place to see if that made any difference at all, and so far I haven't seen anything shady like that, which obviously could be any of several reasons, but I guess my question to all of you who have read this far is:

Should I be worried?

I mean, it didn't seem like anyone got in.  Running "who" didn't turn up any extra logins to the box, and I don't see anything obviously messed with. I don't have any ports open/listening at either the router or Firestarter, so I'm just completely confused as to how this traffic appeared on the private network from public IPs, from my point of view unsolicited.

To sum:

Any way to tell easily if someone managed to get into the local box?
Any way to tell if this is Firestarter misinterpreting traffic?
Just what would anybody be trying to attack on tcp port 0?


I'm sorry if I am breaking any forum etiquette or if I'm posting in the wrong place, but like I said, first time poster, and even though I've been a computer user for a long time, for some reason (which blows the mind of everyone I tell), I pretty much never actually post to forums for help.  Maybe I'm antisocial?

Thanks in advance

p.s. anyone who wants to see the txt file dump from firestarter, let me know and I'll post it.

---

### Post by kidders on 2007-08-11
Hi there & welcome,

Although it's hard to be completely sure without a little more information about your network traffic, it sounds as though paranoia has gotten the better of you hehe.

Just a few random observations...
[LIST]
[*]Running multiple firewalls isn't always a good plan. Aside from making legitimate use of your network unnecessarily difficult for yourself, you can cause problems if all your firewalls aren't correctly configured ... such as routing anomalies, difficulty determining the true origins & destinations of packets & odd network traffic. Also, it's surprisingly easy for malicious traffic to fall between two stools & get onto your LAN.
[*]Depending on how you look at it, TCP port 0 doesn't really exist. Normally, traffic on port 0 is simply dynamically reallocated to a higher port number ... something which is in no way unusual or worrying.
[*]Unsolicited attempts to probe or access your network are nothing to be too concerned about either. Port scans, ICMP traffic, attempts to log into things like externally accessible SSH servers, and so on often occur with very high frequency, and are nothing to worry about on a properly configured Linux box with a properly configured firewall.
[*]The probability that you will ever detect an intrusion by typing "who" is extremely low. You would have to leave a terminal server of some kind, with *exceptionally* poor password protection, open to the outside world to allow an unauthorised login to your box.[/LIST]> **rit said:**
> Any way to tell easily if someone managed to get into the local box?Not unless you already have some kind of intrusion detection regime.

> **rit said:**
> Any way to tell if this is Firestarter misinterpreting traffic?Not really. But it does take a fair degree of knowledge to know what tools like that are telling you, sometimes.

> **rit said:**
> Just what would anybody be trying to attack on tcp port 0?Some low-level attacks aimed at triggering buffer overflows or causing DoS issues might involve port 0, I suppose. It's important to underline, however, that there is a world of a difference between simply receiving unsolicited network traffic and being attacked.


I hope this is of some help.

---

### Post by rit on 2007-08-13
Thanks very much!  I appreciate you humoring my paranoia.  It is still very curious to me that any traffic of an unsolicited nature could make it past the first firewall (the router) to begin with, since the policy should be 'drop' since we have no ports open or forwarded.  At any rate, it has stopped, so that's positive!

Thanks again!

---

### Post by kidders on 2007-08-13
> **rit said:**
> Thanks very much!  I appreciate you humoring my paranoia.Oh dear... I didn't really mean it like that. You gotta check these things out... to be sure you have your head wrapped around what's happening on your own network. :-)

> **rit said:**
> It is still very curious to me that any traffic of an unsolicited nature could make it past the first firewall (the router) to begin with, since the policy should be 'drop' since we have no ports open or forwarded.  At any rate, it has stopped, so that's positive!You may find that what you observed was normal for whatever was running on your network at the time, although to explain any further than that would be a little time-consuming ... so I won't, unless you'd like me to hehe.

If you continue to be concerned though, you should certainly post back. If you're interested in someone's opinion other than mine, try posting a new thread ... I promise I won't answer it hehe. It's important to feel safe when using your computer, so I certainly wouldn't expect you to blindly take my word for it that you're probably okay.

Having said that, I did feel I should try to reassure you though.

---


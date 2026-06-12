---
title: "[SOLVED] Inline Virus Scanning"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by kambrik on 2007-07-25
I am wanting to put a linux box in between our router and our hub to filter out any harmful material that might be passing to our internal network.  I was wondering what would be my options.

Thanks

---

### Post by kidders on 2007-07-27
Hi there,

Although what you're describing is possible, I would strongly discourage it, for three main reasons:
[LIST]
[*]**Performance:** Checking everything for harmful code would have a significant performance impact. As a "for instance", Samba clients can very easily get fed up waiting for large files to be scanned before being handed over, and can misbehave.
[*]**Coverage:** It would be very difficult to ensure 100% coverage, without damaging usability, especially where web browsing is concerned.
[*]**Bad practice:** Such schemes encourage complacency, which essentially guarantees failure.[/LIST]In practice, you see, another way of writing that list might be...
[LIST]
[*]**Performance:** Encourage users to try to defeat prudent safety measures, so they can get access to what they want more quickly.
[*]**Coverage:** Make users resent your security precautions, rather than thanking you for them, by denying them access to things you can't scan properly (eg streaming media).
[*]**Bad practice:** Magnify risks associated with the use of things like USB disks on networked PCs, because people don't feel like they have to act with a healthy sense of suspicion.[/LIST]If you're interested in playing with the idea anyway, you will find that many applications know how to talk to thing like virus scanners (most often ClamAV). Off the top of my head, examples include Dansguardian, Samba & Postfix (for web browsing, file sharing & mail exchange).

In general, asynchronous network communications respond best to centralised checks, mostly because you can spend as long as you like scanning & re-scanning things. The most commonplace example is email, although how to approach scanning/filtering it very much depends on the ballpark your mail delivery volume is in. Real-time network communication is much harder to deal with satisfactorily. In the end, individual client-side utilities are invariably necessary to plug little gaps in coverage, which is why, all things considered, I prefaced my post the way I did.

I hope that helps.

---


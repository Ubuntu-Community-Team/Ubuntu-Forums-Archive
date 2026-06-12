---
title: "SSL Inspection for use with DansGuardian"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by 13l-jason on 2014-02-09
I hope this is the right place to ask this question.  I'm setting up DansGuardian to help keep my kids in line while on the Internet.  I've got it working great for HTTP, but as soon as I try blocking Google searches based on the URL, it just allows everything through.  I block https traffic, but I'd rather allow that and just block the content.

Here's what I'm using
Dan's Guardian v2.10.1.1
Tiny Proxy v1.8.3  (I figure I'll have to change to something like SquidProxy for what I'm looking for)
My server is actually running on a Raspberry Pi (Linux raspberrypi 3.10.25+ #622 PREEMPT Fri Jan 3 18:41:00 GMT 2014 armv6l GNU/Linux)
My clients are all Ubuntu 13.10

I'm assuming the only way to do this is via SSL inspection, where the clients use a my servers certificate, so it can pick up the request and decrypt it, pass it on to DansGuardian, which will filter it and pass it on to the proxy server at which point it gets encrypted with the destination's certificate.

Thanks in advance for the help.

---

### Post by CharlesA on 2014-02-09
The whole point of SSL is to prevent a man in the middle attack, which is exactly what this sounds like.

What would you kids be accessing over https that they would not be accessing over http? This sounds like trying to sold a parental problem with technology.

---

### Post by 13l-jason on 2014-02-10
It is very much like a man in the middle attack, and I understand the purpose of SSL.  Of course, it's not an attack, this is my own network, with my own equipment.  This isn't a parenting issue it's a technology issue, and of course, I'm going to use technology to solve it.

---

### Post by CharlesA on 2014-02-10
The thing is, something who wants to do the same thing for not so benign reasons could also find the steps required to accomplish what you want.

I do not believe there should be a need to sniff HTTPS traffic just to limit access, and I'm sure there are other forums out there that will gladly help you but I do not believe this is an appropriate thing to have posted here.

Thread closed.

---


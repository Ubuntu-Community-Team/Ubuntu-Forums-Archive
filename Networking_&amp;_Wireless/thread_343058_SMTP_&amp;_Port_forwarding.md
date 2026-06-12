---
title: "SMTP &amp; Port forwarding"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by code-breaker on 2007-01-20
I am a networking noob with a linksys WCG200. I haven't been able to send mail via smtp since I got it, I figured this is because I use the router's firewall. So I configured the router to set up some port-forwarding. This works, but I have a few questions.

I enter the port range to forward and the IP to forward to, but it also asks me to choose a protocol, the options being tcp, udp, or both. I chose both, and am able to send mail, but is this right? 

Why should I need port forwarding if I am initiating the transaction (by sending a message)?

Thirdly, is this a security concern? 

Thanks.

---

### Post by kidders on 2007-01-21
Hi there,

If you are initiating an outgoing connection to a remote SMTP server, you won't benefit from enabling port forwarding. The only way your router could be preventing you from contacting a mail gateway is by blocking *outgoing* TCP connections on port 25, which isn't usually done by domestic hardware.

Are you sure there isn't something else going on?

---

### Post by code-breaker on 2007-01-21
Well, I have no idea. I am now able to send mail. I turned off port forwarding and it still works (as you indicate it should). I have no idea why I was unable to send, but it was with two different mail servers, and they both spontaneously started working at the same time, right when I enabled port forwarding. As I said forwarding is now off and I can still send mail, so I guess I'm back in business, although I'm baffled as to what the problem was. Thanks for the reply.

---


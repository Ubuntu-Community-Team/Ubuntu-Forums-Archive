---
title: "How gufw and firewalls work"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by greenarrow on 2010-02-20
Hey guys, I just installed Ubuntu Netbook Remix on my Acer Aspire One.  I've always used Fedora on my home computer, but the UNR is just way easier to get working on the netbook.  I was wondering though, how does default deny setting work in GUFW?  Would the ruleset be something like "block in all, allow out all"?  If all I wanted to do on my netbook would be to access the web, and get updates for the OS, what would the ruleset look like? Thanks in advance.

---

### Post by manny43 on 2010-02-20
Deny all incoming traffic and you still can get updates and also access the web.

---

### Post by jpl888 on 2010-02-20
I think UFW is set up like all standard firewalls by default i.e. as you say allow all connections out but no connections in.

---

### Post by J V on 2010-02-20
ufw is off by default... you probably don't need a firewall though: nothing is listening on linux so unless you install a malicious program (and then you have bigger fish to fry), don't worry about it...

---

### Post by jpl888 on 2010-02-20
> **J V said:**
> ufw is off by default... you probably don't need a firewall though: nothing is listening on linux so unless you install a malicious program (and then you have bigger fish to fry), don't worry about it...

I'm sorry guy but "nothing is listening on linux". Come on it depends on what you have installed. Here is my netstat -l output i.e. what is "listening" on my machine.

```
tcp        0      0 *:domain                *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 tux:ipp                 *:*                     LISTEN     
tcp        0      0 *:5500                  *:*                     LISTEN     
tcp6       0      0 [::]:domain             [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:domain                *:*                                
udp        0      0 *:42043                 *:*                                
udp        0      0 *:bootps                *:*                                
udp6       0      0 [::]:domain             [::]:*                             

```

---

### Post by J V on 2010-02-20
compared to windows: thats nothing :)

point is, only programs that need a port are getting it, no need for firewall without special server software, and if you have that you probably know how to configure ufw :)

---

### Post by jpl888 on 2010-02-20
Well I think better safe than sorry even if you don't think there is anything listening.

At least it's another hoop for the baddies to jump through that will make your machine that little bit lest enticing.

---

### Post by J V on 2010-02-20
The point is you can't just "turn on" the firewall, you have to configure it for every program that has internet access... same as windows ones (only they have cool guis that ask you whenever something wants access)

So turn it on: tweak a few settings: it won't matter... you'll need to add every program you want to it. waste o time on average machine if you ask me...

---

### Post by jpl888 on 2010-02-20
Well I prefer an access by exception policy than let it all through cos I don't think there's anything that might give me a problem.

But hey we are all different.

Vive la difference!

---


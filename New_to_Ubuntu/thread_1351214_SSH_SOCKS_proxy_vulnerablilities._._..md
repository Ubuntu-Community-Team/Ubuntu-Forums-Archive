---
title: "SSH SOCKS proxy vulnerablilities. . ."
date: 2009-12-10
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-12-10
Hi!

When I am on a strange network, I usually tunnel all of my web traffic through an SSH tunnel with:

```
ssh -D 8000 my.ubuntu.server
```

Then I tell Firefox to use localhost:8000 as a SOCKS 5 proxy, and I set network.proxy.socks.remote_dns to true in about:config.

I guess the real question would be. . . Is this really secure?  I use private key authentication, and logging in without a password is disabled.  How might an attacker go about detecting my traffic?  Would a URL filter/DNS server/packet sniffer be able to detect my traffic/get my passwords?  I'm kind of paranoid when it comes to strange networks, but sometimes there is no other option.

Any advice would be appreciated.
Thanks!

---

### Post by jbrown96 on 2009-12-10
You need to make sure that your DNS requests go over that proxy. Most of the time this is a separate configuration. If you don't do this, then evesdroppers would not be able to read the traffic, but they could tell which websites you go to. 


SSH is very secure, and there's currently no big vulnerabilities. Who would want to intercept your traffic? Anything that's private on the internet is already encrypted (using ssl, which is likely more secure than ssh), and if it's not, then it can be intercepted at your proxy. No one would take the time to break ssh encryption. [This]("http://xkcd.com/538/") is what would happen if someone wanted your info.

I'm a recovering paranoid encrypter. Let me tell you, it's not worth the time. No one cares about what you are doing, period.

---


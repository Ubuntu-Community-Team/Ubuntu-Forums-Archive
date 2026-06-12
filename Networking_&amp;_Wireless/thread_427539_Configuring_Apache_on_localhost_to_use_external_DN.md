---
title: "Configuring Apache on localhost to use external DNS"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by TheFuzzy0ne on 2007-04-29
Hi everyone.

I wasn't sure where to post this topic, so I posted here. If anyone can suggest a better place, please let me know. :)

I have Apache set up on my localhost as a pure development environment. No-one can access it from the outside world, not even me. I would for my development Web site to be able to access external Web sites. or more specifically, external DNS servers, so I can do DNS lookups. I'm not quite sure of the tools I need, or the steps I need to take in order to make this work.

/etc/resolv.conf is currently points to my router for DNS. I would have though this was adequate for my needs, but evidently it's not, I have installed BIND9, but I can't seem to find an easy way to configure it to work with only a couple of external DNS servers. I thought that my router would have handled the DNS itself, but it doesn't seem to be the case.

If anyone can point me in the right direction, I would really appreciate it. Over the past few days, I have been Google's biggest customer, and I've gotten nowhere.

Many thanks in advance.

Daz.

---

### Post by Thomi on 2007-04-29
If your browser could make it to this website, you almost certainly CAN access external DNS servers

What exactly do you mean when you say "access external DNS servers".. How do you plan on accessing them?

Try the following to verify that you can access a DNS server:

nslookup google.com

You should get the A record of the stated domain listed.


You shouldn't need to install the Bind9 package unless you want to do one of the following:

 * install a caching DNS server
 * Install your own DNS server, for example to create or manage your own TLD zones.

HTH!

---

### Post by TheFuzzy0ne on 2007-04-29
Hi Thomi.

Thanks for the swift reply.

I am simply trying to achieve a mail exchange lookup through PHP. It works on my Web site (hosted somewhere in the US), but I can't get it to work from my local development Web site. The query times out. I assumed that there's something that I need to do with Apache in order to get it to do the lookup on an external DNS server, rather than trying to do it locally (at least I "think" that's what it's trying to do).

The nslookup works just as expected. I suspected that I didn't need BIND9, as I don't want to run a full blown DNS server, but I was getting desperate and just started guessing as I couldn't find anything comprehensive on the Web. 

I am trying to use PHP's getmxrr() function to check email domains to confirm they are valid. The strange thing is that I can resolve and connect to external with no problem, and send them using my localhost development Web site as a proxy. The only thing I can't seem to do, is query external DNS servers. :confused: 

I think this may not be the place to be asking for help, as it might actually be an issue with Apache's set up, as opposed to a problem with Kubuntu's set up as I thought originally. 

I appreciate your assistance so far, but in fairness, if I need to ask elsewhere, please feel free to tell me to do so. Truth be told, I like the friendly people on this site more than others. Hehe.

Best wishes.

Daz.

---

### Post by TheFuzzy0ne on 2007-04-29
OK, and update. I've just discovered that 
[PHP]
gethostbynamel();
[/PHP]

seems to do the job. It resolves to an IP address, which is good enough for me, although I think I need to test it some more.

In the meantime, if you can suggest anything that might help with fixing my original problem, it would still be appreciated, even though I appear to have found an alternative.

Thanks again.

Daz.

---


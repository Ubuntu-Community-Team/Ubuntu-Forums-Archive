---
title: "How can I block a specific site in a domain?"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by kung fu buntu on 2008-08-13
I have a tricky problem over here...

I would like to block a specific site on a given domain, while leaving the other ones working fine.
For example, I want to block:
[hxxp://foobar.com/stuff/specificsite](hxxp://foobar.com/stuff/specificsite)
But want to access without problems:
[hxxp://foobar.com/stuff/other](hxxp://foobar.com/stuff/other)

I have to block this at an ethernet port level in iptables because my computer is working as a gateway and I want to block it for the other computer.

And if possible I would also like to block this at the user level on my computer, because I have an account... and that could end up being used as a backdoor.

BTW, it would be great if I could use regular expressions in the URLs to block.

Thanks.

---

### Post by jimv on 2008-08-13
Never set up anything in iptables, but in general I think that a rule to block [www.somesite.com/webpage](www.somesite.com/webpage) and allow [www.somesite/webpage/*](www.somesite/webpage/*) would work.

Is this a website of yours?

---

### Post by bab1 on 2008-08-13
If I understand you correctly, you want to block traffic for the others and see it yourself.  If so then you can block (restrict) traffic on the outbound interface rather than on inbound interface.

This solves where to do what you want, but does not solve your need to block specific web pages.  I don't believe iptables will do what you want.  You will need a tool that reads packet content not just the headers.  Commercially this is like [[COLOR="Magenta"]Web-Sense[/COLOR]]("http://en.wikipedia.org/wiki/Websense").  You might look for an open source equivalent.

Edit:  Just did a search on the term websense on this forum and found [COLOR="Red"]**[[COLOR="DarkOrange"]SquidGuard[/COLOR]]("http://www.squidguard.org/")**[/COLOR], a plugin for Squid Proxy.  This may be what you need.

---

### Post by kung fu buntu on 2008-08-13
> **bab1 said:**
> If I understand you correctly, you want to block traffic for the others and see it yourself.  If so then you can block (restrict) traffic on the outbound interface rather than on inbound interface.Yes, that is what I want to do. Although I didn't understand what you meant on which interface. I will block it on the interface that connects my pc with the other one.

I never used squid... but I have this idea that it's a bit complicated to use and overkill for the job, as well as consuming "some" computer resources.

I will give it a try anyway, but meanwhile I'm still open to other solutions to this problem.

BTW, I hope it works ok at DNS and IP level.

---

### Post by bab1 on 2008-08-13
Correct.  The interface is the NIC you using to connect to the other computer, NOT the one to the internet.

Your needs are NOT at the DNS or IP level.  Blocking specific websites means blocking specific [COLOR="DarkOrange"]*files*[/COLOR] to be interpreted by your browser.  It has nothing to do with IP or DNS.  You can think of it as blocking *[COLOR="Red"]**what**[/COLOR]* not [COLOR="Blue"]*[I]who*[/I][/COLOR].

---

### Post by kung fu buntu on 2008-08-13
I still don't see how I will relate squid with my secondary NIC.
Doesn't squid work on a global level?

---

### Post by bab1 on 2008-08-13
We were talking about two ideas.  IP Blocking is for an interface.  Squid is a proxy for the user.  When we are talking about Squid it really doesn't matter which NIC it is associated with.  Exclude the user specifically.

Edit:  I believe you should associate the proxy facing the internet.

---

### Post by kung fu buntu on 2008-08-13
mmhm... searching for squid lead me to [this post]("http://ubuntuforums.org/showthread.php?t=810748")
Which makes it seem that it's possible to relate an interface with squid...
And with dansguardian some interesting things become possible.
But I'll have to try all of this first...

---

### Post by bab1 on 2008-08-13
Don't forget to look at squid-guard it is specificly for what you needed.

Good luck.

---


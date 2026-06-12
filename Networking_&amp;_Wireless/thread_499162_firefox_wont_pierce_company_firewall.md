---
title: "firefox wont pierce company firewall"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by marzshadow on 2007-07-12
Feisty Fawn
The network works well.
I can see internal websites.
I can see some external websites if I use https://
When I try to connect [http://www.yahoo.com/](http://www.yahoo.com/)
I get 
"!  The conenction was reset.
The connection to the serve was reset while the page was loading."

It's the same for anyplace on the internet.

Strangely enough, the update manager works....I can browse and install packages and update the system.
If I boot the machine up in XP, things work well.  

I suspect I've got a configuration problem with my companie's firewall.  Or maybe IPv6.
Any suggestions?

Thanks
--Mark

---

### Post by tribaal on 2007-07-12
Silly idea, but does your company use an http proxy (most medium to large businesses do)?

-trib'

---

### Post by tava0002 on 2007-07-12
Yes, find out if your company uses a proxy server and make sure your browser proxy settings are correct.  If that's not it it's probably a firewall issue and you need to look at audits from it.

---

### Post by marzshadow on 2007-07-12
My company is most likely using a proxy but all of the windows machines seem to discover it automagicly.
The IS group is forbidden to support linux so I'm on my own.  I'm not going to be able to view the logs.

Any suggestions?

--mark

---

### Post by Yoooder on 2007-07-12
on a Windows machine you could try to bring up IE and poke around for it's proxy settings to see if you can scrape them from there.

Also on a windows machine, try running > tracert yahoo.com from a command prompt.  It will show all hops between your machine and the net (provided each hop has the protocol enabled).  The first one or few hops should be internal addresses, try each one as a proxy for Firefox.  I *think* it should be the last internal address, as that will be the address of the router/server closest to the intertubes.

---


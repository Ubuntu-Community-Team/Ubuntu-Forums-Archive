---
title: "iptables not dropping http traffic after using DROP command"
date: 2014-05-27
forum: Networking &amp; Wireless
---

### Post by brad23 on 2014-05-27
Hi Folks,

I'm using 11.10 Ubuntu (yes, outdated and unsupported, but I'm in the middle of a big project w/ software dependencies making it hard to upgrade at the moment).

I've set up dansguardian as a filter a laptop using privoxy as a backend and it is working very well (explicit proxy type so that I can do https filtering).  But I'm having trouble closing the loophole that allows me to simply set my browser (chromium) proxy settings to be "none", thereby circumventing the whole thing (trying to do precisely what the green text says here: [http://contentfilter.futuragts.com/wiki/doku.php?id=preventing_skipping_around&DokuWiki=4df3d177ebaa46204a39a6769ad43ed0](http://contentfilter.futuragts.com/wiki/doku.php?id=preventing_skipping_around&DokuWiki=4df3d177ebaa46204a39a6769ad43ed0)).

Here's my problem.  If I have my browser proxy set to "none" and I issue the following commands:

sudo iptables -A INPUT -p tcp --destination-port 80 -j DROP
sudo iptables -A INPUT -p tcp --destination-port 443 -j DROP

I would expect that I can't do any browsing, but I can, and everything!  It seems perhaps there's another port that is allowing http content through, or I've got the command wrong.  To be honest, I've read up on some iptables to learn a bit but I still don't know much.

If I do the same commands above except using OUTPUT, indeed everything is blocked.  But this doesn't allow anything at all when reconfiguring the browser proxy to point to my specified proxy (privoxy) connected to Dansguardian.

Unfortunately, because my Ubuntu is out of date, I cannot install Shorewall and I need to use iptables commands.

Any ideas?

Thanks in advance,
Brad

---

### Post by Lars Noodén on 2014-05-27
The INPUT chain refers to packets coming in to your machine from the outside.  So those two rules block external access to your web server not access from your web browser to external web servers.

You can see a little more of what is going on with the connections with netstat.  Open up a terminal on the side with netstat,

```

while sleep 1; do clear; netstat -ntp;done

```

then try accessing some web pages.

---

### Post by jaimerosario on 2014-07-20
you can download fwbuilder ([http://www.fwbuilder.org](http://www.fwbuilder.org)), and re-create the iptables.

---


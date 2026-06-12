---
title: "[SOLVED] can only surf one site on 7.10"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by blingo on 2007-10-31
Hello,
I've installed 7.10 on a brand new computer.
It has an onboard wired lan which i'm using.

I've discoverd that I can only surf to:

[http://www.mozilla.com/products/firefox/central.html](http://www.mozilla.com/products/firefox/central.html)

and related,

All other sites are stuck at "waiting for".
That indicates, I belive, that the sites are found.
Also each time I enter the name of a site I can see network activity on the system monitor, but just a few on all other sites.

I've looked into the stuff about ipv6 and never it was more dead than on this machine.
Also i've changed my dns, I don't think it's that.

Many thanks,

A broken link will not be given as a prize to the proud solver of this enigma.

---

### Post by johnl on 2007-10-31
To completely rule out DNS problems, have you tried visiting a site by ip address?  for example, [http://72.14.207.99/](http://72.14.207.99/) should take you to google.com.    You can also test DNS resolution on the command line using the command "resolveip example.com" to see what address your DNS is mapping example.com to.

---

### Post by blingo on 2007-10-31
it still waits:
waiting for 72.14.207.99...

I hope to install resolveip as soon as I'll have an internet connection ;)

---

### Post by blingo on 2007-12-06
It's been so long, I'll start again.

Hello,
I can only surf to the Mozila web site.

1)I don't think it's DNS becuase when in terminal, if I write ping [www.something](www.something)... it gives me it's IP very fast.

2)I've tried messing with IPV6 before and it made no diffrance. currently I've Reinstalled Ubuntu, and IPV6 is enabled.

The Firefox "finds" the sites, than hangs on "Waiting for...".
Also I'm having trouble with downloading packages, sometimes it works, sometimes it doesn't.

I'm surfing throgh a Routher with wires.

It looks much like there's a firewall blocking me. is there a builtin firewall to Ubuntu, and how to stop this?

Also I've tested several other linux distributions (Despite that Ubuntu is my favorite)  - all with the same problem.

Best Wishes and Thanks.

---


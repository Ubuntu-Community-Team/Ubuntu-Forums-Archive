---
title: "ICS connection with Windows running slowly"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by ccgnome on 2006-08-03
Hi

I use a DirecPC one way satellite link for my internet connection. I have to use a Windows XP PC for my gateway as there are no Linux drivers for the satellite card.

The Windows PC is set up for internet connecdtion sharing. It works flawlessly with two XP PCs connected to the gateway PC via my home network.

I've installed Ubuntu on another PC and am having some problems connecting to the internet via the Windows XP PC gateway.

In principle it should have been easy. Just set up a DHCP connection to the gateway from within Ubuntu.

And simple it was, with a catch. Everything works just fine except I'm getting time-outs when I connect to a site.

Sometimes the web page load fine but 95% of time I get timeouts.

I can ping the gateway PC. I can ping any web site. No problems. The DNS seems to work fine. Indeed, the fact some web pages load OK suggests the basic setup is fine.

My guess is the high satellite latency (typically 600-800ms) is causing the timeout problem. 

In a Windows system I'd fiddle with the MTU, the size of the receive window, path MTU discovery and other TCP parameters but from what I understand these are hard wired into the Kernel and Ubuntu.

Then again my diagnosis may be totally wrong and it's got nothing to do with TCP.

Any suggestions are most welcome.

Thanks

Chris

---

### Post by eXisor on 2006-08-03
It took me ages to find the simple answer to setting MTU for a DHCP setup, ie. requiring no special boot script. It was originally posted by mlonker, but is buried in a thread somewhere

[http://glasnost.beeznest.org/articles/290](http://glasnost.beeznest.org/articles/290)

---


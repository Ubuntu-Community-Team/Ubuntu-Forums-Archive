---
title: "Compressing X11 Forwarding Over Internet"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by adamjs on 2007-01-26
I have been trying to use ssh with X11 forwarding over the internet to access my Ubuntu machine from my MacBook Pro and my windows computer with Cygwin as well as some Linux machines.  I have had the experience that the graphical interface has been somewhat sluggish even though all of the connections involved are broadband.  Someone mentioned to me that there is some sort of program out there that can be used to compress the X11 forwarding that makes it much more usable over a remote connection.  Does anyone on this experience know anything more about how to do this or have any experience on the subject?
Thanks
AJS

---

### Post by lhtown on 2007-01-27
You might check over at the [http://www.k12ltsp.org/](http://www.k12ltsp.org/) or [http://www.ltsp.org/](http://www.ltsp.org/) projects or some of the related projects to see if they have done anything like that since they have similar requirements.

It seems to me like compressing and decompressing all of that would slow you down unless and even if you have a pretty fast computer. Besides, it seems like the network should handle most traffic fine.

You might check out your network. Could it be your router or one of your nic cards that is the problem? Most home routers are pretty anemic. While it might give you the advertised bandwidth, that doesn't mean it will handle the traffic quickly and without delays. You might think about adding a nic card to your computer and setting it up as a router. (I think that can be done, can't it?) Maybe you could try it with just a crossover cable?

---

### Post by lhtown on 2007-01-27
Wait a minute, you said over the INTERNET. Yeah, it would be slow.

I was thinking an home office network. You have a number of latency issues to deal with as well as likely bandwidth restrictions (unless you are on like a T1 line). I am surprised it is usable at all.

---

### Post by askreet on 2008-03-25
Google for NX NoMachine, they have a solution that is free to home users and clients are available on Mac and Windows -- it's their custom version of X11 Forwarding.

---


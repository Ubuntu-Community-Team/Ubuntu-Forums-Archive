---
title: "Is it possible to set up a proxy/router that will manage quotas of bandwith?"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by mac.ryan on 2008-02-11
I live in a community of 60+ people, and we share a single DSL connection amongst us all (not many geeks around, luckily for the bandwidth!).

One of the most critical issues is bandwidth during office hours, as people using their computers to work gets their speed sucked away by those of us who are rostered for a day off.

The problem is that our network do not have any system of bandwidth control. In other terms: given a connection speed of 100, if there are 2 computers online they will go at 50 each, if they are 10, they will go at speed 10.

Ideally, I would like to set up a machine as proxy/router for our LAN, and I would like to programme it in an "intelligent way", with flexible rules like for example:
a) during office hours, share 80% of the bandwidth with the office computers, and share the remaining 20% amongst all the other computers.
b) any given user can't download more than 100 Mb over a period of 24 hours
c) ...

I have no experience in managing servers, but I am a quick learner. Can somebody point me in the right direction? I have the the feeling squid might be where to start from, but - browsing the documentation - I found no trace of "intelligent rules for clients"...

Many thanks in advance! :)

---

### Post by dasunst3r on 2008-02-11
If you are using a Linksys WRT54__ router, you should consider a firmware called "Tomato."  [http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

---

### Post by mac.ryan on 2008-02-11
It effectively looks like Tomato could - using a mixture of access restrictions and QoS - achieve about the same I want... so I will consider it as a backup solution! :)

What I would like to find out - though - is if there is any ubuntu-packages (or GNU software to be compiled on my own, deb packages, or...) that would allow me to achieve me the same functionality on a dedicated computer, where I could also install a proxy server, etc.

The reasons for choosing a computer rather than a routerbox are:
[LIST]
[*]I already have a candidate machine I could use.
[*]I like the idea of learning something new.
[*]I have the impression that on a computer I would have a greater flexibility in terms of configuration and add-ons (for example I could run on the same machine a proxy... or maybe the rules are entered with a scripting language...)[/LIST]Anyhow: thanks for having pointed me out on the tomato page. A valid fall-back option, I would say! :)

---

### Post by KCPokes on 2008-02-11
Look into Smoothwall (smoothwall.org) or IPcop as possible solutions.  They are easily customized as there is a whole community of people creating homebrew customizations.  Look into the Advanced Web Proxy, for Smoothwall, as I believe it has the capabilities of doing what you are wanting.

---

### Post by mac.ryan on 2008-02-11
Thanks a lot! With the shared DSL it will take ages to download, but I have already started... I will post in this thread more once experimented a bit with it.

---

### Post by KCPokes on 2008-02-12
Luckily the ISOs for Smoothwall are only around 70MB, so that should help.  Just a thought, though, before you get too far.  I believe, in order to control bandwidth as you'd like, you will require Advanced Web Proxy.  Smoothwall recently launched version 3, so it is a bit young in terms of time for development.  This translates into the fact that not all mods have been ported from SWE 2.0 to SWE 3.0.  Some of them that have been ported don't have the same functionality as what was in the previous version.  The short of it is, depending on what other functionality you desire, going with SWE 2.0 may be a better bet for the present time.  

In regards to the advanced web proxy, you can read up on the features in the administrator's guide:  [http://www.advproxy.net/documentation/smoothwall-advproxy-en.pdf](http://www.advproxy.net/documentation/smoothwall-advproxy-en.pdf)

Good luck.  I've been running Smoothwall for three years now and have been nothing but happy.  I've never had a failure yet, since converting, compared to constant failures with my Linksys router.  Throw in the capabilities you have with Smoothwall and there is no comparison to a cheap router.

---

### Post by mac.ryan on 2008-02-14
Well... thanks again for all the info!

I have been trying to run an installation of SW 3.0 in a virtualised environment (VBox) but the installation failed reporting "unable to calculate dependencies". I might try with version 2.0, although I wonder if the virtualised environment coiuld be the reason for the failure.

Strangely enough - although the website also report an ISO image of 69 MB - once downloaded on my computer it is only 10 MB... (but the file open correctly without any error)... I might try to download it again to check if 10 MB is just a "chunk" that opens correctly by chance, unless somebody confirms first that the ISO in reality is just 10 MB.

Thanks again for the useful post, anyhow!

---

### Post by zirconx on 2008-04-02
> **mac.ryan said:**
> Well... thanks again for all the info!

I have been trying to run an installation of SW 3.0 in a virtualised environment (VBox) but the installation failed reporting "unable to calculate dependencies". I might try with version 2.0, although I wonder if the virtualised environment coiuld be the reason for the failure.

Strangely enough - although the website also report an ISO image of 69 MB - once downloaded on my computer it is only 10 MB... (but the file open correctly without any error)... I might try to download it again to check if 10 MB is just a "chunk" that opens correctly by chance, unless somebody confirms first that the ISO in reality is just 10 MB.

Thanks again for the useful post, anyhow!

mac.ryan, did you ever get this working?  I'm trying to install smoothwall into a virtual machine and am getting the same error.

---


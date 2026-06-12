---
title: "Living in a Novell Border Manager environment"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by j00z76 on 2006-11-08
Hi,
I have installed Kubuntu on the box at my office. We have a Novell network, which isn't much of a problem, as most of the shares I might want to use are also available through Samba. However, a major hurdle is access to the web, which is crucial if only just to download extra packages I need for work. We must go through a Border Manager proxy server. I noticed that cl4others <http://cl4others.sf.net/>.

All I need to do is mount my SYS volume using my Novell username and ncpmount. However, I get an error "ncpmount: No such entry (-601) in nds login", which after googling probably means that I need to use "Novell's full dot notation" for my username, which I don't really know what it means.

How does this "dot notation" work, and what other information do I need to use cl4others?

At any rate, I would like to know if I just need to use my proxy settings (IP address and port) in adept/synaptic/apt-get in order to obtain juicy deb packages once I am running cl4others.

Many thanks!
Jose

---


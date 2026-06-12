---
title: "Ubuntu 7.10 &amp; Firefox 2.0.0.11 - Can't resolve geno-server"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by Achtung on 2008-02-07
Here's the deal.

I'm using Ubuntu Gutsy Gibbon on my laptop, which I use both at home and at the lab I work at. 
Web browsing goes without a hitch, except in one case. Through a Windows-based computer, we send queries to Matrix Science's Mascot search engine to identify proteins based on mass spectrometry results. The results of these queries come back by email as http urls. 

When I open these links on a Windows machine, they open up correctly. However, if I try to open the same link on my Ubuntu laptop, I get the "Problem loading page - Server not found" error in Firefox. Here's a sample link : 
[http://geno-server/mascot/cgi/master_results.pl?file=../data/20080131/F003594.dat#Hit1](http://geno-server/mascot/cgi/master_results.pl?file=../data/20080131/F003594.dat#Hit1)

At first I thought it was the automatic addition of "www" and "com" to adresses by firefox, but turning this feature off didn't help.
Then I thought it was the user agent, but using the user agent switcher firefox extension didn't work, and I can access the results with firefox on a windows machine.
I have tried to access the results by disabling all of my extensions (Adblock Plus, Linkification, Noscript & User Agent Switcher) at once or in different groups, to no avail. 
I tried to get access through a VMWare virtual machine running IE6 in windows XP sp2 on my Ubuntu laptop, but it doesn't connect. 
I tried disabling IPv6 both in firefox and systemwide, but that doesn't help.

What should I try next to solve this issue?

---

### Post by Achtung on 2008-02-14
*Bump* 

I tried to change my DNS server settings, but it didn't help.
I just tried with Firefox 3 to no avail. 

Does anybody have **any** idea?

---


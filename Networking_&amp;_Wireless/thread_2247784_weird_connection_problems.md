---
title: "weird connection problems"
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by jevece on 2014-10-10
I experience weird connection problems that only (seem to) occur when I am trying to view a website from a certain url (http:/vergunningen.info). It's a website that I maintain myself.

What happens is that for one out of five (sometimes more often, sometimes less often) requests there is big delay between the initial response at the request and the completion of that request. The browser shows the first half of the page, then a long time nothing happens, and after 20-40 seconds the rest of the page is loaded and completed. So there is a big 'pause' in the receiving part of the request.

When I ping the url, everything is fine. Responsetimes are consistently around 30-40 ms.

The problem started after I made a change in etc/hosts to temporarily point the domain name to another IP (while I was moving the website from one server to another).
After the move was ready, I deleted the line that pointed the domain name to the old ip. 

Could there be a relation between the problems I experience and my fiddling around with the hosts file?

Another problem that I experience since the move to the new server is that when I try to establish a SSH connection with the server, it takes more than a minute before the connection is made. 

At first I was stalking my hosting provider about this problem, but the problem doesn't seem to be on the server. All my coworkers that work on the same site (from different locations) don't experience any problems. So it must be something with my computer. I am using Ubuntu 12.04 on Dell XPS 13.

I hope someone can shed a bit of light on this.

Jan

---


---
title: "making an external ip address resolve locally"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by pincombe on 2008-01-07
Hi,

I have a dedicated server provided by [Nasstar]("http://www.nasstar.co.uk/") . I can't change servers unfortunately which is a shame because I have this nasty problem I haven't been able to solve.

The server is only allocated an internal IP address. The internet facing IP address is handled through what I presume is a hardware based firewall.

The issue I have is in PHP. I host multiple websites and some of them have news feeds. I thought it would be nice to display the news items on the front page of one of the websites, using the feed which already exists. 

Doing this creates some kind of loop which results in the page not displaying. This problem is immediately fixed when I add the website to /etc/hosts

However although this solution is reasonable at the moment. In the future other people will be using the server to host websites and I don't like the idea of having to give them ssh access or root access to the server.

Has anyone got any possible solutions to this problem?

I was thinking along the lines of either being able to find another way to set a local host or maybe if its possible add a local loop for the internet facing IP address.

Any suggestions are welcome at this point :popcorn:

---

### Post by tatster on 2008-01-10
Hi,

A few questions to set the ball rolling hopefully....

Do you have SSH access to your server?  Are you able to get any successful name resolution to the internet - either by pinging servernames, or nslookup or dig ?

What is your server configured to talk to for name resolution.  ie DNS servers.


Tatster.

---


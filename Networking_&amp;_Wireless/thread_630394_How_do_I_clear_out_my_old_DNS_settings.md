---
title: "How do I clear out my old DNS settings?"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by wendallsan on 2007-12-03
Hi all,

After having a heck of time getting my wireless card to work in my desktop (spent a month tweaking my resolve.conf when the problem was actually in my /etc/dhcp3/dhclient.conf), I finally have reliable wifi network access (yay!).  It seems that my computer (or maybe my router) has cached a number of bum addresses for a lot of domain names (such as yahoo.com and google analytics).  Where would this stuff be stored and how can I clear it out so that I can do a new domain lookup and get the right addresses for these sites?  I have currently removed my router DNS from the loop entirely, so I'm guessing that even if the info is wrong there, it shouldn't matter because my box is not using that service for DNS lookups.

thanks!

---

### Post by bwald on 2007-12-03
Hello,

Are you using Firefox?  If so, there is a quick way to wipe its "cache" of stored webpages.  Just go to tools -> clear private data.  Then select "cache" and delete it.

---

### Post by wendallsan on 2007-12-03
Hi, yes I'm using Firefox, clearing the cache didn't seem to make a difference.  I had some problems with my home router usurping my DNS settings that I fixed last week, but sites that I tried to visit last week are still not connecting this week, although the rest of the Internet is working fine.  I can ping the server names and get a good dns lookup and successful pings from the terminal, but it seems like Firefox or some other "layer" in the networking system is stuck with bad IP addresses for certion sites.  Any other ideas?  Thanks again!

---

### Post by bwald on 2007-12-03
Hrm, have you tried using a different browser?  You could try Epiphany for gnome or Konqueror for KDE.  If either of those have the same problem connecting then check your "/etc/hosts" file.  See if any of the sites you can't reach are described in /etc/hosts.

---


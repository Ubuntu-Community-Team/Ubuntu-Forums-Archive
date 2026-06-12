---
title: "server can't reach some hosts"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by grough on 2006-10-12
My Ubuntu server is unable to reach the majority of the sites I try on the web, and I can&#8217;t figure out why. The other machines on my home network can access all sites without problems.

For instance, pinging google.com works fine, but it can&#8217;t reach ubuntuforums.org, and most annoying of all, it can&#8217;t reach the Ubuntu repositories, preventing me from installing new software.

The only sites I&#8217;ve found to work (just trying randomly) are google.com, digg.com, songbirdnest.com. Anything else I&#8217;ve tried can&#8217;t be reached.

When pinging, most sites return an &#8220;unknown host&#8221; error, or otherwise the ping starts, but no packets are returned. Results have been consistent for each site tried.

Strangely, Ruby can load documents from hosts that are unavailable to ping&#8230; that&#8217;s the only other thing I&#8217;ve tried. I don&#8217;t have a real browser as this is a headless server.

I have no idea why this could be happening; does anybody out there?

Thanks,
Gavin

---

### Post by dannyboy79 on 2006-10-12
have you tried disabling ipv6? also, make sure that your dns servers are set and that they aren't being changed when you reboot! these are 2 of the most common problems I am seeing in these forums. Let me if you get it fixed after working on these 2 things.

---


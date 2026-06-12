---
title: "What is up with my DNS??"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by wendallsan on 2007-11-28
Hi all,

I've been trying to use Ubuntu on a couple systems for several months and have been plagued by network problems, seemingly based on DNS problems.  Once in a blue moon I am able to surf the web without any problems, but 99% of the time I am unable to view web sites that I haven't already successfully been to before.  I've seen this problem documented all over this forum.  This problem is affecting multiple PC's in my household the same way, regardless of how their connected (wired or wireless).

Here is what I see.  I can look at my /etc/resolv.conf and see:


search domain.actdsltmp
nameserver 192.168.0.1
nameserver 208.64.240.3

Problem is I know my router has a crappy DNS server and want to use my ISP Provider's DNS's, which are at  66.228.195.3 and 66.228.195.2.  I don't even know what that 208 IP address is.  So the easy solution would be to edit the file, remove the 2 nameserver lines and put in 2 of my own to my ISP's servers.  I do so, save the changes, and restart the network (/etc/init.d/networking restart).  BAM, the original resolv.conf is back and my changes are gone.  What's going on?

---

### Post by jimrz on 2007-11-28
Try going to the panel >System>Administration>Network>the"DNS" tab and deleting the funky IP's  then add your own choice of DNS server IP's. 
If that does not help, then try accessing your router's config and looking to see if that is where the problem originates. If so, you should be able to manually change them there.

---


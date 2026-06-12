---
title: "Intranet Issues"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by j-sta on 2008-01-15
So I'm a fairly new Ubunutu/Linux user, but so far I've  been able to find help for just about all the little issues I've come across.
This one, though, I'm not having any luck.  I've done a lot of searching, and have yet to find anything that's much help with this one.

I'm having issues viewing webpages that hosted within the internal network.
Quite frequently, as soon as I try to refresh the page, I immediately get "Page cannot be found."  This does not happen when viewing pages on the internet, though.

Now, I would think this is a network or config issue, but I don't believe that's the case.
I have disabled IPv6.  I have added lines in the hosts file, to point the domain to the IP address.  I have tried changing DNS servers.  But regardless of all this, I have the same issue.

I have another laptop running XP on the same subnet; no issues what-so-ever.  I also have an XP virtual machine running on this Ubuntu box, and it has no issues.
Only Ubuntu does.

Am I just missing something?

Also to note; at times, a ping to the gateway times out.  But again, this only happens on Ubuntu, not on the XP virtual machine, not on my XP laptop.

Thanks for any help! :)

quick edit: it's wired network; no wireless.  Also, I have tried swapping the ethernet cords between my XP laptop and Ubuntu box, thinking maybe it's the port in the router; issue still persists.

another quick edit: Ok so it's not an intranet site; it is accessible from the internet, but access is limited to certain IP ranges; those being internet network IPs, and certain external IPs.  Wether or not that makes a di fference.  But it is all within the internal network.

---

### Post by mimada on 2008-01-16
I'm seeing a lot of issues with samba and connecting to other computers on the LAN. Try disabling the iptables firewall and see if that takes care of your issues. You might want to install the Firestarter front end for iptables if you're not comfortable with the command line.

---

### Post by j-sta on 2008-01-16
is iptables installed by default?

and the strange thing is, it's only with webpages hosted within the internal network.

Now, say I'm trying to get to ubuntuforums.org; it  may sit at "finding host ubuntuforums.org" for up to 3-4 seconds, but then loads the page.

With any of the pages hosted on the internal network, it *instantly* comes up with site cannot be found.

One thing I just thought of; I'm going to try setting the hosts file to the external IP address, instead of the internal, and see if that might make a difference.

I will look into getting iptables disabled though, if it is in fact running.


quick edit, since a ping timed out; here's what's happening.  And again as I posted earlier, I have absolutely no issues with my XP laptop, or with the XP virtual machine running on this  Ubuntu  box.  And I also just remembered, the site is no longer accessible from an external network, as it's now hosted within the AD Domain.

> PING samuel.ad.mta-telco.com (192.168.*.*) 56(84) bytes of data.
From 2811-1-wasilla-fe0-0.*.net (64.4.*.*) icmp_seq=1 Destination Host Unreachable
64 bytes from *.*.mta-telco.com (192.168.*.*): icmp_seq=2 ttl=124 time=12.6 ms
64 bytes from *.*.mta-telco.com (192.168.*.*): icmp_seq=3 ttl=124 time=2.23 ms
64 bytes from *.*.mta-telco.com (192.168.*.*): icmp_seq=4 ttl=124 time=2.17 ms

--- samuel.ad.mta-telco.com ping statistics ---
4 packets transmitted, 3 received, +1 errors, 25% packet loss, time 3003ms


---

### Post by j-sta on 2008-01-16
I installed Firestarter, went through the setup, then made sure the firewall was disabled.
It's disabled.  But I continue to have the issues.

Any other ideas?

---

### Post by j-sta on 2008-01-17
well, so it appears to just be a Firefox issue, and not Ubuntu.
Got Opera installed, and I'm not having the problem anymore.

What settings in Firefox could cause something like this?

---

### Post by j-sta on 2008-01-18
well I'm pretty sure I finally got the issue resolved.
I finally managed to get a statically assigned IP address working, and now I'm no longer having the issue.

I changed the priority on the DNS servers, and all is good.
I think it had something to do with the internal DNS servers responding to Linux, for whatever reason.  Or maybe it's just due to the fact that atleast 1 of the DNS is setup on an AD Controller.

But... life is good now :)

---

### Post by zipperback on 2008-01-18
Glad to hear you got the issues resolved. I had a similar issue with internal network pages not showing up, I tracked it down to an issue with the broadband gateway that I was using, very strange indeed. Anyway, glad to hear you got it up and running.

- zipperback
:popcorn:

---


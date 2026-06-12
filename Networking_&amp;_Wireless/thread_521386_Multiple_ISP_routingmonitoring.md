---
title: "Multiple ISP routing/monitoring"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by OldManRiver on 2007-08-09
All,

I had (still have) a Gentoo box that I was trying to config to work on multiple ISPs (3).  Have onboard NIC to serve to network (from all I read monitoring NICs have to be exact make and model) so onboard is odd duck, therefore has to be the NIC serving DHCP to the network.

I just couldn't get this done in Gentoo.  Couldn't get the config files right following the HOWTOs.

I posted the following on the Gentoo forum to explain my problem in depth:

[http://forums.gentoo.org/viewtopic-t-533062-highlight-.html](http://forums.gentoo.org/viewtopic-t-533062-highlight-.html)

Have drawings, links and all there, but a little lengthy due to exchanges on the page.  Anyway you will get a real good feel for what I need to do, by reading that.  Also you'll see the dropping connections, have forced us onto the 144KB line as main line and need to get the other back so getting this config right is critical to our operations, plus I have VOIP phone on the ckt and need it on highest speed possible, as the latency is horrible on the 144KB (VOIP not recommended below 512KB). BTW all ckts are back up, but need them routing through this box.

I'm taking a course at the University to prep for Linux cert.  My prof is full time industrial Linux/Unix sysadmin.  He uses and swears by Ubuntu.  After months of not getting the job done on Gentoo, I converted my Red Hat (config for this clugey there also) box to Ubuntu, so I could get up.  Had install problems y'day, which took all day to resolve, mostly because monitor is non-supported LCD and config with it is tricky.  So far Ubuntu has lived up to the rep my prof gave it, easy and stable.

Now, this U box, which I'm on needs to get the IP routing, IP monitoring, and DHCP clients & server configed right.

Would appreciate input on howto get this done!

Thanks!

OMR

---

### Post by OldManRiver on 2007-08-09
All,

Found a resource for this at:

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

But what he is doing looks to be opposite of what I want to do.

If I understand this post this config has one ISP connect and two Network connect so network can be segmented.  Am I wrong?

Can someone enlighten me?

OMR

---

### Post by OldManRiver on 2007-08-10
All,

Sure would be nice to know someone reads and cares about your problem.

OMR

---

### Post by OldManRiver on 2007-08-13
All,

Overdrank, gave me a link to set the U box as server at thread:

[http://ubuntuforums.org/showthread.php?p=3182168#post3182168](http://ubuntuforums.org/showthread.php?p=3182168#post3182168)

Hope this resolves most of the problems.

Still may need to re-post if I find problems with install.

Thanks!

OMR

---


---
title: "All networking is gone after upgrade to 7.10"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by maximizer on 2008-03-01
I have an old Inspiron 4000 that last year had everything working, both wired and wireless, for a few months.  Then I auto-upgraded to 7.10 in October, and all networking disappeared.  I didn't have time to deal with this at the time, but now I'd like to revive it.

I had everything working with Wicd, but don't recall all the steps I had to do.  I don't know much about networking.

Just now I tried "ifup eith0", got "No such device".

My wireless is a Broadcom 43xx based PCMCIA.  The lights are dark, and "ifup wlan0" gives No such device also.

Please help!  I dread reinstalling - I have no CD drive, last time I did this with network boot and it was painful :)

Thank you!

---

### Post by kaginken on 2008-03-01
This worked for me, I have a dell with same NIC:

[http://backports.ubuntuforums.com/showthread.php?t=405990](http://backports.ubuntuforums.com/showthread.php?t=405990)

If that doesn't do it, another option is to install the previous version that was working.  Not sure if that's an option you're ready to consider yet.  My wife's laptop stopped working too after an upgrade, so I just installed the old 6.06 dapper drake and it's back!

Oddly, some versions of ubuntu seem to work better than others 

Hope this helps!

---


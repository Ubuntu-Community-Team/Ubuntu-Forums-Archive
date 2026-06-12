---
title: "ping connects, firefox doesn't after 2.6.20 kernel upgrade"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by Miaowara on 2007-02-19
Hi,

I just upgraded my kernel to 2.6.20 and while it is blazing fast, I'm having a problems with my wireless. I can't seem to connect to the internet with Firefox or wget (they just seem to hang trying to connect though they do appear to be occasionally receiving tiny, tiny pieces of data). I *do* get a response when I ping sites, however. Weird, huh?

If I boot back into my previous kernel (or into Windows XP for that matter) I have no problems connecting to the Internet so it doesn't appear to be any problem with my router or settings.

I should mention that the firmware drivers were not in /lib/firmware/2.6.20 as they were supposed to which was created a problem like the following link so I copied the necessary ipw2100 firmware files as instructed here:
[http://ubuntuforums.org/showthread.php?t=135827&highlight=ipw2100_get_firmware](http://ubuntuforums.org/showthread.php?t=135827&highlight=ipw2100_get_firmware)

Upon the advice of others I've disabled ipv6 as specified here:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Still doesn't work though.

Anybody got any suggestions on how I can get my wireless working correctly? Thanks!

---

### Post by leatherworker on 2007-02-19
I have just installed Ubuntu 6.10 and I have mostly the same problem:  pinging, no problem.  Tracing:  it hangs after travelling five nodes.  From Firefox, it would hang after saying "Connecting to  www.google.com".

There are a few websites I can connect to without a problem, but not Google, Wikipedia or Ubuntu Forums (I ma now writing from a neiboring windows machine that uses the same DSL router and also wireless connection.....

If I look at the under Network settings, I see fixed dns settings  :

192.168.0.1
205.171.3.65

and under search domains I have

domain.actdsltmp

Are these correct?

JOhan

---

### Post by leatherworker on 2007-02-20
Hey, I just got mine fixed from a tutorial in these forums (How-To Stabilise your DNS addresses)  at 
[http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns](http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns) 

All I did was to follow this:
IPv6 Quick (Firefox) Fix

If you can't access the web through Firefox, though you know you have an internet connection via your modem/router try the following:

Enter about:config in Firefox's address field.

Enter ipv6 in the new Filter: field.

Double click on the line left in the display window to change it's boolean value to true.

Restart Firefox.

& that should be that... 

It worked!

I hope this helps!

---

### Post by Miaowara on 2007-02-20
Thanks leatherworker, no joy though. I tried disabling ipv6 in firefox but with no luck. Think I'll just fall back to a kernel that works for the time being, though I'm not giving up!

---


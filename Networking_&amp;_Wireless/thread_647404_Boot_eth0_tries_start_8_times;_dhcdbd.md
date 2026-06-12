---
title: "Boot: eth0 tries start 8 times; dhcdbd ?"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by movrshakr on 2007-12-22
(Will try in a different topic)

This is about several problems, but I think they are all resulting from one root cause. It started when I found that ALWAYS after boot, my ntp had no associations with servers to sync to even though good ones were specified in ntp.conf.

I looked in syslog and found that ntpd was starting up when eth0 was not yet active, so of course it could not associate with the servers specified in ntp.conf.

Furthermore, to my surprise, I see that eth0 is trying to start EIGHT TIMES (Stage 1 thru3) before finally succeeding thru Stage 5--fully up. And it appears that the failures of the eight times is because dhcdbd is not yet loaded...there are these lines just after the eight failures

NetworkManager: <WARN> nm_dhcp_manager_begin_transaction(): dhcdbd not running!
Dec 21 08:20:28 maximus NetworkManager: <info> Activation (eth0) failure scheduled...
Dec 21 08:20:28 maximus NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 21 08:20:29 maximus NetworkManager: <info> Activation (eth0) failed.

So,
- is dhcdbd the cause of eth0 not coming up?
- why is it not starting in an acceptable order (early enough)?
- how can I fix this?

Thanks.

---

### Post by movrshakr on 2007-12-22
Followup with more info...in another thread, I saw folks talking about the 'interfaces' file.  The ones they were describing had many more lines in it than mine.  Mine has only this:

auto lo
iface lo inet loopback

Is this possibly part of the problem described in my initial post?  Just striking in the dark here.

---

### Post by heindsight on 2007-12-23
I just noticed that I have the same problem -- I would probably never have noticed if not for this thread :)

The problem is not with the interfaces file, but rather has to do with the order in which services are started.
There's a bug report related to this on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/176213](https://bugs.launchpad.net/ubuntu/+bug/176213)

I haven't tried it yet, but it seems the solution is to make dhcdbd start earlier in the boot process.

---

### Post by randomjohn on 2008-01-04
> **heindsight said:**
> I just noticed that I have the same problem -- I would probably never have noticed if not for this thread :)

The problem is not with the interfaces file, but rather has to do with the order in which services are started.
There's a bug report related to this on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/176213](https://bugs.launchpad.net/ubuntu/+bug/176213)

I haven't tried it yet, but it seems the solution is to make dhcdbd start earlier in the boot process.

How would I go about changing the order of the boot process?  I'm getting the same error again.  Last time I had to completely remove and reinstall samba to fix this.  I'm looking for an easier longer-term solution.

---

### Post by movrshakr on 2008-01-04
.
Read through this thread (5 pages): 
[http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr](http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr)

You can dl and install and use the ubuntu app package called **sysv-rc-conf**. 

You use the -p switch with it, but you need to know what you are doing.  To summarize the end point of my transactions over in that thread...
-------- After doing all the other changes -----------------------------------
I reset (using "sysv-rc-conf -p ' by the way) S24dhcdbd to S13dhcdbd in /etc/rc[2-5].d. And, lo and behold,

a. ntpd tries to start but fails to get associations due to eth0 not being configured yet (as before)...BUT...

b. eth0 no longer tried 7 to 10 times to come up; it goes through the five stages only once!

c. ntpdate runs--apparently successfully--from the new script:..
(Dec 27 18:57:48 maximus ntpdate[5454]: adjust time server 209.132.176.4 offset 0.009138 sec)

d. ntpd starts again, successfully--from the new script, as a post boot 'ntpq -p' shows associations to the servers configured in ntp.conf.

In other words, all works as it should, after the modifications so kindly suggested by heindsight.

Summary: on my machine, the problem is completely solved by
doing the changes he suggested (read previous posts) and
using the script file he provided, and
changing dhcdbd to priority S13 (BTW, I left the Kill ones unchanged at K16 in 0,1,6)
-----------------------------------------------------
so read all of it over there.  There's more we did than this.

---


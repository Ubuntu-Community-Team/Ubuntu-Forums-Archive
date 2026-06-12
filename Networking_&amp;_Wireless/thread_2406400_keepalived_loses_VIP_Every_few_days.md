---
title: "keepalived loses VIP Every few days"
date: 2018-11-20
forum: Networking &amp; Wireless
---

### Post by sbisker on 2018-11-20
I have six nodes setup with keepalived on Ubuntu 18.04.  They provide a bunch of VIPs.  I can manually failover from one to the other without any issues.  Every few days, however, VIPs are lost on all nodes.  Keepalived is still running on every node.  There are no entries in the logs.  I think that it has to do with auto-updates for security related packages.  On both of the last to occasions, updates were installed in the morning.  It appears that the cause is restarting of systemd-networkd.  When this occurs keepalived doesn't get notified that the interface is down.   I found this article describing the same symptoms:  [https://access.redhat.com/solutions/3541681](https://access.redhat.com/solutions/3541681).

To recreate the issue.
1. Start keepalived
2. Verify VIP is present
3. service systemd-networkd restart
4. Verify VIP is missing and did not failover to backup node.

Any suggestions would be greatly appreciated.

---

### Post by wes234234 on 2018-11-21
We're having the same issue here on both 16.04 and 18.04 in multiple environments, using keepalived 1:1.2.24-1ubuntu0.16.04.1 and [FONT=monospace][COLOR=#000000]1:1.3.9-1ubuntu0.18.04.1[/COLOR]
[/FONT] respectively.  Nothing in the logs about a failover, the master still thinks it's master and the backup is backup, the VIP simply vanishes off the interface after a couple days.  As of now I'm at a loss to explain it and can't find anyone else reporting the same issue except for this forum post here

---

### Post by wes234234 on 2018-11-21
I notice this in the changelog for both these versions:

  * d/p/fix-removing-left-over-addresses-if-keepalived-abort.patch:
    Cherry-picked from upstream to ensure left-over VIPs and eVIPs are
    properly removed on restart if keepalived terminates abonormally.

and I notice a correlation between the problem and systemd-tmpfiles triggering a cleanup.  I wonder if this code might be misdetecting a SIGHUP or something as an abnormal shutdown.  For now we're downgrading

---

### Post by wildmanne39 on 2018-11-21
Hello and welcome to the forum wes, please start your own thread instead of hijacking someone else's, that way you can both get the help you deserve and it does not get confusing for the people that try to help you.

Thanks

---

### Post by wes234234 on 2018-11-22
Wildmanne39 I don't understand how you could possibly think adding information relevant to the OPs post and confirming their issue is in any way hijacking the thread.  That's a very silly assertion

---

### Post by QIII on 2018-11-22
wes --

Adding your information does not materially help the OP.  In fact, your symptoms, though similar, may arise from entirely different causes and discussion of them may very well lead to confusion for the OP and those wishing to help.  That is not a "silly assertion".  It is a phenomenon the Staff has observed over many, many years of experience.

Please allow the OP to get individual help for his/her problem free of interjection.  If you would like a resolution, please start your own thread.

If you find a resolution, please feel free to share that with the OP then.

---

### Post by wes234234 on 2018-11-22
Sure, I just thought this was a regular forum, that is when I found the post in google results and opened it I missed the 'official support' path leading to it... apologies.  Anyway, our attempted resolution is to downgrade keepalived to the version in the repo from before that patch ubuntu backported that I mentioned above.  I believe OP should give that a go as well because it might just work and can't be worse than their current situation - and although I can't speak for them I'm sure if they're hurting as much as we are from this issue they might appreciate the suggestion.  I'll report back if it works for us, otherwise start a new thread if the problem persists as you request.

---

### Post by wes234234 on 2018-11-28
FYI, after 5 days we haven't seen a recurrence of our specific 'VIP spontaneously vanishes' issue since downgrading to versions from before the 'd/p/fix-removing-left-over-addresses-if-keepalived-abort' patch on both 16.04 and 18.04.  I hope this helps sbisker and anyone else experiencing the same problem

---


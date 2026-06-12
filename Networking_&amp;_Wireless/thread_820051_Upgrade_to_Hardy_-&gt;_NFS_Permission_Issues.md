---
title: "Upgrade to Hardy -&gt; NFS Permission Issues"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by SeanOB on 2008-06-05
Hello,

I've upgrade all of my boxes to hardy and now I'm having mount permission issues when I try to mount my server (that is serving via nfs.)

I get something like:
mount failed, reason given by server: Permission denied

The current "fix" is to restart the nfs kernel on the server with:
sudo /etc/init.d/nfs-kernel-server restart

Then all of the mounts work fine...

Any ideas?
Something going wrong at boot?  Some service startup order issue?
What log(s) should I look at?

I can post my exports or fstab if someone is curious...

The fix works fine when I'm at home; but I just got an SMS from the wife that said:
"I can't play music on the mythbox :("

DOH!  Can't exactly SMS back the fix.
(In related news I don't have internet access at home due to an messup at ATT).

Thanks!

SeanOB

---

### Post by SeanOB on 2008-06-07
Anyone seeing this issue?

It's not a big deal until my machine gets restarted...  then I have to remember to manually restart the nfs kernel.

Anyone?

-Sean

---


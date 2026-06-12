---
title: "NIS client boot order problem"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by professorYaffle on 2008-09-19
I'm setting up a new machine on the local network using Hardy. It was installed from the alternate CD (as I wanted the root partition on a striped LVM partition) and then upgraded over the net to a normal desktop set of packages, and then further updated to the kubuntu desktop.

It mostly works but I'm having problems with NIS when booting. It won't bind to the server (which happens to be a Solaris box) when booting. However, once the machine is up I can restart the nis client by hand and it works fine. Then I restart autofs, and kdm etc. and eventually the machine is working fine, but I had to do this every boot.

The NIS server is defined in yp.conf with an explicit IP address. No name, so it's not dependent on DNS, yet when booting I get the impression that it's broadcasting for a server and ignoring the one I told it to use. When I restart NIS by hand it goes straight there.

Yesterday I took the machine down to single use mode and went through the services by hand one at a time in the order they appear in rc5.d. I discovered that the service NIS was waiting for was "hal" - that's not one I'm familiar with so I'm not sure if my current solution is correct: I've moved hal in the start order from S24hal (I think) to S17hal - one before S18nis.

This seems to work okay for me, but it strikes me that if this is the correct solution it's a fairly basic bug in the init script package - so I rather suspect that it's more likely that I've misconfigured something in NIS, (or deeper in the networking etc..)

Any help clearing this up (or confirming it's worth submitting a bug report) would be appreciated. Not sure what config data etc. is worth posting.

Cheers!

+Dave

---

### Post by mirabilos on 2009-05-19
A similar problem has bitten our desktops at work, where we use LDAP.
The problem is that KDM starts *way* too early, it ought to be run
last, very last, in the boot process, only after EVERYTHING else has
run. But Canonical seems to have chosen the Windows® XP approach to
boot time reduction &#8211; show the GUI early so that the user is happy.

Now a workaround is to disable NetworkManager by uncommenting the
stuff in /etc/network/interfaces &#8211; but that does not fix all of our
problems.

So if you know of a way to make KDM start last, which is kept over
package updates (i.e. no manually changing rc symlinks), I&#8217;d be
glad to hear about it.

---

### Post by professorYaffle on 2009-05-19
> **mirabilos said:**
> So if you know of a way to make KDM start last, which is kept over
package updates (i.e. no manually changing rc symlinks), I’d be
glad to hear about it.The only thing I can think of would be to write a little script and add it into /etc/rc.local that looks in the rc?.d directories to see if S13kdm exists, and if so to rename it S99kdm.
So, after an update that re-installed S13kdm, the first boot would be dodgy but the system should always be okay on the next reboot.

---

### Post by mirabilos on 2009-05-19
> **professorYaffle said:**
> The only thing I can think of would be to write a little script and add it into /etc/rc.local that looks in the rc?.d directories to see if S13kdm exists, and if so to rename it S99kdm.

S99 is not good, I chose S95.

> **professorYaffle said:**
> So, after an update that re-installed S13kdm, the first boot would be dodgy but the system should always be okay on the next reboot.

Thanks, this is what I did now. So there is probably no better way, hm?
I did use update-rc.d though.

---

### Post by professorYaffle on 2009-05-19
Just thought it through a little bit further. If you're adding new scripts in with update-rc.d then it would be better to make this kdm-init-moving script run during shutdown, not boot up. So it would get called going down after an update and then even the first reboot should work fine.

---

### Post by mirabilos on 2009-05-20
Something like that, yes. We have a script run every 10 minutes,
positioned on a server, with which we schedule things like that,
until we get around to set up puppet or something similar. (Just
too much to do, too few time&#8230;)

---

### Post by 480silverton on 2009-10-09
Has anyone figured out a answer to this problem?

---

### Post by mirabilos on 2009-10-10
(I tried to respond yesternight in Lynx, but it didn&#8217;t work, it
let me log in, but when wanting to post it said I was not logged
in, WTF?)

A periodically run script, whether via cron or as /etc/init.d/
one (current solution, since we have a company-config package
anyway), has worked very well for us.

---


---
title: "WG111T Lost on Reboot Problem"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by jreising on 2006-10-20
Hi Folks,

I have a weird problem with my WG111T.  I have it working w/ ndiswrapper but if I reboot the system the adapter won't come up unless I disconnect it and reconnect it before booting back up.  The adapter works fine on Windows XP since the system is dual boot, so it's almost as if something in dapper is scrambling it's brain on reboot.  If I type ndiswrapper -l it says the device and driver are installed but ifconfig iwconfig, etc don't see it...

Any ideas?

Thanks,

Joe

---

### Post by nomisholman on 2007-01-15
G'day

I haven't seen any other post about this yet.

I'm getting the same problem too.
I've found I have to have the adaptor disconnected on bootup.
Then reconnect it and it comes up.

Its been awhile since i've played with linux (slackware '96 was the last thing i remember)
I'm guessing its got something to do with the order things get loaded in the init scripts.

Anyone out there got any suggestions.

I'll keep playing and let you know

Simon

---

### Post by Multivitamin on 2008-03-30
Hello :)

one year later and another wg111t user (me) has the same problem. 

Did anyone has got a solution for this problem?

--
Multi

---


---
title: "setenv DISPLAY"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by PhantomOG on 2008-08-25
I've got Ubuntu successfully installed, got the wireless networking going, and also got my cisco VPN software installed and working.

When I'm at work and log onto a different machine, I do the following:
rlogin othermachine
setenv DISPLAY mymachine:0
(also run xhost + on mymachine before logging onto the remote system)

And then I can run programs on the othermachine and view them onscreen at mymachine.

How can I do this now at home with my Ununtu machine?  I can rlogin to the machines at work, however, I can't get the display working.  I've tried:

setenv DISPLAY my.ip.address:0.0

but that doesn't work.  What is the correct way to do this?  Or is it not possible unless I'm actually physically connected to the network at work?

---

### Post by PhantomOG on 2008-08-25
figured it out.  Info in this thread worked:

[http://ubuntuforums.org/showthread.php?t=265660](http://ubuntuforums.org/showthread.php?t=265660)

---


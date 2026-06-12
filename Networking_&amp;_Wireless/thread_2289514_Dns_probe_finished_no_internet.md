---
title: "Dns_probe_finished_no_internet"
date: 2015-08-04
forum: Networking &amp; Wireless
---

### Post by Steve_McCoy on 2015-08-04
Need some guidance. I'm running Ubuntu 14.04 64-bit. Been having some on-and-off issues with Google Chrome and Chromium opening very slowly, as well as long delays going to websites...getting "resolving host" message in the browsers. 
After doing some research online, I took what I'm guessing was bad advice and ran "sudo dpkg-reconfigure resolvconf". Got a screen that says "prepare /ect/resolvconf for dynamic update?", to which I answered Yes.  Then, after a reboot, I have no internet access. Browsers show "DNS_PROBE_FINISHED_NO_INTERNET" message.
How can I fix this mess I created? Thanks...

Steve

---

### Post by TheFu on 2015-08-05
Over the last few days, DNS servers around teh world have been under attack. BIND has a bug.
[http://arstechnica.com/security/2015/08/exploits-start-against-flaw-that-could-hamstring-huge-swaths-of-internet/](http://arstechnica.com/security/2015/08/exploits-start-against-flaw-that-could-hamstring-huge-swaths-of-internet/)

Nothing you or I can do about that, but live with it until they are all patched and the crackers stop bothering.

So - you've marked this as "solved" but didn't list the corrective actions taken. Other people will have the same question, so having the answer here really would help the community. Please add it.

---


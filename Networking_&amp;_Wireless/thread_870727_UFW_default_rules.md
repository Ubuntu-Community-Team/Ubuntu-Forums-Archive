---
title: "UFW default rules"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by ProbablyX on 2008-07-26
Hello!

What are the default rules of ufw (the Uncompilcated FiewWall)?

I've read on some websites that you are to apply "deny all" or so, but it seems ufw blocks stuff anyway for me.

That is, is having ufw enabled sufficient or should you make some settings?

Thanks

---

### Post by bryncoles on 2008-07-26
follow this guide to set up UFW:

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

as i understand it (and i could be wrong) the ufw is a configuration tool for the ip tables. by default, it has no rules set, but by default ubuntu has no services running and nothing listening at any ports. 

so, unless you install something that connects to (or wants to connect to) the internet, the default 'no rules' are effectively the same as default 'deny all' rules (which is what the command sudo ufw default deny' would implement). 

i would follow the guide i posted, as it cant hurt to set up the firewall to deny everything... can it?

---


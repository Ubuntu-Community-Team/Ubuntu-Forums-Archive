---
title: "Hardy locks on SUDO during configuration as NIS client"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by wimmelis on 2008-11-13
Dear all, 


For the last few days, I have been trying to get a Hardy 64-bit installation to become NIS client, but without luck. 
The NIS server runs VINE linux, and has proven to work with other machines, and has all access permissions set correctly (the machine which runs Ubuntu now used to have vine linux on it and NIS was working then).
I have tried most how-tos I came across, but what really puzzles me is that when making some changes to either the groups file or nsswitch.conf, suddenly the sudo command would not work anymore. And then I can only go into rescue mode and undo those changes.  

Secondly, is there any recommended howto for getting nis to work ? As my machine does not bind ... well it does not really get configured either :(

Many thanks in advance, 


Regards,

WM

---

### Post by wimmelis on 2008-11-13
Dear all, 


I fear not to be able to explain how it got solved, since after a reboot everything seemed to work, though before the reboot some packages were updated, so maybe they solved the problem.


WM

---


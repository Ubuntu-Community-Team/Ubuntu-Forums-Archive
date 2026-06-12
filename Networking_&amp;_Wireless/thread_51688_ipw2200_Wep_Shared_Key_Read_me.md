---
title: "ipw2200 Wep Shared Key Read me"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by jts on 2005-07-24
I'm posting this, in the hopes that it may save someone elses sanity.

After running Ubunutu against my wireless AP for some time now, with absolutely no problems, it just "would not connect" one day.  Couldn't figure it out.  I tried to use the networking tool (System->Admin->Networking), entered/double checked my keys.  Made sure I used "s:"  in front of my key...everything.

Long story short, finally figured out my problem.  For some reason, the word "restricted" was not being added to my  /etc/network/interefaces  
file (Man pages can sometimes be your friend).

So in that file, I changed

wireless-key s:myhappykeywhichisfakehere

to

wireless-key s:myhappykeywhichisfakehere restricted


After I was done editing the file, a quick /etc/init.d/network restart
is all it took to get it up and running.  

Don't know if this is a bug or not, but I hope this helps someone out.

---


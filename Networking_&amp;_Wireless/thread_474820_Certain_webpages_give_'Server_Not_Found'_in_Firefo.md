---
title: "Certain webpages give 'Server Not Found' in Firefox"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by LBarrettAnderson on 2007-06-15
I just installed Ubuntu the other day.  Originally I had installed the 64 bit version but yesterday changed to 32 bit, and I had the same problem on both of them.

Certain pages give a "Server Not Found" error in firefox (while these exact same pages work fine on my other computer running windows).  If I then go to the address bar and then press enter, the same page will load just fine.

Some other details:  The stylesheets on yahoo and yahoo sports do not load.

Google ads do not load (there are no ad-blockers installed afaik).

From my research on the subject I can tell that it is probably a combination of problems from my ISP and firefox (or network) settings - I was not, however, able to find a solution.

I tried epiphany or whatever the other browser  is and I got the exact same problem, so I'm assuming that it has something to do with the settings in Ubuntu.

Any help would be greatly appreciated.  (I'm running ubuntu until my next paycheck, UNLESS I like it enough to keep it a bit longer.  If I can't fix this problem, my "Ubuntu/Linux Trial" will be short and not very sweet).

---

### Post by LBarrettAnderson on 2007-06-15
If anyone was/is curious, I was able to fix the problem entirely.

It was a DNS problem.  Originally my resolv.conf file had it pointing to my router, but apparently my router is messed up, and by pointing to my ISPs DNS address I was able to get everything working.

---

### Post by moayyad65 on 2007-08-31
i also have the same problem!

---


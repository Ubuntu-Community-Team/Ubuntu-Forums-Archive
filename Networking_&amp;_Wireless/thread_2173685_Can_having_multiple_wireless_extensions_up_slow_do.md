---
title: "Can having multiple wireless extensions up slow down the internet on my computer?"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by Panderz on 2013-09-10
This could very possibly be a stupid question, but I'm not sure and this have been bugging me the past couple of days. 
if I typed "ifconfig" in the bash, it would show eth0, lo, and wlan0 all as being up. I noticed that my internet has been really slow on openSUSE and Ubuntu, both of which would show the same result as the output of "ifconfig".
I took a chance and disabled lo and eth0, now my internet seems to be very smooth, before I would just be waiting minutes for a web page to load.
So, my question is, are these all supposed to be turned on at once, or were they not supposed to be on? Networking has always been my downfall, so I really have no clue if this is a dumb question.
Thank you!

---

### Post by Panderz on 2013-09-10
Surely someone can answer this :(

---

### Post by varunendra on 2013-09-11
I find the question, combined with your experience with the change, rather interesting, not dumb :P

In theory it shouldn't affect internet speed or response time, unless you have some non-standard, interfering settings.

It would be interesting to see what is making the difference in practice for you. I suspect it may be due to the fact that resolvconf package makes the /etc/resolv.conf file point to the localhost (whereas it traditionally used to point to the actual DNS). Since you disabled the localhost interface (lo), it now goes straight to the actual DNS. This is just an assumption and I maybe outright wrong.

Besides, the resolvconf package and /etc/resolv.conf file pointing to the localhost is a standard setting for Ubuntu now, and so far I haven't noticed any performance loss due to it.

Would you like to share with us the following outputs ? -
```
cat /etc/resolv.conf
cat /etc/network/interfaces
nm-tool
```

And if after enabling the eth0 and lo interfaces again, any of the above outputs change, please post the changed output as well.

While posting the outputs, please wrap them in 'Code' tags (follow the "Using Code Tags" link in my signature to see how). Thanks.

**PS:**
It is not a good idea to bump your thread before 24 hours if no one replied. It makes your thread look as if it has gotten replies, thus causing some potential helpers move on.

---


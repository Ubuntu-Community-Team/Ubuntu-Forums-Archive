---
title: "inetd and xinetd"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by SneakPeak on 2009-02-08
Hi,

What is the difference between inetd and xinetd?  Can one run both?  Why does Ubuntu appear to come with inetd as default?

I am trying desperately to get network scanning to work.  On my local 8.10 Ubuntu box I can scan perfectly.  I have followed various howtos on how to set up saned and a scanner server but I cannot scan from a windows box on my network.  (The windows box has Vista installed)  I have tried the windows version of xsane and SaneTwain and neither work.

On a some posts it seems that one can fix this by installing xinetd and forcing sane to run as root.  Seems like a risky approach.

Any advice?

Sneaks

---

### Post by blueridgedog on 2009-02-08
> **SneakPeak said:**
> Hi,

What is the difference between inetd and xinetd?  Can one run both?  Why does Ubuntu appear to come with inetd as default?


Here is a good analysis of xinetd:

[http://www.xinetd.org/faq.html](http://www.xinetd.org/faq.html)

It appears to fit what you are trying to do, but the configuration is somewhat advanced and exacting.

---

### Post by SneakPeak on 2009-02-09
Thank you 

That is useful information.  Do you think I should try to find a fix with inetd or should I use xinetd?  Is there a downside to using xinetd?

Thanks

Sneaks

---


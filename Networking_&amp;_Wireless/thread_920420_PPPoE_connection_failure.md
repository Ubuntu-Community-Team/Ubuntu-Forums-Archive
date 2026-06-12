---
title: "PPPoE connection failure"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Tekmo on 2008-09-15
I'm sorry I couldn't give a more descriptive title because I don't know exactly what triggers the problem except using Ubuntu (and even then only sometimes).  Basically, the PPPoE connection does not seem to work in Ubuntu and I'll give as much detail as I can from what I've tried about what works and what does not.

First off, the PPPoE connection worked in Windows XP.  So then I installed Ubuntu from a LiveCD and tried to set up a PPPoE connection using the Network Manager and it silently failed.  Whenever I try to enable PPPoE it just unchecks it and does not give any helpful feedback why it did not work.

So I did some research and tried out using pppoeconf.  The first time I used it it detected "eth0" and "eth0:avahi" but it failed to locate an access concentrator.  I checked my physical connection, which was perfectly okay and the green light was on and I also went back to Windows to verify that it still worked there, which it did.

I went back to Ubuntu after having restarted it to try again and this time it only detected "eth0" and was able to set it up and I indicated for it to start on boot (basically answered "Yes" to everything).  Internet worked.

But then after 2 restarts of my computer (both times back to Ubuntu) the internet stopped working.  I tried "pon dsl-provider" and that didn't work.  I also tried to list all pppd processes and there were none.  Trying to run pppoeconf again ended up detecting no access concentrator (I forgot whether it detected the eth0:avahi that time).

So I looked up a solution I found on the net that recommended removing the modifications to /etc/network/interfaces that pppoeconf had made and rerunning the configuration after restarting.  That worked and it got my internet up again.  But after 2 restarts of my computer it died again.  When I tried the same solution a 2nd time it did not work.

To see if my manual modifications had screwed stuff up, I booted ubuntu from the LiveCD and tried to see what I could to.  Then, for some curious reason, the network manager PPPoE worked that time and my internet was fine, so I removed the original ubuntu partition and reinstalled a clean install over it (ok, maybe a bit overkill, but I wanted to be sure).  I tried the same thing again in the new installation (before applying updates or anything, it was the very first thing I did) and the network manager failed.  Frustrated, I went back to booting from LiveCD to see if it still worked there and it did not.

I decided since I had a clean installation again to just stop before I messed anything else up and ask here what the problem might be.  As you can see, the problem is not very reproducible and it just sometimes randomly decides to work and sometimes it does not.  Windows continues to work the whole time so I know it is not a problem with the physical connection and that it has something to do with some part of Ubuntu.

Does anybody have any idea what may be the problem?  If you need any further diagnostic information, feel free to ask me for it.  I know I could buy a router to avoid this but it would really be a waste since I don't need to use more than one computer or use wireless.

---

### Post by Tekmo on 2008-09-16
Could somebody please help?

---


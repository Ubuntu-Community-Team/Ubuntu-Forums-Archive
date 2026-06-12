---
title: "Google Reader and GMail doesn't work"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by krendar on 2010-08-14
I have a problem on my netbook with UNR. The Google Reader page and the Google Mail page times out without loading and this has been going on at least since yesterday when I booted my netbook.

It seems to be every google page where I need to log in. Google search is working fine. Google Mail is being fetched fine from within Evolution.

This is a problem both on Chromium and on Firefox. Firefox just shows a blank page when I try to load Reader.

With a google search I found a tip to try to enable SSL 2.0 and disable SSL 3.0 within Chromium. That did not help.

I tried to search on twitter and I see no other people having problems with google so I assume its my system.

Hope somebody has a tip!

---

### Post by lovinglinux on 2010-08-14
Disable ipv6. See method #3 of [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by krendar on 2010-08-14
Thanks lovinglinux!

I solved it by deleting everything in my Google Chrome profile and relogging into Google again and everything worked.

I have not used this machine for a month and I suppose some of the stored cookies were invalid or whatever.

---


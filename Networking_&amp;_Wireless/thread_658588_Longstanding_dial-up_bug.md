---
title: "Longstanding dial-up bug"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by stefcep on 2008-01-04
One bug thats in Ubuntu since version 6 happens when you use dial up (ppp ) to access the internet and you have ethernet card as well, but you are not using the ethernet card. Its is possible to get a connection to your ISP via ppp, but none of your net apps ie browser, email, synaptic will be able to find the connection.  My solution was to open a terminal and type sudo route default ppp0, AFTER I had dialed and established my dial-up connection.  This bug doesn't happen in KUBUNTU when using kppp.  Its high time that this was fixed, because if you only have dial-up and you can't get net access your installation is only half completed.  I actually removed Ubuntu 7.04 because of this (no-one knew how to fix it at the time) and was hoping 7.10 was different.  Its not, and I think a few new users might remove 7.10 as well, just because of this simple bug.

---


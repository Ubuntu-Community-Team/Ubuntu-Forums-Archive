---
title: "How to boot up ubuntu to rdp directly into a windows terminal server"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by plockery on 2005-06-08
I am thinking of putting ubuntu onto some of thin clients at work that connect to windows terminal server 2003 (saves on windows license fees for terminal os's).

1. How do you get ubuntu to boot up and automatically connect to a windows terminal server via rdp?

I have tried from runlevel 1 or runlevel 2 without gdm with no success.
Where does one put a command such as that in rc.local in other distros?

2. What is the fastest way to get ubuntu to boot like this. Does uninstalling software make bootup any faster?

3. I have seen references to things like freenx. Not sure what that is but is this a better way to go for thin clients? I need local usb support on the thin client so that emory sticks can be mapped to the server.

Thanks Peter

---

### Post by cwaldbieser on 2005-06-08
In response to your question #3, FreeNX is software that improves the performance of X-windows over a network.  It has some other nifty features, too, but the responsiveness over even a dial up connection is what makes it so cool.  This is not really a practical solution if Windows is your terminal server (since Win2k3 doesn't run any X-apps).

---


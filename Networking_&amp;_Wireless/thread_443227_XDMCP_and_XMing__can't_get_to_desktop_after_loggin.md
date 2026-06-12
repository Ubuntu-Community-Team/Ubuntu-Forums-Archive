---
title: "XDMCP and XMing:  can't get to desktop after logging in"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by oldtappan on 2007-05-14
On Fiesty, I've setup XDMCP.  I connect from a Windows box using XMing to my Ubuntu box.  I enter my credentials at the XDMCP gdm login screen.  Click OK and all I see is the Human theme background/wallpaper.  I don't see my desktop (sometimes there a small white rectangle near the top left corner).  

Why can't I see my desktop?  Help!



PS:  XMing seems to be working fine.  For example, I can run X-Window apps on my Windows desktop.  It's just that I can't login and get to my Ubuntu desktop using XMing and XDMCP.  Why?

Thanks.

---

### Post by il_ventu on 2007-05-17
You must disable the firewall in both machine (i don't know how to configure correctly the firewall in the Windows machine), be sure the two system can resolve correctly the name of the other peer, then use xlaunch specifying -once in the additional options and disabling the clipboard support.
For me it works, let me know if it works for you too.

Ciao
a

---

### Post by zenon212 on 2007-05-31
I am having the same problem.  I have allowed the Xming software through my firewall on my Vista box.  My Ubuntu box does not have a firewall set up.  I tried the mentioned changes and nothing is different.

I can use XDMCP to get from one Linux box to another, just not Vista to either Linux box.

---

### Post by flobo on 2007-06-19
I had the same problem with Dapper, and the solution was simply to disable the clipboard integration in Xming. I have no idea why Xming clipboard integration is leading to a lock during the Gnome startup.
Maybe you have the same problem?

---

### Post by NZJon on 2007-07-02
That -- removing clipboard integration in Xming -- seemed to work for me too. Would be nicec to have clipboard integration; maybe someone wiser than I can explain what's going on...

Cheers,

   Jon

---


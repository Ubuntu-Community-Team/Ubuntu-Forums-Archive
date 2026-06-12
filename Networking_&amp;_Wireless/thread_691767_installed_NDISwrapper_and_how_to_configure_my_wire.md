---
title: "installed NDISwrapper and how to configure my wireless driver?"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by FastMady123 on 2008-02-08
I installed NDISwrapper and I need help configuring my wireless card. I have a Compaq Presario V5000 laptop. What should I do?

---

### Post by Hitam269 on 2008-02-09
I personally do not know anything about NDISwrapper, so I can not help you with that, but have you checked to make sure your network card cannot work with madwifi?  It seems like that would be much simpler than NDISwrapper, at least based on what I have heard.  I got madwifi set up in about ten or fifteen minutes on my computer.  [This guide]("http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/") (with one or two changes which I think are all explained in the comments) explains how to get madwifi working if that helps at all.  Good luck.

---

### Post by agim on 2008-02-09
If you have to go with the ndiswrapper route, you need your wireless drivers. Do you have the cd for your wireless card? If not, type this

lspci

and post the output.

---

### Post by agim on 2008-02-09
I have heard of problems with ndiswrapper too, but I have never had trouble with it. If it is in madwifi, I would go with that though.

---


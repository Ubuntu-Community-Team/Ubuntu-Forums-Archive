---
title: "[SOLVED] Pidgin login problems"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Safder on 2007-06-26
Hi everyone,

I am a new user of ubuntu, and have been using it for a couple of months now..:D , however I've been having this problem with gaim/pidgin since I've upgraded to Feisty.

I am not being able to log into pidgin, when my firewall is running. The firewall I am using is Firestarter. I haven't changed any of my settings since drapper. So I am essentially using the same settings I had in feisty, but I am facing this problem. I am able to log into pidgin when I manually stop my firewall. Could someone suggest me some steps to fix this problem. Thank you.

---

### Post by DugieHowsa on 2007-06-26
What IM protocol are  you using?  Yahoo? AOL?  MSN?

There is currently a known issue with Pidgin connecting to MSN networks behind some firewalls.

[http://developer.pidgin.im/ticket/485](http://developer.pidgin.im/ticket/485)

If that is not your issue, then check out the list of the rest of open issues here:

[http://developer.pidgin.im/query](http://developer.pidgin.im/query)

If you need futher help, you can either post more detailed information here (such as protocols used, procedures that replicate problem, and either pidgin log files or contents of the debug window).

---

### Post by Safder on 2007-06-27
I found out a way to run pidgin now. I went through a iptables script tutorial, and implemented that script, after which my pidgin was connecting without any problems. Thanks for your help :D

---


---
title: "Networking woes since Dapper..."
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by WinterWeaver on 2007-06-30
I've had this problem for a whole year now, across 3 versions of Ubuntu (dapper, edgy, feisty).

Actually it's two problems.

1 - I'm having problems connecting to my Router. After I log in >> Sometimes the Router setup pages display, other times it doesn't. Majority of times it doesn't display at all. I've tried this across multiple browsers. Also disabled ipv6 in Firefox, but still no joy.

2 - Connecting to a Windows Network. I can connect to the windows user, and I can see the shares. BUT if I try open the share, I cant show the contents. Sometimes, I can see the contents, but I cant copy files from it... we have to use a USB Stick all the time, which is quite annoying.

I'll be grateful if someone could help me solve and understand these problems once and for all.

First you will prob want me to give you the output of certain commands? You'll have to tell them to me, as I know absolutely nothing about Networking on Linux.

ta,

WW

---

### Post by bren on 2007-06-30
for the windows share search on this forum for the howto by stormbringer - it works

bren

---

### Post by tgalati4 on 2007-06-30
You may have a router problem or a cable problem.  Try replacing or rerouting the cable.

What is your power situation?  Do you have the router on an Uninterruptible Power Supply?  What is the brand of router?  They do go bad sometimes.

---

### Post by WinterWeaver on 2007-06-30
Regarding the windows shares, I've read many posts and How-Tos, but the problem is not setting the shares etc. it's the fact that it DID work, and SOMETIMES works, but sometimes it doesnt... sometimes, I can see files, but I cannot copy them, Other times, I cannot even see files.

Router > No UPS, and the problem persists on two different routers (home, and where I'm at now). In windows it works fine.

Let me also say, if I use the Live CD to boot, then I can access the router without any problems.

---

### Post by tgalati4 on 2007-07-01
Could it be a Network-Manager issue?  Perhaps the Live CD does not use Network Manager but your install does?  There are ways to disable Network Manager (search the forums) and set up your connection manually.  It's not hard, just tedious.  Let us know what other things you have tried.

---


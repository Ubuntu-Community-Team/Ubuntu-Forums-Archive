---
title: "Error Setting Up Cisco VPN Client (UbuntuStudio 8.04)"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by quattro004 on 2008-06-11
Hi,
I need help setting up a cisco vpn client with UbuntuStudio 8.04. I have tried following the tutorial here: [http://www.blog.arun-prabha.com/2008/05/01/cisco-vpn-installation-issue-with-ubuntu-804-hardy-heron/](http://www.blog.arun-prabha.com/2008/05/01/cisco-vpn-installation-issue-with-ubuntu-804-hardy-heron/) However, when I try to install the vpn client patch I get the following error:

command issued: patch < ./vpnclient-linux-2.6.24-final.diff

error received:
patching file GenDefs.h
patching file interceptor.c
Hunk #1 succeeded at 24 (offset -4 lines).
Hunk #2 succeeded at 48 (offset -4 lines).
Hunk #3 FAILED at 107.
Hunk #4 succeeded at 123 (offset -23 lines).
Hunk #5 FAILED at 350.
Hunk #6 succeeded at 849 (offset -86 lines).
Hunk #7 succeeded at 891 (offset -86 lines).
2 out of 7 hunks FAILED -- saving rejects to file interceptor.c.rej

Any help is much appreciated. Thanks.

---

### Post by jwithy on 2008-06-21
I had the same problem.  I found out that you first need to apply the 2.6.22 patch followed by the 2.6.24 patch.  You'll still get failed hunk errors, but you can use the interceptor.c.rej file to look at where in the file it needs to be changed.  If you know at least a little C++, you shouldn't have any problems.  If someone gives me a page to post it on, I will gladly upload the files that I've edited.

---


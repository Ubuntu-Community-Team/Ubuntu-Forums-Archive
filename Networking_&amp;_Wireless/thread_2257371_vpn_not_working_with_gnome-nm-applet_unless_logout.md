---
title: "vpn not working with gnome-nm-applet unless logout"
date: 2014-12-19
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2014-12-19
Hi, 

I have set up a vpn on my Ubuntu 14.04 laptop to get to the university's network. It has been working very well but I don't know since when trying to connect through gnome-nm-applet doesn't  work any more. Clicking the VPN entry from the drop down doesn't do anything. But if I logout and login again then it works. 

Please help. Thanks.

---

### Post by slickymaster on 2014-12-19
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by monkeybrain20122 on 2014-12-20
Apparently network manager timeouts too soon [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/420411](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/420411)

Following post #9 I upgraded network manger from this ppa [https://launchpad.net/~elemecca/+archive/ubuntu/nm-vpn](https://launchpad.net/~elemecca/+archive/ubuntu/nm-vpn) It appears to fix the problem.

---

### Post by monkeybrain20122 on 2014-12-20
Opps, happy too early. After working for 5 or 6 reboots it stops working again. Is there a way to 'unsolve' the thread?

---

### Post by vasa1 on 2014-12-20
> **monkeybrain20122 said:**
> ... Is there a way to 'unsolve' the thread?
If you find a way, maybe edit the wiki to include the "unsolve"?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Oops! Just go back and the option is now to mark the thread unsolved!

---

### Post by monkeybrain20122 on 2014-12-20
> **vasa1 said:**
> 
Oops! Just go back and the option is now to mark the thread unsolved!

Missed that. thanks!

---

### Post by monkeybrain20122 on 2014-12-21
It is this bug [https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/1297849](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/1297849)

---


---
title: "TCP connections freeze then time out"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by tnaran on 2007-10-21
Across any number of applications, my TCP connections (e.g., downloads from my news server, from updates, or even other website via Firefox) will just stop.  No further traffic through the firewall/router -- just silence until the application times out.  But if I were to start another download within seconds of the last one beginning to freeze, the downloads works fine until it too freezes.  This happens with http downloads, nntp, you name it.

The XP box connected to the same firewall/router is just fine.  I had this exact same problem the last time I used Linux 4 years ago, but no one could help except "did you update everything? Did you use Linux approved hardware?" and other unhelpful suggestions.

I've seen other people in this forum, and other, report the exact same problem and again... silence.  I see their posts, but most of the time, no replies.  When there are, they offer suggestions that don't solve the problem and the thread dies.

I've tried using the TCP/IP tweaks suggested and turned off IPV6 as some sites have suggested for slowness problems, but no effect.

Looking at ifconfig, it reports no packet losses.  I'm disinclined to suspect the router because XP works fine through it.

My crazy idea is that maybe a packet gets "missed" when it's received, but I've tried some of the sysctl configurations that are supposed to make connections more robust, and I haven't seen any significant difference.

Help!!

---

### Post by tnaran on 2007-10-21
Did some digging and found other people had this issue (Google "linux tcp connections stall").

First thing is switching my firewall/router to static addressing for my Linux box.  I had done that before, but it only improved the situation a little bit.  Even weirder was the lease time on the router was 1 week and this problem would happen within minutes.  Strange.

Next was a suggestion to sudo sysctl -w net.ipv4.tcp_window_scaling=0.  So far, it's behaving OK, but it's really hard to tell because all the update servers are struggling under the Gutsy Gibbon release and my news server isn't 100% perfect, but so far, it's behaving itself.  I'll keep people informed

---


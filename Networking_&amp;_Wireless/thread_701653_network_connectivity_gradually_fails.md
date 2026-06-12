---
title: "network connectivity gradually fails"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by wmbclark on 2008-02-19
I almost don't know how to describe this problem.  I'm running 7.10 as my work desktop, and connecting all through our complex network.  After being up for a few minutes to a couple of hours, I will start losing my ability to make network connections, but it happens gradually starting with more distant networks and getting closer to me over 15 minutes or so.

I'll give you the typical progression which may make more sense than the above.

I'll be doing my ordinary thing with connections to the web, as well as 5-15 systems on our internal network.  First my web browsing stops working, but internal systems are still available.  Then I lose connection to our remote site systems, then I lose contact with systems in our building, but on other nets, and finally I won't be able to connect to any system even on the same subnet.  I've found no way to recover my network from any stage without a reboot.  No one else on my subnet has any of these issues.

This would almost make sense if a) I was running a routing daemon and b) I could still reach my own subnet, but neither of those is true.  I have a single default route, which still pings until near the end of the progression.  I don't see anything in the logs that points toward a problem leading to this behavior.

I've created the file /etc/modprobe.d/bad_list which contains the line 'alias net-pf-10 off'.  That was supposed to disable ipv6, but lsmod shows the ipv6 module is loaded and in use so I'm not sure the instructions were correct.

Any suggestions?  I know it sounds like I'm smoking crack, but I really am seeing this several times per day.

---

### Post by wahr on 2008-02-19
i've been poking around today looking for my own answers and came across several threads with somewhat similar problems of signal loss.

don't take my word as absolute gospel, but they identified it as a driver issue.

Have you tried the alternative driver methods? (ndiswrapper for instance?--the forum has guides on it)

---

### Post by wmbclark on 2008-02-19
I have not.  The only things I saw with my (admittedly quick) search seemed to point at ipv6 being the culprit.  I'll check out the ndiswrapper info.

---

### Post by wmbclark on 2008-02-25
More detail:

This problem is with the onboard ethernet port on my motherboard.  It's a Realtek interface, but I can't remember the specific model.  If anyone needs to know I'll be glad to go back and get the version info.

I installed ndiswrapper, and it loaded the kernel module properly.  It also recognized the driver files and found my interface.  Unfortunately even blacklisting the original linux driver module did not result in the ndiswrapper controlling the interface.  The blacklisted driver continued to be loaded.

In desperation I bought an Intel EXPI9300, and disabled the onboard ethernet.  The problem is now gone.

I hate throwing hardware at a software problem, but I had to make this system work as my primary work desktop.

---


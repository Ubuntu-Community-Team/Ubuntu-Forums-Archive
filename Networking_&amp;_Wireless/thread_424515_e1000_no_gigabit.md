---
title: "e1000 no gigabit?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by macmasterxiv on 2007-04-26
I just got a new hp laptop that comes with an intel pro/1000PL network adaptor. For some reason, even though ubuntu says it's connected at gigabit speed (to a gigabit switch), I can only get fast (100) ethernet speed when transferring files.

I have a D-Link 5 port gigabit switch and another desktop with a gigabit NIC that runs gentoo. All software and indicator lights suggest everything is running at gigabit speeds.

Running the laptop on ubuntu and the desktop on gentoo, transferring files is slow (100mbit speeds). When the laptop is switched to windows and the desktop stays with gentoo, file transfers actually run at gigabit speed.

My question: does the e1000 driver support gigabit on the intel pro/1000PL? If so, how do I get it to work properly?

Thanks,
JM

---

### Post by macmasterxiv on 2007-05-02
Ok, after using iperf between the two computers on linux, it appears that it is not a driver problem, but a problem on the client side of samba mounting in nautilus. Is there any way to fix this?

---


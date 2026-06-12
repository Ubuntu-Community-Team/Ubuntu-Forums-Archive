---
title: "[SOLVED] computer not showing up in network places"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by evil316 on 2007-12-09
I have a wireless network.  I have 2 laptop Ubuntu PC's connected wireless, I have 2 more Ubuntu computers connected via ethernet to the router.  I can see 3 of the 4 in network places but one I cannot see.  The one I can't see is connected via ethernet.  I verified the same settings via System/admin/network and also by looking at /etc/hosts and /etc/resolv.conf (different host names of course) between the two ethernet connected machines.  They are set up the same.  There has to be something I'm missing but it's not coming to me.  Any suggestions?

Thanks!

---

### Post by Lostincyberspace on 2007-12-09
Do you have any thing shared from there, are the ports open, can you manualy ping it? Those are the first Ideas that came to mind, just to get a bearing.

---

### Post by evil316 on 2007-12-09
I can ping the IP address.  I am not doing any sharing at this point.  A port scan on that machine shows only ports 39249, 41931, and 50851.

---

### Post by jflaker on 2007-12-09
I don't think the system will be listed unless there is a share.

---

### Post by evil316 on 2007-12-09
That's what I've read but all my other machines are visible and there are no shares with them.

---

### Post by jflaker on 2007-12-09
same workgroup?

---

### Post by evil316 on 2007-12-09
Yes, all the machines are set up with a .ubuntu at the end.

---

### Post by jflaker on 2007-12-09
only suggestion is to create a folder that is read only and share it.  (read only so no file get put into it)

---

### Post by evil316 on 2007-12-09
OK, well that did it.  I went into folder sharing and it told me sharing wasn't installed.  That's why.  All is working good now.

Thanks!  I guess I should have poked around more.  I just assumed it was already installed.

---

### Post by jflaker on 2007-12-09
Still an amateur to ubuntu, I know networking and this also happens with windows on a peer network......the system doesn't advertise unless a share is made, which will install/start the services as you saw.....

---

### Post by Lostincyberspace on 2007-12-09
It is hard to diagnose most networing problem because the people who are having them don't know how to describe them or know what is going on. If it is network problemb "ping first ask questions later" is my first response. I then tell to check the ports that is where most problems are.

---


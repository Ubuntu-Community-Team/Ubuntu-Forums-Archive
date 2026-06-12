---
title: "Intel Advanced Networking Services (ANS)"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by nuno0351 on 2006-08-21
Hi guys,
I'm getting ready to setup a semi production (home use) Ubuntu x64 server (6.06), and I have a Intel Pro/1000 MT Dual Port Server NIC that I would like to set up with intel drivers and ANS package for load balancing.
I've found generic Linux instructions from Intel ([http://www.intel.com/support/network/adapter/1000/linux/ans.htm#config)](http://www.intel.com/support/network/adapter/1000/linux/ans.htm#config)), but I wanted to know if any of you guys have any personal experience setting this up, and if so, what to look out for.
Any info is greately appreciated of course.

---

### Post by Patrick-Ruff on 2006-08-21
it appears to look ok, I haven't personally set up anything like this but I'm sure if you run into any problems the insanely large community will be able to help you.


good luck, have fun :).

---

### Post by nuno0351 on 2006-08-21
Cool, thanks for the reply.
I will update with a 'how-to' when/if I figure it out.

---

### Post by nuno0351 on 2006-08-25
As it turns out, you only need Intel ANS if you are running Linux 2.4 -.
The Intel e100/e1000 drivers are compatible with kernel level NIC teaming available in Linux 2.6.  So that's all you have to configure.

---


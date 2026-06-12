---
title: "Gateway M-151S (laptop) wireless"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by kcackler on 2008-05-15
Hi there everyone.  While I'm not new to Linux in general, I am very new to Ubuntu, and, specifically, using linux in a home environment.

Due to problems that my fiancee is having with vista/wireless on her laptop, we've decided to give Ubuntu a try.  The problem is that for the life of me, I can't get ndiswrapper to work out for me.  I've extracted the files from the gateway setup .exe for the wireless drivers, and used ndiswrapper to install them.  ndiswrapper gui then reports that the driver is installed and that the hardware is present.  I modprobe and iwconfig shows that no wireless interfaces are installed.  

I've followed the instructions in the WIKI to a "T" and still can't get it working.  I'm sure it's possible, as I've seen this specific Realtek chipset several times in the ndiswrapper compatibility list

I definitely need some hand holding here.  Tell me what terminal commands to run, and I'll do it.  I'm not scared of configuration files, as I've been editing them on servers for years.  I'm just lost when it comes to ndiswrapper.

If anyone has gotten wireless running on this specific laptop, that would be FANTASTIC, especially if you could give me a link to the correct drivers and tell me exactly what steps I need to take to get it working.:lolflag:

If you need anything from me, ask away.

Thanks in advance.

Kevin

---

### Post by kcackler on 2008-05-15
This issue has been resolved. By getting the driver for the 8187b directly from realtek, rather than from gateway, ndiswrapper got everything running perfectly right then.

---


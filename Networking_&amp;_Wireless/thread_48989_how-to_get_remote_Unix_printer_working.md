---
title: "how-to get remote Unix printer working?"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by kline on 2005-07-14
Hello Folks,

I spent a couple hours trying to be able to print from here, "ethic.thought.org" to my printer server "tao.thought.org"; no  joy.  Most of my other servers are FreeBSD.  I have run severak flavors of Linux over the years, most recntly RH-8.  There, to get printing working, I just edited /etc/printcap and presto!  Here I have tried the sysadmin GUI method and test files just got lost.  Probably queued somewhere: Guessing!

Everywhere else on my unix network, I can print okay--from every other BSD platform.  Does anybody know what I'm doing wrong?  Are there any netwrking tools I can use to  figure out why my jobs are being postponed?  (No, not using CUPS elsewhere.)

thanks for any insights,

gary kline

---

### Post by kline on 2005-07-17
Well, people, I figured it out.   I installed the BSD lpr/lpd spooler on my ubuntu platform and used /etc/printcap to send test files to my print server.   I'll stay away from the flame-bait issues andsay that the main differences that *I* see between unix and linux is that unix [Berkeley flavor] comes with src.   Linux is generally much easier to use, more friendly for the naive user.   

-gdk

---


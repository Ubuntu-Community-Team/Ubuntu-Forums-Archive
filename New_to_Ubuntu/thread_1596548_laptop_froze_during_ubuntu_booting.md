---
title: "laptop froze during ubuntu booting"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by sallam on 2010-10-14
Greetings

Its the first time I see this, so I thought I ask.
I started my dual boot (ubuntu 10.10 - Win7) laptop today, and after the initial boot selection, the booting stopped at a black screen, with only a very tiny white curser at top left of screen. It kept like that and did not continue the booting process. Minutes later, I pressed the power button, and ubuntu closed, then I started the laptop again and everything went normal this time.

Can someone please help me understand what was that?
Or is there an error log to read and know what went wrong?
I need to know what is the proper procedure to do in case this happened again.

many thanks.

---

### Post by sallam on 2010-10-16
someone please?

---

### Post by Quackers on 2010-10-16
Browse the the logs at /var/log and see if you can find anything suspicious ( or System > Admin > Log viewer).

---

### Post by NightwishFan on 2010-10-16
No problem my friend, I will help you. :) This might have been a temporary issue. If it happens often, please post here again.

What you should do in the case that this happens again, is try to press CTRL+ALT+DEL. This will instruct Ubuntu to reboot the machine safely. If that does not work, hold ALT+SYSRQ, then while holding press one at a time R,E,I,S,U,B. This will force Ubuntu to reboot safely.

If you wish to check the logs for errors, you can open the System Log Viewer. If you want to check the log manually, look at /var/log/syslog.

I hope you like Ubuntu. :)

---

### Post by sallam on 2010-10-16
Many thanks Quackers.
I tried the log viewer, but I did'nt understand a thing.

NightwishFan,
Yes, I like ubuntu each day even more, thanks to the wonderful support of people like you.
The crash happened only once. But I'll remember your advice next time.
Many thanks.

---


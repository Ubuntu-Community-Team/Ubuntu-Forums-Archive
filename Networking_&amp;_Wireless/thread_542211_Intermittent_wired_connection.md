---
title: "Intermittent wired connection"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by frenchcr on 2007-09-03
Hi,

Just installed 7.04 for someone and installed updates. When they boot up the internet works. However, the connection is intermittent and doesnt last long when it is working. Any ideas on where to start.

**SOLVED**  I also have a laptop (ACER aspire 5920g) that i upgraded to gutsy. When i boot internet doesnt connect, I have to go into network settings and uncheck then reselect the wired connection. Ubuntu reconfigures connection and this fixes problem. How do i get it to connect by itself after booting up 


Any updates that could cause this...any roll backs to fix it ??

---

### Post by frenchcr on 2007-09-03
bumpety bump ...no ideas?...pls!!!

---

### Post by frenchcr on 2007-09-05
no one at all?

---

### Post by frenchcr on 2007-09-05
The intermittent wired desktop is still a problem.

...**BUT**, i just fixed the laptop problem...yay!

What fixed it, incase any other poor sole gets tormented by the same problem...

I went into System/Admin/Network tools,
In network device pull down box selected eth0,
Then clicked on IPv6,
Clicked on configure on the right to open eth0 properties,
In there i ticked the enable roaming mode button.

Rebooted and internet connected on boot up.

**I still dont know why**  ...can someone explain...the answer probably lies in the following...I use my laptop at home and in my office...both are wired connections...the problem of "not connecting at boot up" occured in both places.

---

### Post by frenchcr on 2007-09-06
reinstalled desktop with ubuntu ultimate 1.4 and solved the intermittent internet connection...who knows why?

---


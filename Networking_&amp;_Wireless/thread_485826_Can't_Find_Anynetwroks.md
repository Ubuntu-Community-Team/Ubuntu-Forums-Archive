---
title: "Can't Find Anynetwroks"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by jasonpeinko on 2007-06-27
My Feisty laptop was working perfectly until I went up to Seattle with my mom, I found the connection the first time and it connected fine, I loaded google, but then nothing after that, so i restarted the computer and now no networks show up :( So is there something I turned off or what?

---

### Post by kevdog on 2007-06-27
If this is a laptop, did you turn on the wirless card?? I think it is like alt-F2 but it depends on your computer model.

Also what is the output of the following at the command line:
iwlist scan

It would also be helpful if nothing works to post the following
/etc/network/interfaces
ifconfig
lshw -C network

---


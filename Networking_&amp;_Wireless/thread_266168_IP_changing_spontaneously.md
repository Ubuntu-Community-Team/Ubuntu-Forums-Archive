---
title: "IP changing spontaneously"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by ineluki12 on 2006-09-26
I have a *very* bizarre problem going on. I'm using ndiswrapper to run my Dell Broadcom wireless card. I've compiled the latest version of ndiswrapper (1.23). The card appears to be working correctly for the mostpart. However, my IP address is changing about once every minute or two! :shock:  It's hell on file downloads when I'm not NATed. Has anyone else seen anything like this? I'm going to try downloading the latest Dell driver, but I was wondering if anyone had other advice.

Thanks!

---

### Post by Mr Frosti on 2006-09-26
Run the command "tail -f /var/log/syslog" in a terminal to see if any of the information talks about changing the wireless card IP address.

The "-f" switch will make the log file continually update on your screen, so just leave it up and wait for the IP to change, then check the log.

---

### Post by ineluki12 on 2006-09-28
Thanks for the reply! Changing the Dell driver fixed the problem. But I'll keep your suggestion in mind for future issues.

---

